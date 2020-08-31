---
title: Erstellen einer pseudoconsole-Sitzung
description: Eine Pseudo Konsolen Sitzung ermöglicht einer Anwendung das Hosten der Aktivitäten einer zeichenmodusanwendung.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, konpty, pseudoconsole, Windows Pty, Pseudo Konsole
ms.openlocfilehash: ec63cf4bfc1502aa37b0b336f1ffdc7bab2be07e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059906"
---
# <a name="creating-a-pseudoconsole-session"></a>Erstellen einer pseudoconsole-Sitzung

Die Windows-Pseudo Konsole, manchmal auch als Pseudo Konsole,-Konstante oder Windows-Pty bezeichnet, ist ein Mechanismus, der zum Erstellen eines externen Hosts für subsystemaktivitäten im Zeichenmodus entwickelt wurde, die den Benutzer Interaktivität-Teil des standardmäßigen Konsolen Host Fensters ersetzen.

Das Hosting einer pseudoconsole-Sitzung unterscheidet sich etwas von einer herkömmlichen Konsolen Sitzung. Herkömmliche Konsolen Sitzungen werden automatisch gestartet, wenn das Betriebssystem erkennt, dass eine zeichenmodusanwendung gerade ausgeführt wird. Im Gegensatz dazu müssen eine Pseudo Konsolen Sitzung und die Kommunikationskanäle von der Hostinganwendung erstellt werden, bevor der Prozess mit der untergeordneten Zeichenmodus-Anwendung erstellt wird, die gehostet werden soll. Der untergeordnete Prozess wird weiterhin mithilfe der Funktion " [**deateprocess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) " erstellt, aber mit einigen zusätzlichen Informationen, die das Betriebssystem zum Einrichten der entsprechenden Umgebung leiten werden.

