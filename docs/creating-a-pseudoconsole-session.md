---
title: Erstellen einer Pseudokonsolensitzung
description: Eine Pseudokonsolensitzung ermöglicht einer Anwendung das Hosten der Aktivitäten einer Zeichenmodusanwendung.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API, Kon-PTY, Pseudokonsole, Windows-PTY, Pseudo-Konsole
ms.localizationpriority: high
ms.openlocfilehash: 8cd057d3e74659fdeff6c569ddb053c881af1de8
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420229"
---
# <a name="creating-a-pseudoconsole-session"></a>Erstellen einer Pseudokonsolensitzung

Die Windows-Pseudokonsole, manchmal auch als Pseudokonsole, Kon-PTY oder Windows-PTY bezeichnet, ist ein Mechanismus, der dazu dient, einen externen Host für Aktivitäten des Zeichenmodus-Subsystems zu schaffen, der den Anteil des Standardkonsolen-Hostfensters ersetzt, der für Benutzerinteraktivität vorgesehen ist.

Das Hosten einer Pseudokonsolensitzung unterscheidet sich etwas von einer herkömmlichen Konsolensitzung. Herkömmliche Konsolensitzungen werden automatisch gestartet, wenn das Betriebssystem erkennt, dass eine Zeichenmodusanwendung ausgeführt werden soll. Im Gegensatz dazu müssen eine Pseudokonsolensitzung und die Kommunikationskanäle von der Hostinganwendung erstellt werden, bevor der Prozess mit der zu hostenden, untergeordneten Zeichenmodusanwendung erstellt wird. Der untergeordnete Prozess wird trotzdem mithilfe der Funktion [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) erstellt, jedoch mit einigen zusätzlichen Informationen, die das Betriebssystem anweisen, die passende Umgebung herzustellen.

