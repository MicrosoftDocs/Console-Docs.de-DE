---
title: SetConsoleCtrlHandler-Funktion
description: Fügt eine von der Anwendung definierte HandlerRoutine-Funktion zur Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt sie aus dieser.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 03e7166f84be2f760a4ffea385225390bdb3ffa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357710"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="b1201-104">SetConsoleCtrlHandler-Funktion</span><span class="sxs-lookup"><span data-stu-id="b1201-104">SetConsoleCtrlHandler function</span></span>

<span data-ttu-id="b1201-105">Fügt eine von der Anwendung definierte [**HandlerRoutine**](handlerroutine.md)-Funktion zur Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt sie aus dieser.</span><span class="sxs-lookup"><span data-stu-id="b1201-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="b1201-106">Wenn keine Handlerfunktion angegeben wird, legt die Funktion ein vererbbares Attribut fest, das bestimmt, ob der aufrufende Prozess <kbd>STRG</kbd>+<kbd>C</kbd>-Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b1201-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1201-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1201-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a><span data-ttu-id="b1201-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="b1201-108">Parameters</span></span>

<span data-ttu-id="b1201-109">*HandlerRoutine* \[in, optional\]</span><span class="sxs-lookup"><span data-stu-id="b1201-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="b1201-110">Ein Zeiger auf die von der Anwendung definierte [**HandlerRoutine**](handlerroutine.md)-Funktion, die hinzugefügt oder entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b1201-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="b1201-111">Dieser Parameter kann **NULL** sein.</span><span class="sxs-lookup"><span data-stu-id="b1201-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="b1201-112">*Add* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b1201-112">*Add* \[in\]</span></span>  
<span data-ttu-id="b1201-113">Wenn dieser Parameter **TRUE** ist, wird der Handler hinzugefügt. Ist er **FALSE**, wird der Handler entfernt.</span><span class="sxs-lookup"><span data-stu-id="b1201-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="b1201-114">Wenn der *HandlerRoutine*-Parameter **NULL** ist, bewirkt der Wert **TRUE**, dass der aufrufende Prozess die Eingabe von <kbd>STRG</kbd>+<kbd>C</kbd> ignoriert, während beim Wert **FALSE** die normale Verarbeitung der Eingabe von <kbd>STRG</kbd>+<kbd>C</kbd> wiederhergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="b1201-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> input, and a **FALSE** value restores normal processing of <kbd>CTRL</kbd>+<kbd>C</kbd> input.</span></span> <span data-ttu-id="b1201-115">Dieses Attribut zum Ignorieren oder Verarbeiten von <kbd>STRG</kbd>+<kbd>C</kbd> wird von untergeordneten Prozessen geerbt.</span><span class="sxs-lookup"><span data-stu-id="b1201-115">This attribute of ignoring or processing <kbd>CTRL</kbd>+<kbd>C</kbd> is inherited by child processes.</span></span>

## <a name="return-value"></a><span data-ttu-id="b1201-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b1201-116">Return value</span></span>

<span data-ttu-id="b1201-117">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="b1201-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b1201-118">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="b1201-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b1201-119">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="b1201-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b1201-120">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="b1201-120">Remarks</span></span>

<span data-ttu-id="b1201-121">Diese Funktion bietet eine ähnliche Benachrichtigung für Konsolenanwendungen und-Dienste, wie sie [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) für grafische Anwendungen mit einem Nachrichtensystem bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="b1201-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="b1201-122">Sie könnten diese Funktion auch aus einer grafischen Anwendung heraus verwenden, es ist aber nicht sichergestellt, dass sie vor der Benachrichtigung von **WM\_QUERYENDSESSION** eingehen würde.</span><span class="sxs-lookup"><span data-stu-id="b1201-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="b1201-123">Für jeden Konsolenprozess gibt es eine eigene Liste mit anwendungsdefinierten [**HandlerRoutine**](handlerroutine.md)-Funktionen, die <kbd>STRG</kbd>+<kbd>C</kbd>- und <kbd>STRG</kbd>+<kbd>UNTBR</kbd>-Signale verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="b1201-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signals.</span></span> <span data-ttu-id="b1201-124">Die Handlerfunktionen verarbeiten außerdem Signale, die vom System generiert werden, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt.</span><span class="sxs-lookup"><span data-stu-id="b1201-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="b1201-125">Anfänglich enthält die Handlerliste für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)-Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="b1201-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="b1201-126">Ein Konsolenprozess fügt zusätzliche Handlerfunktionen hinzu oder entfernt diese, indem er die Funktion **SetConsoleCtrlHandler** aufruft, was sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt.</span><span class="sxs-lookup"><span data-stu-id="b1201-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="b1201-127">Wenn ein Konsolenprozess eins der Steuersignale empfängt, werden seine Handlerfunktionen der Reihe nach beginnend mit der zuletzt registrierten aufgerufen, bis einer der Handler `TRUE` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="b1201-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns `TRUE`.</span></span> <span data-ttu-id="b1201-128">Wenn keiner der Handler `TRUE` zurückgibt, wird der Standardhandler aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b1201-128">If none of the handlers returns `TRUE`, the default handler is called.</span></span>