Weitere Hintergrundinformationen zu diesem System finden Sie im [ersten Ankündigungs Blogbeitrag](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Ausführliche Beispiele für die Verwendung von pseudoconsole finden Sie in unserem GitHub [-Repository Microsoft/Console](https://github.com/Microsoft/console) im Verzeichnis "Beispiele".

## <a name="preparing-the-communication-channels"></a>Vorbereiten der Kommunikationskanäle

Der erste Schritt besteht darin, ein paar synchroner Kommunikationskanäle zu erstellen, die während der Erstellung der pseudoconsole-Sitzung für die bidirektionale Kommunikation mit der gehosteten Anwendung bereitgestellt werden. Diese Kanäle werden vom pseudoconsole-System mithilfe von "read [**File**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) " und " [**Write File**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) " mit [synchroner e/a-](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output)Vorgängen verarbeitet. Datei-oder e/a-Geräte Handles wie ein Dateistream oder eine Pipe sind zulässig, solange keine [**über**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) Lapp Ende Struktur für die asynchrone Kommunikation erforderlich ist.

**Nebenbei**

Um Racebedingungen und Deadlocks zu vermeiden, wird dringend empfohlen, dass jeder der Kommunikationskanäle in einem separaten Thread gewartet wird, der seinen eigenen Client Puffer Status und jede Messaging Warteschlange in der Anwendung verwaltet. Wenn Sie alle pseudoconsole-Aktivitäten im gleichen Thread ausführen, kann dies zu einem Deadlock führen, bei dem einer der Kommunikationspuffer ausgefüllt wird und auf die Aktion wartet, während Sie versuchen, eine blockierende Anforderung an einen anderen Kanal zu senden.

## <a name="creating-the-pseudoconsole"></a>Erstellen der pseudoconsole

Identifizieren Sie mit den eingerichteten Kommunikationskanälen das Lese Ende des Eingabe Kanals und das "Write"-Ende des Ausgabe Kanals. Dieses Paar von Handles wird beim Aufrufen von [**createpseudoconsole**](createpseudoconsole.md) zum Erstellen des-Objekts bereitgestellt.

Beim Erstellen von wird auch eine Größe bereitgestellt, die die X-und Y-Dimensionen (in Anzahl von Zeichen) darstellt. Dies sind die Abmessungen, die auf die Anzeige Oberfläche für das endgültige Präsentations Fenster (Terminal) angewendet werden. Die Werte werden verwendet, um einen in-Memory-Puffer im Pseudo Konsolensystem zu erstellen. 

Die Puffergröße bietet Antworten auf Client-Zeichenmodus-Anwendungen, die mithilfe der [Client seitigen Konsolenfunktionen](console-functions.md) wie [**getconsoleskreenbufferinfoex**](getconsolescreenbufferinfoex.md) nach Informationen suchen und das Layout und die Positionierung von Text vorschreiben, wenn Clients Funktionen wie " [**Beschreib teconsoleoutput**](writeconsoleoutput.md)" verwenden.

Zum Schluss wird ein Flags-Feld bei der Erstellung einer pseudoconsole zur Durchführung spezieller Funktionen bereitgestellt. Legen Sie diese Einstellung standardmäßig auf 0 fest, um keine besondere Funktionalität zu haben.

Zurzeit ist nur ein spezielles Flag verfügbar, um die ervererbungsquelle der Cursorposition von einer Konsolen Sitzung anzufordern, die bereits an den Aufrufer der pseudoconsole-API angefügt ist. Dies ist für die Verwendung in komplexeren Szenarien vorgesehen, in denen eine Host Anwendung, die eine Pseudo Konsolen Sitzung vorbereitet, selbst auch eine Client Zeichenmodus-Anwendung einer anderen Konsolen Umgebung ist. 

Unten finden Sie einen Beispielcode Ausschnitt, der mit der Verwendung von "" erstellt wird, um ein paar von Kommunikations [**Kanälen einzurichten und**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) die Pseudo Konsole zu erstellen.

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


**HINWEIS:** 

Dieser Code Ausschnitt ist unvollständig und wird nur für die Demonstration dieses bestimmten Aufrufes verwendet. Sie müssen die Lebensdauer des **Handles**s entsprechend verwalten. Wenn die Lebensdauer von **Handles**nicht ordnungsgemäß verwaltet wird, kann dies zu deadlockszenarien führen, insbesondere bei synchronen e/a-aufrufen.

Nach Abschluss [**des Vorgangs zum**](https://msdn.microsoft.com/library/windows/desktop/ms682425) Erstellen einer Anwendung, die an die pseudoconsole angefügt ist, müssen die während der Erstellung angegebenen Handles von diesem Prozess freigegeben werden. Dadurch wird der Verweis Zähler für das zugrunde liegende Geräte Objekt verringert, und e/a-Vorgänge können einen unterbrochenen Kanal ordnungsgemäß erkennen, wenn die pseudoconsole-Sitzung seine Kopie der Handles schließt.

## <a name="preparing-for-creation-of-the-child-process"></a>Die Erstellung des untergeordneten Prozesses wird vorbereitet.

Die nächste Phase besteht in der Vorbereitung der [**startupinfoex**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) -Struktur, die die pseudoconsole-Informationen beim Starten des untergeordneten Prozesses vermittelt.

Diese Struktur enthält die Möglichkeit, komplexe Startinformationen bereitzustellen, einschließlich der Attribute für die Prozess-und Thread Erstellung.

Verwenden Sie [**initializeprocthreadattributelist**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in einem doppelten Callcenter, um zunächst die Anzahl der Bytes zu berechnen, die zum Speichern der Liste erforderlich sind, den angeforderten Arbeitsspeicher zuzuordnen und dann erneut den nicht transparenten Speicher Zeiger bereitzustellen, um ihn als Attribut Liste einzurichten.

Führen Sie als nächstes [**updateprocthreadattribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) aus, indem Sie die initialisierte Attribut Liste mit dem-Flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, dem pseudoconsole-Handle und der Größe des pseudoconsole-Handles übergeben.

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

[**Rufen Sie als nächstes**](https://msdn.microsoft.com/library/windows/desktop/ms682425) die [**startupinfoex**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) -Struktur mit dem Pfad zur ausführbaren Datei und ggf. zusätzlichen Konfigurationsinformationen auf. Es ist wichtig, das **EXTENDED_STARTUPINFO_PRESENT** -Flag festzulegen, wenn aufgerufen wird, um das System zu warnen, dass der pseudoconsole-Verweis in den erweiterten Informationen enthalten ist.

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

**Nebenbei**

Das Schließen der Pseudo Konsolen Sitzung, während der gehostete Prozess noch startet und eine Verbindung hergestellt wird, kann dazu führen, dass von der Client Anwendung ein Fehler Dialogfeld angezeigt wird. Das gleiche Fehler Dialogfeld wird angezeigt, wenn dem gehosteten Prozess ein ungültiges Pseudo Konsolen Handle für den Start zugewiesen wird. Der Initialisierungs Code für den gehosteten Prozess ist identisch. Im Popup Dialogfeld der gehosteten Client Anwendung bei einem Fehler wird `0xc0000142` eine lokalisierte Meldung mit der fehlerhaften Initialisierung gelesen.

## <a name="communicating-with-the-pseudoconsole-session"></a>Kommunikation mit der pseudoconsole-Sitzung

Nachdem der Prozess erfolgreich erstellt wurde, kann die Host Anwendung das schreibende der Eingabe Pipe verwenden, um Benutzer Interaktions Informationen an die pseudoconsole zu senden, und das leseende der ausgabepipe, um grafische Präsentationsinformationen von der Pseudo Konsole zu erhalten. 

Es ist vollständig für die Host Anwendung zu entscheiden, wie weitere Aktivitäten behandelt werden sollen. Die Hostinganwendung könnte ein Fenster in einem anderen Thread starten, um Benutzerinteraktionen zu erfassen und in das schreibende der Eingabe Pipe für die Pseudo Konsole und die Anwendung im gehosteten Zeichenmodus zu serialisieren. Ein anderer Thread könnte gestartet werden, um das leseende der Ausgabe Pipe für die Pseudo Konsole zu entfernen, den Text und die Informationen zu den [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) zu decodieren und auf dem Bildschirm darzustellen. 

Threads können auch verwendet werden, um die Informationen aus den pseudoconsole-Kanälen an einen anderen Kanal oder ein anderes Gerät zu übertragen, einschließlich eines Netzwerks an Remote Informationen an einen anderen Prozess oder Computer, und jegliche lokale Transcodierung der Informationen zu vermeiden.

## <a name="resizing-the-pseudoconsole"></a>Ändern der Größe der pseudoconsole

Während der Laufzeit gibt es möglicherweise eine Situation, in der die Größe des Puffers aufgrund einer Benutzerinteraktion oder einer Out-of-Band-Anforderung von einem anderen Anzeige-/Interaktionsgerät geändert werden muss.

Dies kann mit der [**resizepseudoconsole**](resizepseudoconsole.md) -Funktion durchgeführt werden, wobei die Höhe und die Breite des Puffers in der Anzahl von Zeichen angegeben werden.

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

## <a name="ending-the-pseudoconsole-session"></a>Beenden der pseudoconsole-Sitzung

Um die Sitzung zu beenden, müssen Sie die Funktion [**closepseudoconsole**](closepseudoconsole.md) mit dem Handle aus der ursprünglichen Pseudo Konsolen Erstellung abrufen. Alle angefügten Anwendungen im Zeichenmodus, wie z. b. der aus dem [**Vorgang "deateprocess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) ", werden beendet, wenn die Sitzung geschlossen wird. Wenn das ursprüngliche untergeordnete Element eine shelltyp Anwendung war, die andere Prozesse erstellt, werden alle zugehörigen verknüpften Prozesse in der Struktur ebenfalls beendet.

**Nebenbei**

Das Schließen der Sitzung hat mehrere Nebeneffekte, die zu einer Deadlockbedingung führen können, wenn die Pseudo Konsole synchron mit einem Single Thread verwendet wird. Beim Schließen der pseudoconsole-Sitzung kann ein abschließendes Frame Update ausgegeben `hOutput` werden, das aus dem Kommunikationskanal Puffer abgeleitet werden soll. Wenn außerdem `PSEUDOCONSOLE_INHERIT_CURSOR` beim Erstellen der pseudoconsole ausgewählt wurde, kann der Versuch, die pseudoconsole zu schließen, ohne auf die Cursor erstellungsabfragenmeldung (die empfangen `hOutput` und Antworten über übermittelt wird `hInput` ) zu einer anderen Deadlock-Bedingung führen. Es wird empfohlen, dass Kommunikationskanäle für die pseudoconsole in einzelnen Threads gewartet werden und verbleibt, bis Sie von der Client Anwendung, die beendet wird, oder durch den Abschluss von Beendigungs-Aktivitäten beim Aufrufen der [**closepseudoconsole**](closepseudoconsole.md) -Funktion beendet und verarbeitet wird.
