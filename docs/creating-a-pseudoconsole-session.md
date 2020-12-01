---
title: Erstellen einer pseudoconsole-Sitzung
description: Eine Pseudo Konsolen Sitzung ermöglicht einer Anwendung das Hosten der Aktivitäten einer zeichenmodusanwendung.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, konpty, pseudoconsole, Windows Pty, Pseudo Konsole
ms.localizationpriority: high
ms.openlocfilehash: 8cd057d3e74659fdeff6c569ddb053c881af1de8
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420229"
---
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="30167-104">Erstellen einer pseudoconsole-Sitzung</span><span class="sxs-lookup"><span data-stu-id="30167-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="30167-105">Die Windows-Pseudo Konsole, manchmal auch als Pseudo Konsole,-Konstante oder Windows-Pty bezeichnet, ist ein Mechanismus, der zum Erstellen eines externen Hosts für subsystemaktivitäten im Zeichenmodus entwickelt wurde, die den Benutzer Interaktivität-Teil des standardmäßigen Konsolen Host Fensters ersetzen.</span><span class="sxs-lookup"><span data-stu-id="30167-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="30167-106">Das Hosting einer pseudoconsole-Sitzung unterscheidet sich etwas von einer herkömmlichen Konsolen Sitzung.</span><span class="sxs-lookup"><span data-stu-id="30167-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="30167-107">Herkömmliche Konsolen Sitzungen werden automatisch gestartet, wenn das Betriebssystem erkennt, dass eine zeichenmodusanwendung gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="30167-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="30167-108">Im Gegensatz dazu müssen eine Pseudo Konsolen Sitzung und die Kommunikationskanäle von der Hostinganwendung erstellt werden, bevor der Prozess mit der untergeordneten Zeichenmodus-Anwendung erstellt wird, die gehostet werden soll.</span><span class="sxs-lookup"><span data-stu-id="30167-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="30167-109">Der untergeordnete Prozess wird weiterhin mithilfe der Funktion " [**deateprocess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) " erstellt, aber mit einigen zusätzlichen Informationen, die das Betriebssystem zum Einrichten der entsprechenden Umgebung leiten werden.</span><span class="sxs-lookup"><span data-stu-id="30167-109">The child process will still be created using the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="30167-110">Weitere Hintergrundinformationen zu diesem System finden Sie im [ersten Ankündigungs Blogbeitrag](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="30167-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="30167-111">Ausführliche Beispiele für die Verwendung von pseudoconsole finden Sie im GitHub [-Repository Microsoft/Terminal](https://github.com/microsoft/terminal) im Verzeichnis "Beispiele".</span><span class="sxs-lookup"><span data-stu-id="30167-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [microsoft/terminal](https://github.com/microsoft/terminal) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="30167-112">Vorbereiten der Kommunikationskanäle</span><span class="sxs-lookup"><span data-stu-id="30167-112">Preparing the communication channels</span></span>

<span data-ttu-id="30167-113">Der erste Schritt besteht darin, ein paar synchroner Kommunikationskanäle zu erstellen, die während der Erstellung der pseudoconsole-Sitzung für die bidirektionale Kommunikation mit der gehosteten Anwendung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="30167-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="30167-114">Diese Kanäle werden vom pseudoconsole-System mithilfe von "read [**File**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) " und " [**Write File**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) " mit [synchroner e/a-](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output)Vorgängen verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="30167-114">These channels are processed by the pseudoconsole system using [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="30167-115">Datei-oder e/a-Geräte Handles wie ein Dateistream oder eine Pipe sind zulässig, solange keine [**über**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) Lapp Ende Struktur für die asynchrone Kommunikation erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="30167-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

> [!WARNING]
><span data-ttu-id="30167-116">Um Racebedingungen und Deadlocks zu vermeiden, wird dringend empfohlen, dass jeder der Kommunikationskanäle in einem separaten Thread gewartet wird, der seinen eigenen Client Puffer Status und jede Messaging Warteschlange in der Anwendung verwaltet.</span><span class="sxs-lookup"><span data-stu-id="30167-116">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="30167-117">Wenn Sie alle pseudoconsole-Aktivitäten im gleichen Thread ausführen, kann dies zu einem Deadlock führen, bei dem einer der Kommunikationspuffer ausgefüllt wird und auf die Aktion wartet, während Sie versuchen, eine blockierende Anforderung an einen anderen Kanal zu senden.</span><span class="sxs-lookup"><span data-stu-id="30167-117">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="30167-118">Erstellen der pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="30167-118">Creating the Pseudoconsole</span></span>

<span data-ttu-id="30167-119">Identifizieren Sie mit den eingerichteten Kommunikationskanälen das Lese Ende des Eingabe Kanals und das "Write"-Ende des Ausgabe Kanals.</span><span class="sxs-lookup"><span data-stu-id="30167-119">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="30167-120">Dieses Paar von Handles wird beim Aufrufen von [**createpseudoconsole**](createpseudoconsole.md) zum Erstellen des-Objekts bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="30167-120">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="30167-121">Bei der Erstellung ist eine Größe erforderlich, die die X-und Y-Dimensionen (als Anzahl von Zeichen) darstellt.</span><span class="sxs-lookup"><span data-stu-id="30167-121">On creation, a size representing the X and Y dimensions (in count of characters) is required.</span></span> <span data-ttu-id="30167-122">Dies sind die Abmessungen, die auf die Anzeige Oberfläche für das endgültige Präsentations Fenster (Terminal) angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="30167-122">These are the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="30167-123">Die Werte werden verwendet, um einen in-Memory-Puffer im Pseudo Konsolensystem zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="30167-123">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span>

<span data-ttu-id="30167-124">Die Puffergröße bietet Antworten auf Client-Zeichenmodus-Anwendungen, die mithilfe der [Client seitigen Konsolenfunktionen](console-functions.md) wie [**getconsoleskreenbufferinfoex**](getconsolescreenbufferinfoex.md) nach Informationen suchen und das Layout und die Positionierung von Text vorschreiben, wenn Clients Funktionen wie " [**Beschreib teconsoleoutput**](writeconsoleoutput.md)" verwenden.</span><span class="sxs-lookup"><span data-stu-id="30167-124">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="30167-125">Zum Schluss wird ein Flags-Feld bei der Erstellung einer pseudoconsole zur Durchführung spezieller Funktionen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="30167-125">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="30167-126">Legen Sie diese Einstellung standardmäßig auf 0 fest, um keine besondere Funktionalität zu haben.</span><span class="sxs-lookup"><span data-stu-id="30167-126">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="30167-127">Zurzeit ist nur ein spezielles Flag verfügbar, um die ervererbungsquelle der Cursorposition von einer Konsolen Sitzung anzufordern, die bereits an den Aufrufer der pseudoconsole-API angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="30167-127">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="30167-128">Dies ist für die Verwendung in komplexeren Szenarien vorgesehen, in denen eine Host Anwendung, die eine Pseudo Konsolen Sitzung vorbereitet, selbst auch eine Client Zeichenmodus-Anwendung einer anderen Konsolen Umgebung ist.</span><span class="sxs-lookup"><span data-stu-id="30167-128">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span>

<span data-ttu-id="30167-129">Unten finden Sie einen Beispielcode Ausschnitt, der mit der Verwendung von "" erstellt wird, um ein paar von Kommunikations [**Kanälen einzurichten und**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) die Pseudo Konsole zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="30167-129">A sample snippet is provided below utilizing [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) to establish a pair of communication channels and create the pseudoconsole.</span></span>

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
><span data-ttu-id="30167-130">Dieser Code Ausschnitt ist unvollständig und wird nur für die Demonstration dieses bestimmten Aufrufes verwendet.</span><span class="sxs-lookup"><span data-stu-id="30167-130">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="30167-131">Sie müssen die Lebensdauer des **Handles** s entsprechend verwalten.</span><span class="sxs-lookup"><span data-stu-id="30167-131">You will need to manage the lifetime of the **HANDLE** s appropriately.</span></span> <span data-ttu-id="30167-132">Wenn die Lebensdauer von **Handles** nicht ordnungsgemäß verwaltet wird, kann dies zu deadlockszenarien führen, insbesondere bei synchronen e/a-aufrufen.</span><span class="sxs-lookup"><span data-stu-id="30167-132">Failure to manage the lifetime of **HANDLE** s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="30167-133">Nach Abschluss [**des Vorgangs zum**](https://msdn.microsoft.com/library/windows/desktop/ms682425) Erstellen einer Anwendung, die an die pseudoconsole angefügt ist, müssen die während der Erstellung angegebenen Handles von diesem Prozess freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="30167-133">Upon completion of the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="30167-134">Dadurch wird der Verweis Zähler für das zugrunde liegende Geräte Objekt verringert, und e/a-Vorgänge können einen unterbrochenen Kanal ordnungsgemäß erkennen, wenn die pseudoconsole-Sitzung seine Kopie der Handles schließt.</span><span class="sxs-lookup"><span data-stu-id="30167-134">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="30167-135">Die Erstellung des untergeordneten Prozesses wird vorbereitet.</span><span class="sxs-lookup"><span data-stu-id="30167-135">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="30167-136">Die nächste Phase besteht in der Vorbereitung der [**startupinfoex**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) -Struktur, die die pseudoconsole-Informationen beim Starten des untergeordneten Prozesses vermittelt.</span><span class="sxs-lookup"><span data-stu-id="30167-136">The next phase is to prepare the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="30167-137">Diese Struktur enthält die Möglichkeit, komplexe Startinformationen bereitzustellen, einschließlich der Attribute für die Prozess-und Thread Erstellung.</span><span class="sxs-lookup"><span data-stu-id="30167-137">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="30167-138">Verwenden Sie [**initializeprocthreadattributelist**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in einem doppelten Callcenter, um zunächst die Anzahl der Bytes zu berechnen, die zum Speichern der Liste erforderlich sind, den angeforderten Arbeitsspeicher zuzuordnen und dann erneut den nicht transparenten Speicher Zeiger bereitzustellen, um ihn als Attribut Liste einzurichten.</span><span class="sxs-lookup"><span data-stu-id="30167-138">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="30167-139">Führen Sie als nächstes [**updateprocthreadattribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) aus, indem Sie die initialisierte Attribut Liste mit dem-Flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, dem pseudoconsole-Handle und der Größe des pseudoconsole-Handles übergeben.</span><span class="sxs-lookup"><span data-stu-id="30167-139">Next, call [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

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

## <a name="creating-the-hosted-process"></a><span data-ttu-id="30167-140">Erstellen des gehosteten Prozesses</span><span class="sxs-lookup"><span data-stu-id="30167-140">Creating the Hosted Process</span></span>

<span data-ttu-id="30167-141">[**Rufen Sie als nächstes**](https://msdn.microsoft.com/library/windows/desktop/ms682425) die [**startupinfoex**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) -Struktur mit dem Pfad zur ausführbaren Datei und ggf. zusätzlichen Konfigurationsinformationen auf.</span><span class="sxs-lookup"><span data-stu-id="30167-141">Next, call [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passing the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="30167-142">Es ist wichtig, das **EXTENDED_STARTUPINFO_PRESENT** -Flag festzulegen, wenn aufgerufen wird, um das System zu warnen, dass der pseudoconsole-Verweis in den erweiterten Informationen enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="30167-142">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

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
> <span data-ttu-id="30167-143">Das Schließen der Pseudo Konsolen Sitzung, während der gehostete Prozess noch startet und eine Verbindung hergestellt wird, kann dazu führen, dass von der Client Anwendung ein Fehler Dialogfeld angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="30167-143">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="30167-144">Das gleiche Fehler Dialogfeld wird angezeigt, wenn dem gehosteten Prozess ein ungültiges Pseudo Konsolen Handle für den Start zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="30167-144">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="30167-145">Der Initialisierungs Code für den gehosteten Prozess ist identisch.</span><span class="sxs-lookup"><span data-stu-id="30167-145">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="30167-146">Im Popup Dialogfeld der gehosteten Client Anwendung bei einem Fehler wird `0xc0000142` eine lokalisierte Meldung mit der fehlerhaften Initialisierung gelesen.</span><span class="sxs-lookup"><span data-stu-id="30167-146">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="30167-147">Kommunikation mit der pseudoconsole-Sitzung</span><span class="sxs-lookup"><span data-stu-id="30167-147">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="30167-148">Nachdem der Prozess erfolgreich erstellt wurde, kann die Host Anwendung das schreibende der Eingabe Pipe verwenden, um Benutzer Interaktions Informationen an die pseudoconsole zu senden, und das leseende der ausgabepipe, um grafische Präsentationsinformationen von der Pseudo Konsole zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="30167-148">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span>

<span data-ttu-id="30167-149">Es ist vollständig für die Host Anwendung zu entscheiden, wie weitere Aktivitäten behandelt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="30167-149">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="30167-150">Die Hostinganwendung könnte ein Fenster in einem anderen Thread starten, um Benutzerinteraktionen zu erfassen und in das schreibende der Eingabe Pipe für die Pseudo Konsole und die Anwendung im gehosteten Zeichenmodus zu serialisieren.</span><span class="sxs-lookup"><span data-stu-id="30167-150">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="30167-151">Ein anderer Thread könnte gestartet werden, um das leseende der Ausgabe Pipe für die Pseudo Konsole zu entfernen, den Text und die Informationen zu den [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) zu decodieren und auf dem Bildschirm darzustellen.</span><span class="sxs-lookup"><span data-stu-id="30167-151">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span>

<span data-ttu-id="30167-152">Threads können auch verwendet werden, um die Informationen aus den pseudoconsole-Kanälen an einen anderen Kanal oder ein anderes Gerät zu übertragen, einschließlich eines Netzwerks an Remote Informationen an einen anderen Prozess oder Computer, und jegliche lokale Transcodierung der Informationen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="30167-152">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="30167-153">Ändern der Größe der pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="30167-153">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="30167-154">Während der Laufzeit gibt es möglicherweise eine Situation, in der die Größe des Puffers aufgrund einer Benutzerinteraktion oder einer Out-of-Band-Anforderung von einem anderen Anzeige-/Interaktionsgerät geändert werden muss.</span><span class="sxs-lookup"><span data-stu-id="30167-154">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="30167-155">Dies kann mit der [**resizepseudoconsole**](resizepseudoconsole.md) -Funktion durchgeführt werden, wobei die Höhe und die Breite des Puffers in der Anzahl von Zeichen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="30167-155">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

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

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="30167-156">Beenden der pseudoconsole-Sitzung</span><span class="sxs-lookup"><span data-stu-id="30167-156">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="30167-157">Um die Sitzung zu beenden, müssen Sie die Funktion [**closepseudoconsole**](closepseudoconsole.md) mit dem Handle aus der ursprünglichen Pseudo Konsolen Erstellung abrufen.</span><span class="sxs-lookup"><span data-stu-id="30167-157">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="30167-158">Alle angefügten Anwendungen im Zeichenmodus, wie z. b. der aus dem [**Vorgang "deateprocess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) ", werden beendet, wenn die Sitzung geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="30167-158">Any attached client character-mode applications, such as the one from the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="30167-159">Wenn das ursprüngliche untergeordnete Element eine shelltyp Anwendung war, die andere Prozesse erstellt, werden alle zugehörigen verknüpften Prozesse in der Struktur ebenfalls beendet.</span><span class="sxs-lookup"><span data-stu-id="30167-159">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

> [!WARNING]
><span data-ttu-id="30167-160">Das Schließen der Sitzung hat mehrere Nebeneffekte, die zu einer Deadlockbedingung führen können, wenn die Pseudo Konsole synchron mit einem Single Thread verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="30167-160">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="30167-161">Beim Schließen der pseudoconsole-Sitzung kann ein abschließendes Frame Update ausgegeben `hOutput` werden, das aus dem Kommunikationskanal Puffer abgeleitet werden soll.</span><span class="sxs-lookup"><span data-stu-id="30167-161">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="30167-162">Wenn außerdem `PSEUDOCONSOLE_INHERIT_CURSOR` beim Erstellen der pseudoconsole ausgewählt wurde, kann der Versuch, die pseudoconsole zu schließen, ohne auf die Cursor erstellungsabfragenmeldung (die empfangen `hOutput` und Antworten über übermittelt wird `hInput` ) zu einer anderen Deadlock-Bedingung führen.</span><span class="sxs-lookup"><span data-stu-id="30167-162">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="30167-163">Es wird empfohlen, dass Kommunikationskanäle für die pseudoconsole in einzelnen Threads gewartet werden und verbleibt, bis Sie von der Client Anwendung, die beendet wird, oder durch den Abschluss von Beendigungs-Aktivitäten beim Aufrufen der [**closepseudoconsole**](closepseudoconsole.md) -Funktion beendet und verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="30167-163">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>