Weitere Hintergrundinformationen zu diesem System finden Sie im [Blogbeitrag mit der ursprünglichen Ankündigung](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Ausführliche Beispiele zum Verwenden der Pseudokonsole finden Sie in unserem GitHub-Repository [microsoft/terminal](https://github.com/microsoft/terminal) im Beispielverzeichnis.

## <a name="preparing-the-communication-channels"></a>Vorbereiten der Kommunikationskanäle

Der erste Schritt besteht darin, ein Paar synchroner Kommunikationskanäle zu erstellen, die während der Erstellung der Pseudokonsolensitzung für die bidirektionale Kommunikation mit der gehosteten Anwendung bereitgestellt werden. Diese Kanäle werden vom Pseudokonsolensystem mithilfe von [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) und [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) mit [synchroner E/A](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) verarbeitet. Datei- oder E/A-Gerätehandles wie ein Dateistream oder eine Pipe sind akzeptabel, sofern keine [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped)-Struktur für die asynchrone Kommunikation erforderlich ist.

> [!WARNING]
>Zum Verhindern von Racebedingungen und Deadlocks empfehlen wir dringend, dass jeder der Kommunikationskanäle in einem separaten Thread bedient wird, der einen eigenen Clientpufferstatus und eine eigene Nachrichtenwarteschlange innerhalb Ihrer Anwendung aufweist. Das Bedienen aller Aktivitäten der Pseudokonsole im gleichen Thread kann zu einem Deadlock führen, bei dem einer der Kommunikationspuffer gefüllt ist und auf Ihre Aktion wartet, während Sie versuchen, eine blockierende Anforderung an einen anderen Kanal zu verteilen.

## <a name="creating-the-pseudoconsole"></a>Erstellen der Pseudokonsole

Identifizieren Sie mithilfe der eingerichteten Kommunikationskanäle das „Leseende“ des Eingabekanals und das „Schreibende“ des Ausgabekanals. Dieses Paar Handles wird beim Aufrufen von [**CreatePseudoConsole**](createpseudoconsole.md) zum Erstellen des Objekts bereitgestellt.

Bei der Erstellung ist eine Größe erforderlich, die die X- und die Y-Abmessung (als Zeichenanzahl) darstellt. Dies sind die Abmessungen, die wir für das endgültige (Terminal-) Präsentationsfenster auf die Anzeigeoberfläche anwenden. Die Werte werden verwendet, um innerhalb des Pseudokonsolensystems einen Puffer im Arbeitsspeicher zu erstellen.

Die Puffergröße wird als Antwort an Clientanwendungen im Zeichenmodus übergeben, die mithilfe der [clientseitigen Konsolenfunktionen](console-functions.md) wie [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) Informationen abzufragen versuchen, und gibt das Layout und die Positionierung von Text vor, wenn Clients Funktionen wie [**WriteConsoleOutput**](writeconsoleoutput.md) verwenden.

Schließlich wird bei der Erstellung einer Pseudokonsole ein Feld für Flags bereitgestellt, um besondere Funktionalität zu realisieren. Standardmäßig ist es auf 0 festgelegt, was keine Sonderfunktionalität bedeutet.

Zurzeit ist nur ein besonderes Flag verfügbar, das die Vererbung der Cursorposition von einer Konsolensitzung anfordert, die dem Aufrufer der Pseudokonsolen-API bereits angefügt ist. Dies ist für die Verwendung in komplexeren Szenarien vorgesehen, in denen eine hostende Anwendung, die eine Pseudokonsolensitzung vorbereitet, ihrerseits ebenfalls als Clientanwendung im Zeichenmodus einer weiteren Konsolenumgebung ausgeführt wird.

Im Codeausschnitt unten ist ein Beispiel angegeben, das [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) verwendet, um ein Paar Kommunikationskanäle einzurichten und die Pseudokonsole zu erstellen.

```C

HRESULT SetUpPseudoConsole(COORD size)
{
    HRESULT hr = S_OK;

    // Create communication channels

    // - Close these after CreateProcess of child application with pseudoconsole object.
    HANDLE inputReadSide, outputWriteSide;

    // - Hold onto these and use them for communication with the child through the pseudoconsole.
    HANDLE outputReadSide, inputWriteSide;

    if (!CreatePipe(&inputReadSide, &inputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    if (!CreatePipe(&outputReadSide, &outputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    HPCON hPC;
    hr = CreatePseudoConsole(size, inputReadSide, outputWriteSide, 0, &hPC);
    if (FAILED(hr))
    {
        return hr;
    }

    // ...

}
```

> [!NOTE]
>Dieser Codeausschnitt ist unvollständig und dient nur zur Demonstration dieses bestimmten Aufrufs. Sie müssen die Lebensdauer der **HANDLE** s passend verwalten. Wenn die Lebensdauer der **HANDLE** s nicht ordnungsgemäß verwaltet wird, kann dies zu Deadlockszenarien führen, insbesondere bei synchronen E/A-Aufrufen.

Beim Abschluss des [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)-Aufrufs, um die Clientanwendung im Zeichenmodus zu erstellen, die an die Pseudokonsole angefügt ist, sollten die während der Erstellung übergebenen Handles von diesem Prozess freigegeben werden. Dadurch wird die Verweisanzahl des zugrundeliegenden Geräteobjekts verringert, und E/A-Vorgänge können einen unterbrochenen Kanal ordnungsgemäß erkennen, wenn die Pseudokonsolensitzung ihre Kopie der Handles schließt.

## <a name="preparing-for-creation-of-the-child-process"></a>Vorbereiten der Erstellung des untergeordneten Prozesses

Die nächste Phase besteht im Vorbereiten der Struktur [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw), die die Pseudokonsoleninformationen beim Starten des untergeordneten Prozesses übermittelt.

Diese Struktur bietet die Möglichkeit, komplexe Startinformationen einschließlich Attributen für die Prozess- und Threaderstellung bereitzustellen.

Verwenden Sie [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in der Art eines Doppelaufrufs, um zuerst die Anzahl der erforderlichen Bytes zum Aufnehmen der Liste zu berechnen, den angeforderten Arbeitsspeicher zuzuweisen und dann in einem erneuten Aufruf den opaken Arbeitsspeicherzeiger zu übergeben, um ihn als Attributliste einrichten zu lassen.

Rufen Sie anschließend [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) auf, und übergeben Sie die initialisierte Attributliste mit dem Flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, das Handle der Pseudokonsole und die Größe des Handles der Pseudokonsole.

```C

HRESULT PrepareStartupInformation(HPCON hpc, STARTUPINFOEX* psi)
{
    // Prepare Startup Information structure
    STARTUPINFOEX si;
    ZeroMemory(&si, sizeof(si));
    si.StartupInfo.cb = sizeof(STARTUPINFOEX);

    // Discover the size required for the list
    size_t bytesRequired;
    InitializeProcThreadAttributeList(NULL, 1, 0, &bytesRequired);

    // Allocate memory to represent the list
    si.lpAttributeList = (PPROC_THREAD_ATTRIBUTE_LIST)HeapAlloc(GetProcessHeap(), 0, bytesRequired);
    if (!si.lpAttributeList)
    {
        return E_OUTOFMEMORY;
    }

    // Initialize the list memory location
    if (!InitializeProcThreadAttributeList(si.lpAttributeList, 1, 0, &bytesRequired))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // Set the pseudoconsole information into the list
    if (!UpdateProcThreadAttribute(attributeList,
                                   0,
                                   PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE,
                                   hpc,
                                   sizeof(hpc),
                                   NULL,
                                   NULL))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    *psi = si;

    return S_OK;
}

```

## <a name="creating-the-hosted-process"></a>Erstellen des gehosteten Prozesses

Rufen Sie als nächstes [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) auf, und übergeben Sie die [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw)-Struktur zusammen mit dem Pfad zur ausführbaren Datei und allen weiteren Konfigurationsinformationen, sofern zutreffend. Es ist wichtig, beim Aufrufen das Flag **EXTENDED_STARTUPINFO_PRESENT** festzulegen, um das System darüber zu informieren, dass der Verweis auf die Pseudokonsole in den erweiterten Informationen enthalten ist.

```C
HRESULT SetUpPseudoConsole(COORD size)
{
    // ...

    PCWSTR childApplication = L"C:\\windows\\system32\\cmd.exe";

    // Create mutable text string for CreateProcessW command line string.
    const size_t charsRequired = wcslen(childApplication) + 1; // +1 null terminator
    PWSTR cmdLineMutable = (PWSTR)HeapAlloc(GetProcessHeap(), 0, sizeof(wchar_t) * charsRequired);

    if (!cmdLineMutable)
    {
        return E_OUTOFMEMORY;
    }

    wcscpy_s(cmdLineMutable, bytesRequired, childApplication);

    PROCESS_INFORMATION pi;
    ZeroMemory(&pi, sizeof(pi));

    // Call CreateProcess
    if (!CreateProcessW(NULL,
                        cmdLineMutable,
                        NULL,
                        NULL,
                        FALSE,
                        EXTENDED_STARTUPINFO_PRESENT,
                        NULL,
                        NULL,
                        &siEx.StartupInfo,
                        &pi))
    {
        HeapFree(GetProcessHeap(), 0, cmdLineMutable);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // ...
}
```

> [!NOTE]
> Das Schließen der Pseudokonsolensitzung, während der gehostete Prozess noch gestartet wird und eine Verbindung herstellt, kann dazu führen, dass die Clientanwendung ein Fehlerdialogfeld anzeigt. Das gleiche Fehlerdialogfeld wird angezeigt, wenn dem gehosteten Prozess beim Start ein ungültiges Handle für die Pseudokonsole übergeben wird. Aus der Sicht des Initialisierungscodes des gehosteten Prozesses sind die zwei Bedingungen identisch. Das Popupdialogfeld der gehosteten Clientanwendung lautet `0xc0000142`, mit einer lokalisierten Meldung, die den Initialisierungsfehler im Detail angibt.

## <a name="communicating-with-the-pseudoconsole-session"></a>Kommunikation mit der Pseudokonsolensitzung

Nach der erfolgreichen Erstellung des Prozesses kann die hostende Anwendung das Schreibende der Eingabepipe verwenden, um Informationen zur Benutzerinteraktion an die Pseudokonsole zu senden, und das Leseende der Ausgabepipe, um Informationen zur grafischen Darstellung von der Pseudokonsole zu empfangen.

Die Entscheidung, wie weitere Aktivitäten behandelt werden, liegt ausschließlich bei der hostenden Anwendung. Die hostende Anwendung kann etwa ein Fenster in einem anderen Thread starten, um Eingaben aus der Benutzerinteraktion zu erfassen und sie für die Pseudokonsole und die gehostete Zeichenmodusanwendung in das Schreibende der Eingabepipe zu serialisieren. Ein weiterer Thread könnte gestartet werden, der das Leseende der Ausgabepipe für die Pseudokonsole leert, den Text und die Informationen der [virtuellen Terminalsequenz](console-virtual-terminal-sequences.md) decodiert und sie auf dem Bildschirm ausgibt.

Threads können außerdem verwendet werden, um die Informationen aus den Kanälen der Pseudokonsole an einen anderen Kanal oder ein anderes Gerät zu übertragen, einschließlich eines Netzwerks, um Informationen remote an einen anderen Prozess oder Computer zu übergeben und jegliche lokale Transcodierung der Informationen zu vermeiden.

## <a name="resizing-the-pseudoconsole"></a>Ändern der Größe der Pseudokonsole

Zur Laufzeit kann ein Umstand eintreten, durch den die Größe des Puffers aufgrund einer Benutzerinteraktion oder einer außer der Reihe empfangenen Anforderung von einem anderen Anzeige-/Interaktionsgerät geändert werden muss.

Dies kann mit der [**ResizePseudoConsole**](resizepseudoconsole.md)-Funktion erfolgen, die sowohl die Höhe als auch die Breite des Puffers in Form einer Zeichenanzahl angibt.

```C
// Theoretical event handler function with theoretical
// event that has associated display properties
// on Source property.
void OnWindowResize(Event e)
{
    // Retrieve width and height dimensions of display in
    // characters using theoretical height/width functions
    // that can retrieve the properties from the display
    // attached to the event.
    COORD size;
    size.X = GetViewWidth(e.Source);
    size.Y = GetViewHeight(e.Source);

    // Call pseudoconsole API to inform buffer dimension update
    ResizePseudoConsole(m_hpc, size);
}
```

## <a name="ending-the-pseudoconsole-session"></a>Beenden der Pseudokonsolensitzung

Um die Sitzung zu beenden, rufen Sie die Funktion [**ClosePseudoConsole**](closepseudoconsole.md) mit dem Handle aus der ursprünglichen Erstellung der Pseudokonsole auf. Alle verknüpften Clientanwendungen im Zeichenmodus, wie etwa die aus dem [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)-Aufruf, werden beim Schließen der Sitzung beendet. Wenn das ursprüngliche untergeordnete Element eine Anwendung vom Shelltyp war, die andere Prozesse erstellt, werden alle zugehörigen verknüpften Prozesse in der Struktur ebenfalls beendet.

> [!WARNING]
>Das Schließen der Sitzung hat eine Reihe von Nebenwirkungen, die zu einer Deadlocksituation führen können, wenn die Pseudokonsole synchron in einem einzelnen Thread ausgeführt wird. Der Vorgang des Schließens der Pseudokonsolensitzung kann zum Senden eines finalen Frameupdates an `hOutput` führen, das aus dem Puffer des Kommunikationskanals entfernt werden sollte. Wenn beim Erstellen der Pseudokonsole `PSEUDOCONSOLE_INHERIT_CURSOR` ausgewählt war, kann der Versuch, die Pseudokonsole zu schließen, ohne auf die Nachricht zur Abfrage der Cursorvererbung zu reagieren (die an `hOutput` empfangen wurde und über `hInput` beantwortet wird), eine andere Deadlockbedingung verursachen. Es wird empfohlen, dass die Kommunikationskanäle für die Pseudokonsole auf einzelnen Threads bedient werden und so lange entleert und verarbeitet bleiben, bis sie von sich aus durch das Beenden der Clientanwendung oder durch den Abschluss der Löschaktivitäten beim Aufruf der Funktion [**ClosePseudoConsole**](closepseudoconsole.md) unterbrochen werden.