<span data-ttu-id="b1201-129">Für Konsolenprozesse werden die Tastenkombinationen <kbd>STRG</kbd>+<kbd>C</kbd> und <kbd>STRG</kbd>+<kbd>UNTBR</kbd> normalerweise als Signale (**STRG\_C\_EVENT** und **STRG\_BREAK\_EVENT**) behandelt.</span><span class="sxs-lookup"><span data-stu-id="b1201-129">For console processes, the <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="b1201-130">Wenn ein Konsolenfenster mit Tastaturfokus <kbd>STRG</kbd>+<kbd>C</kbd> oder <kbd>STRG</kbd>+<kbd>UNTBR</kbd> empfängt, wird das Signal normalerweise an alle Prozesse übergeben, die die betreffende Konsole gemeinsam verwenden.</span><span class="sxs-lookup"><span data-stu-id="b1201-130">When a console window with the keyboard focus receives <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="b1201-131"><kbd>STRG</kbd>+<kbd>UNTBR</kbd> wird immer als Signal behandelt, aber das Verhalten von <kbd>STRG</kbd>+<kbd>C</kbd> kann normalerweise auf drei Arten geändert werden, die das Aufrufen der Handlerfunktionen verhindern:</span><span class="sxs-lookup"><span data-stu-id="b1201-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but typical <kbd>CTRL</kbd>+<kbd>C</kbd> behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="b1201-132">Die Funktion [**SetConsoleMode**](setconsolemode.md) kann den Modus **ENABLE\_PROCESSED\_INPUT** für den Eingabepuffer einer Konsole deaktivieren, sodass <kbd>STRG</kbd>+<kbd>C</kbd> als Tastatureingabe statt als Signal gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="b1201-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so <kbd>CTRL</kbd>+<kbd>C</kbd> is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="b1201-133">Das Aufrufen von **SetConsoleCtrlHandler** mit den Argumenten **NULL** und **TRUE** bewirkt, dass der aufrufende Prozess <kbd>STRG</kbd>+<kbd>C</kbd>-Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b1201-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span> <span data-ttu-id="b1201-134">Dieses Attribut wird von untergeordneten Prozessen geerbt, kann jedoch von jedem Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse davon betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="b1201-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="b1201-135">Wenn ein Konsolenprozess debuggt wird und <kbd>STRG</kbd>+<kbd>C</kbd>-Signale nicht deaktiviert wurden, generiert das System eine **DBG\_CONTROL\_C**-Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="b1201-135">If a console process is being debugged and <kbd>CTRL</kbd>+<kbd>C</kbd> signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="b1201-136">Diese Ausnahme wird nur zum Nutzen des Debuggers ausgelöst, und eine Anwendung sollte niemals einen Ausnahmehandler verwenden, um sie zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="b1201-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="b1201-137">Wenn der Debugger die Ausnahme behandelt, wird das <kbd>STRG</kbd>+<kbd>C</kbd>-Signal von einer Anwendung nicht bemerkt, mit einer Ausnahme: Warnungsfähige Wartebedingungen werden beendet.</span><span class="sxs-lookup"><span data-stu-id="b1201-137">If the debugger handles the exception, an application will not notice the <kbd>CTRL</kbd>+<kbd>C</kbd>, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="b1201-138">Wenn der Debugger die Ausnahme unverarbeitet übergibt, wird <kbd>STRG</kbd>+<kbd>C</kbd> an den Konsolenprozess übergeben und als Signal behandelt, wie zuvor erörtert.</span><span class="sxs-lookup"><span data-stu-id="b1201-138">If the debugger passes the exception on unhandled, <kbd>CTRL</kbd>+<kbd>C</kbd> is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="b1201-139">Ein Konsolenprozess kann die Funktion [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) verwenden, um ein <kbd>STRG</kbd>+<kbd>C</kbd>- oder <kbd>STRG</kbd>+<kbd>BREAK</kbd>-Signal an eine Konsolenprozessgruppe zu senden.</span><span class="sxs-lookup"><span data-stu-id="b1201-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signal to a console process group.</span></span>

