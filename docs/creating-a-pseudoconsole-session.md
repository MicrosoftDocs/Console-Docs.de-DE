---
title: Erstellen einer Pseudokonsolensitzung
description: Eine Pseudokonsolensitzung ermöglicht einer Anwendung das Hosten der Aktivitäten einer Zeichenmodusanwendung.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API, Kon-PTY, Pseudokonsole, Windows-PTY, Pseudo-Konsole
ms.localizationpriority: high
ms.openlocfilehash: c1a83b308e4d9a23fdb6b2778561030e619dfdb3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357930"
---
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="4776d-104">Erstellen einer Pseudokonsolensitzung</span><span class="sxs-lookup"><span data-stu-id="4776d-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="4776d-105">Die Windows-Pseudokonsole, manchmal auch als Pseudokonsole, Kon-PTY oder Windows-PTY bezeichnet, ist ein Mechanismus, der dazu dient, einen externen Host für Aktivitäten des Zeichenmodus-Subsystems zu schaffen, der den Anteil des Standardkonsolen-Hostfensters ersetzt, der für Benutzerinteraktivität vorgesehen ist.</span><span class="sxs-lookup"><span data-stu-id="4776d-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="4776d-106">Das Hosten einer Pseudokonsolensitzung unterscheidet sich etwas von einer herkömmlichen Konsolensitzung.</span><span class="sxs-lookup"><span data-stu-id="4776d-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="4776d-107">Herkömmliche Konsolensitzungen werden automatisch gestartet, wenn das Betriebssystem erkennt, dass eine Zeichenmodusanwendung ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="4776d-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="4776d-108">Im Gegensatz dazu müssen eine Pseudokonsolensitzung und die Kommunikationskanäle von der Hostinganwendung erstellt werden, bevor der Prozess mit der zu hostenden, untergeordneten Zeichenmodusanwendung erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4776d-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="4776d-109">Der untergeordnete Prozess wird trotzdem mithilfe der Funktion [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) erstellt, jedoch mit einigen zusätzlichen Informationen, die das Betriebssystem anweisen, die passende Umgebung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="4776d-109">The child process will still be created using the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="4776d-110">Weitere Hintergrundinformationen zu diesem System finden Sie im [Blogbeitrag mit der ursprünglichen Ankündigung](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="4776d-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="4776d-111">Ausführliche Beispiele zum Verwenden der Pseudokonsole finden Sie in unserem GitHub-Repository [microsoft/terminal](https://github.com/microsoft/terminal) im Beispielverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="4776d-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [microsoft/terminal](https://github.com/microsoft/terminal) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="4776d-112">Vorbereiten der Kommunikationskanäle</span><span class="sxs-lookup"><span data-stu-id="4776d-112">Preparing the communication channels</span></span>

<span data-ttu-id="4776d-113">Der erste Schritt besteht darin, ein Paar synchroner Kommunikationskanäle zu erstellen, die während der Erstellung der Pseudokonsolensitzung für die bidirektionale Kommunikation mit der gehosteten Anwendung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="4776d-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="4776d-114">Diese Kanäle werden vom Pseudokonsolensystem mithilfe von [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) und [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) mit [synchroner E/A](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="4776d-114">These channels are processed by the pseudoconsole system using [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="4776d-115">Datei- oder E/A-Gerätehandles wie ein Dateistream oder eine Pipe sind akzeptabel, sofern keine [**OVERLAPPED**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped)-Struktur für die asynchrone Kommunikation erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="4776d-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

> [!WARNING]
><span data-ttu-id="4776d-116">Zum Verhindern von Racebedingungen und Deadlocks empfehlen wir dringend, dass jeder der Kommunikationskanäle in einem separaten Thread bedient wird, der einen eigenen Clientpufferstatus und eine eigene Nachrichtenwarteschlange innerhalb Ihrer Anwendung aufweist.</span><span class="sxs-lookup"><span data-stu-id="4776d-116">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="4776d-117">Das Bedienen aller Aktivitäten der Pseudokonsole im gleichen Thread kann zu einem Deadlock führen, bei dem einer der Kommunikationspuffer gefüllt ist und auf Ihre Aktion wartet, während Sie versuchen, eine blockierende Anforderung an einen anderen Kanal zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="4776d-117">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="4776d-118">Erstellen der Pseudokonsole</span><span class="sxs-lookup"><span data-stu-id="4776d-118">Creating the Pseudoconsole</span></span>

<span data-ttu-id="4776d-119">Identifizieren Sie mithilfe der eingerichteten Kommunikationskanäle das „Leseende“ des Eingabekanals und das „Schreibende“ des Ausgabekanals.</span><span class="sxs-lookup"><span data-stu-id="4776d-119">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="4776d-120">Dieses Paar Handles wird beim Aufrufen von [**CreatePseudoConsole**](createpseudoconsole.md) zum Erstellen des Objekts bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4776d-120">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="4776d-121">Bei der Erstellung ist eine Größe erforderlich, die die X- und die Y-Abmessung (als Zeichenanzahl) darstellt.</span><span class="sxs-lookup"><span data-stu-id="4776d-121">On creation, a size representing the X and Y dimensions (in count of characters) is required.</span></span> <span data-ttu-id="4776d-122">Dies sind die Abmessungen, die wir für das endgültige (Terminal-) Präsentationsfenster auf die Anzeigeoberfläche anwenden.</span><span class="sxs-lookup"><span data-stu-id="4776d-122">These are the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="4776d-123">Die Werte werden verwendet, um innerhalb des Pseudokonsolensystems einen Puffer im Arbeitsspeicher zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4776d-123">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span>

<span data-ttu-id="4776d-124">Die Puffergröße wird als Antwort an Clientanwendungen im Zeichenmodus übergeben, die mithilfe der [clientseitigen Konsolenfunktionen](console-functions.md) wie [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) Informationen abzufragen versuchen, und gibt das Layout und die Positionierung von Text vor, wenn Clients Funktionen wie [**WriteConsoleOutput**](writeconsoleoutput.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="4776d-124">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="4776d-125">Schließlich wird bei der Erstellung einer Pseudokonsole ein Feld für Flags bereitgestellt, um besondere Funktionalität zu realisieren.</span><span class="sxs-lookup"><span data-stu-id="4776d-125">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="4776d-126">Standardmäßig ist es auf 0 festgelegt, was keine Sonderfunktionalität bedeutet.</span><span class="sxs-lookup"><span data-stu-id="4776d-126">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="4776d-127">Zurzeit ist nur ein besonderes Flag verfügbar, das die Vererbung der Cursorposition von einer Konsolensitzung anfordert, die dem Aufrufer der Pseudokonsolen-API bereits angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="4776d-127">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="4776d-128">Dies ist für die Verwendung in komplexeren Szenarien vorgesehen, in denen eine hostende Anwendung, die eine Pseudokonsolensitzung vorbereitet, ihrerseits ebenfalls als Clientanwendung im Zeichenmodus einer weiteren Konsolenumgebung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4776d-128">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span>

<span data-ttu-id="4776d-129">Im Codeausschnitt unten ist ein Beispiel angegeben, das [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) verwendet, um ein Paar Kommunikationskanäle einzurichten und die Pseudokonsole zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4776d-129">A sample snippet is provided below utilizing [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) to establish a pair of communication channels and create the pseudoconsole.</span></span>

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
><span data-ttu-id="4776d-130">Dieser Codeausschnitt ist unvollständig und dient nur zur Demonstration dieses bestimmten Aufrufs.</span><span class="sxs-lookup"><span data-stu-id="4776d-130">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="4776d-131">Sie müssen die Lebensdauer der **HANDLE** s passend verwalten.</span><span class="sxs-lookup"><span data-stu-id="4776d-131">You will need to manage the lifetime of the **HANDLE** s appropriately.</span></span> <span data-ttu-id="4776d-132">Wenn die Lebensdauer der **HANDLE** s nicht ordnungsgemäß verwaltet wird, kann dies zu Deadlockszenarien führen, insbesondere bei synchronen E/A-Aufrufen.</span><span class="sxs-lookup"><span data-stu-id="4776d-132">Failure to manage the lifetime of **HANDLE** s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="4776d-133">Beim Abschluss des [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)-Aufrufs, um die Clientanwendung im Zeichenmodus zu erstellen, die an die Pseudokonsole angefügt ist, sollten die während der Erstellung übergebenen Handles von diesem Prozess freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="4776d-133">Upon completion of the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="4776d-134">Dadurch wird die Verweisanzahl des zugrundeliegenden Geräteobjekts verringert, und E/A-Vorgänge können einen unterbrochenen Kanal ordnungsgemäß erkennen, wenn die Pseudokonsolensitzung ihre Kopie der Handles schließt.</span><span class="sxs-lookup"><span data-stu-id="4776d-134">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="4776d-135">Vorbereiten der Erstellung des untergeordneten Prozesses</span><span class="sxs-lookup"><span data-stu-id="4776d-135">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="4776d-136">Die nächste Phase besteht im Vorbereiten der Struktur [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw), die die Pseudokonsoleninformationen beim Starten des untergeordneten Prozesses übermittelt.</span><span class="sxs-lookup"><span data-stu-id="4776d-136">The next phase is to prepare the [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="4776d-137">Diese Struktur bietet die Möglichkeit, komplexe Startinformationen einschließlich Attributen für die Prozess- und Threaderstellung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="4776d-137">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="4776d-138">Verwenden Sie [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in der Art eines Doppelaufrufs, um zuerst die Anzahl der erforderlichen Bytes zum Aufnehmen der Liste zu berechnen, den angeforderten Arbeitsspeicher zuzuweisen und dann in einem erneuten Aufruf den opaken Arbeitsspeicherzeiger zu übergeben, um ihn als Attributliste einrichten zu lassen.</span><span class="sxs-lookup"><span data-stu-id="4776d-138">Use [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="4776d-139">Rufen Sie anschließend [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) auf, und übergeben Sie die initialisierte Attributliste mit dem Flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, das Handle der Pseudokonsole und die Größe des Handles der Pseudokonsole.</span><span class="sxs-lookup"><span data-stu-id="4776d-139">Next, call [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

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

## <a name="creating-the-hosted-process"></a><span data-ttu-id="4776d-140">Erstellen des gehosteten Prozesses</span><span class="sxs-lookup"><span data-stu-id="4776d-140">Creating the Hosted Process</span></span>

<span data-ttu-id="4776d-141">Rufen Sie als nächstes [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) auf, und übergeben Sie die [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw)-Struktur zusammen mit dem Pfad zur ausführbaren Datei und allen weiteren Konfigurationsinformationen, sofern zutreffend.</span><span class="sxs-lookup"><span data-stu-id="4776d-141">Next, call [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) passing the [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="4776d-142">Es ist wichtig, beim Aufrufen das Flag **EXTENDED_STARTUPINFO_PRESENT** festzulegen, um das System darüber zu informieren, dass der Verweis auf die Pseudokonsole in den erweiterten Informationen enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="4776d-142">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

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
> <span data-ttu-id="4776d-143">Das Schließen der Pseudokonsolensitzung, während der gehostete Prozess noch gestartet wird und eine Verbindung herstellt, kann dazu führen, dass die Clientanwendung ein Fehlerdialogfeld anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4776d-143">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="4776d-144">Das gleiche Fehlerdialogfeld wird angezeigt, wenn dem gehosteten Prozess beim Start ein ungültiges Handle für die Pseudokonsole übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="4776d-144">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="4776d-145">Aus der Sicht des Initialisierungscodes des gehosteten Prozesses sind die zwei Bedingungen identisch.</span><span class="sxs-lookup"><span data-stu-id="4776d-145">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="4776d-146">Das Popupdialogfeld der gehosteten Clientanwendung lautet `0xc0000142`, mit einer lokalisierten Meldung, die den Initialisierungsfehler im Detail angibt.</span><span class="sxs-lookup"><span data-stu-id="4776d-146">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="4776d-147">Kommunikation mit der Pseudokonsolensitzung</span><span class="sxs-lookup"><span data-stu-id="4776d-147">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="4776d-148">Nach der erfolgreichen Erstellung des Prozesses kann die hostende Anwendung das Schreibende der Eingabepipe verwenden, um Informationen zur Benutzerinteraktion an die Pseudokonsole zu senden, und das Leseende der Ausgabepipe, um Informationen zur grafischen Darstellung von der Pseudokonsole zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="4776d-148">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span>

<span data-ttu-id="4776d-149">Die Entscheidung, wie weitere Aktivitäten behandelt werden, liegt ausschließlich bei der hostenden Anwendung.</span><span class="sxs-lookup"><span data-stu-id="4776d-149">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="4776d-150">Die hostende Anwendung kann etwa ein Fenster in einem anderen Thread starten, um Eingaben aus der Benutzerinteraktion zu erfassen und sie für die Pseudokonsole und die gehostete Zeichenmodusanwendung in das Schreibende der Eingabepipe zu serialisieren.</span><span class="sxs-lookup"><span data-stu-id="4776d-150">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="4776d-151">Ein weiterer Thread könnte gestartet werden, der das Leseende der Ausgabepipe für die Pseudokonsole leert, den Text und die Informationen der [virtuellen Terminalsequenz](console-virtual-terminal-sequences.md) decodiert und sie auf dem Bildschirm ausgibt.</span><span class="sxs-lookup"><span data-stu-id="4776d-151">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span>

<span data-ttu-id="4776d-152">Threads können außerdem verwendet werden, um die Informationen aus den Kanälen der Pseudokonsole an einen anderen Kanal oder ein anderes Gerät zu übertragen, einschließlich eines Netzwerks, um Informationen remote an einen anderen Prozess oder Computer zu übergeben und jegliche lokale Transcodierung der Informationen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="4776d-152">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="4776d-153">Ändern der Größe der Pseudokonsole</span><span class="sxs-lookup"><span data-stu-id="4776d-153">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="4776d-154">Zur Laufzeit kann ein Umstand eintreten, durch den die Größe des Puffers aufgrund einer Benutzerinteraktion oder einer außer der Reihe empfangenen Anforderung von einem anderen Anzeige-/Interaktionsgerät geändert werden muss.</span><span class="sxs-lookup"><span data-stu-id="4776d-154">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="4776d-155">Dies kann mit der [**ResizePseudoConsole**](resizepseudoconsole.md)-Funktion erfolgen, die sowohl die Höhe als auch die Breite des Puffers in Form einer Zeichenanzahl angibt.</span><span class="sxs-lookup"><span data-stu-id="4776d-155">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

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

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="4776d-156">Beenden der Pseudokonsolensitzung</span><span class="sxs-lookup"><span data-stu-id="4776d-156">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="4776d-157">Um die Sitzung zu beenden, rufen Sie die Funktion [**ClosePseudoConsole**](closepseudoconsole.md) mit dem Handle aus der ursprünglichen Erstellung der Pseudokonsole auf.</span><span class="sxs-lookup"><span data-stu-id="4776d-157">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="4776d-158">Alle verknüpften Clientanwendungen im Zeichenmodus, wie etwa die aus dem [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)-Aufruf, werden beim Schließen der Sitzung beendet.</span><span class="sxs-lookup"><span data-stu-id="4776d-158">Any attached client character-mode applications, such as the one from the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="4776d-159">Wenn das ursprüngliche untergeordnete Element eine Anwendung vom Shelltyp war, die andere Prozesse erstellt, werden alle zugehörigen verknüpften Prozesse in der Struktur ebenfalls beendet.</span><span class="sxs-lookup"><span data-stu-id="4776d-159">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

> [!WARNING]
><span data-ttu-id="4776d-160">Das Schließen der Sitzung hat eine Reihe von Nebenwirkungen, die zu einer Deadlocksituation führen können, wenn die Pseudokonsole synchron in einem einzelnen Thread ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4776d-160">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="4776d-161">Der Vorgang des Schließens der Pseudokonsolensitzung kann zum Senden eines finalen Frameupdates an `hOutput` führen, das aus dem Puffer des Kommunikationskanals entfernt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="4776d-161">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="4776d-162">Wenn beim Erstellen der Pseudokonsole `PSEUDOCONSOLE_INHERIT_CURSOR` ausgewählt war, kann der Versuch, die Pseudokonsole zu schließen, ohne auf die Nachricht zur Abfrage der Cursorvererbung zu reagieren (die an `hOutput` empfangen wurde und über `hInput` beantwortet wird), eine andere Deadlockbedingung verursachen.</span><span class="sxs-lookup"><span data-stu-id="4776d-162">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="4776d-163">Es wird empfohlen, dass die Kommunikationskanäle für die Pseudokonsole auf einzelnen Threads bedient werden und so lange entleert und verarbeitet bleiben, bis sie von sich aus durch das Beenden der Clientanwendung oder durch den Abschluss der Löschaktivitäten beim Aufruf der Funktion [**ClosePseudoConsole**](closepseudoconsole.md) unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="4776d-163">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>