<span data-ttu-id="b1201-140">Das System generiert **CTRL\_CLOSE\_EVENT**-, **CTRL\_LOGOFF\_EVENT**- und **CTRL\_SHUTDOWN\_EVENT**-Signale, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt, sodass der Prozess Gelegenheit hat, vor der Beendigung aufzuräumen.</span><span class="sxs-lookup"><span data-stu-id="b1201-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="b1201-141">Konsolenfunktionen oder beliebige C-Laufzeitfunktionen, die Konsolenfunktionen aufrufen, funktionieren möglicherweise nicht zuverlässig, während eins dieser zuvor erwähnten Signale verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="b1201-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="b1201-142">Dies hat den Grund, dass möglicherweise einige oder alle ihrer internen Routinen zur Konsolenbereinigung aufgerufen wurden, bevor der Prozesssignalhandler ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b1201-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="b1201-143">**Windows 7, Windows 8, Windows 8.1 und Windows 10:**</span><span class="sxs-lookup"><span data-stu-id="b1201-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="b1201-144">Wenn eine Konsolenanwendung die gdi32.dll- oder user32.dll-Bibliothek lädt, wird die [**HandlerRoutine**](handlerroutine.md)-Funktion, die Sie beim Aufrufen von **SetConsoleCtrlHandler** angeben, für die Ereignisse **CTRL\_LOGOFF\_EVENT** und **CTRL\_SHUTDOWN\_EVENT** nicht aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b1201-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="b1201-145">Das Betriebssystem erkennt Prozesse, die gdi32.dll oder user32.dll laden, als Windows-Anwendungen und nicht als Konsolenanwendungen.</span><span class="sxs-lookup"><span data-stu-id="b1201-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="b1201-146">Dieses Verhalten tritt auch bei Konsolenanwendungen auf, die keine Funktionen in gdi32.dll oder user32.dll direkt aufrufen, sondern Funktionen wie etwa [Shellfunktionen](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) aufrufen, die ihrerseits Funktionen in gdi32.dll oder user32.dll aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b1201-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="b1201-147">Zum Empfangen von Ereignissen, wenn sich ein Benutzer abmeldet oder das Gerät unter diesen Umständen heruntergefahren wird, erstellen Sie ein verborgenes Fenster in Ihrer Konsolenanwendung, und verarbeiten Sie dann die Fensternachrichten [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) und [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession), die vom verborgenen Fenster empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="b1201-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) and [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) window messages that the hidden window receives.</span></span> <span data-ttu-id="b1201-148">Sie können ein ausgeblendetes Fenster erstellen, indem Sie die Methode [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) mit auf 0 festgelegtem Parameter *dwExStyle* aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b1201-148">You can create a hidden window by calling the [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) method with the *dwExStyle* parameter set to 0.</span></span>

## <a name="examples"></a><span data-ttu-id="b1201-149">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b1201-149">Examples</span></span>

<span data-ttu-id="b1201-150">Ein Beispiel finden Sie unter [Registrieren einer Steuerelementhandler-Funktion](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="b1201-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b1201-151">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b1201-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b1201-152">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b1201-152">Minimum supported client</span></span> | <span data-ttu-id="b1201-153">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="b1201-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b1201-154">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b1201-154">Minimum supported server</span></span> | <span data-ttu-id="b1201-155">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="b1201-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b1201-156">Header</span><span class="sxs-lookup"><span data-stu-id="b1201-156">Header</span></span> | <span data-ttu-id="b1201-157">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="b1201-157">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b1201-158">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="b1201-158">Library</span></span> | <span data-ttu-id="b1201-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b1201-159">Kernel32.lib</span></span> |
| <span data-ttu-id="b1201-160">DLL</span><span class="sxs-lookup"><span data-stu-id="b1201-160">DLL</span></span> | <span data-ttu-id="b1201-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b1201-161">Kernel32.dll</span></span> |
| <span data-ttu-id="b1201-162">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="b1201-162">Unicode and ANSI names</span></span> | |

## <a name="see-also"></a><span data-ttu-id="b1201-163">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b1201-163">See also</span></span>

[<span data-ttu-id="b1201-164">Konsolen-Bearbeitungssteuerelemente</span><span class="sxs-lookup"><span data-stu-id="b1201-164">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="b1201-165">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b1201-165">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b1201-166">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="b1201-166">**ExitProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[<span data-ttu-id="b1201-167">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="b1201-167">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="b1201-168">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="b1201-168">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="b1201-169">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="b1201-169">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="b1201-170">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="b1201-170">**SetConsoleMode**</span></span>](setconsolemode.md)