---
title: SetConsoleCtrlHandler-Funktion
description: Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt Sie.
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
ms.openlocfilehash: 1c5c67bc5900a36bb50c0da90516fab0cec2e366
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039418"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="6938f-104">SetConsoleCtrlHandler-Funktion</span><span class="sxs-lookup"><span data-stu-id="6938f-104">SetConsoleCtrlHandler function</span></span>

<span data-ttu-id="6938f-105">Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der [**Handlerfunktionen**](handlerroutine.md) für den aufrufenden Prozess hinzu oder entfernt Sie.</span><span class="sxs-lookup"><span data-stu-id="6938f-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="6938f-106">Wenn keine Handlerfunktion angegeben wird, legt die Funktion ein Vererb bares Attribut fest, das bestimmt, ob der aufrufende Prozess <kbd>STRG</kbd>- + <kbd>C</kbd> -Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="6938f-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span>

## <a name="syntax"></a><span data-ttu-id="6938f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6938f-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a><span data-ttu-id="6938f-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="6938f-108">Parameters</span></span>

<span data-ttu-id="6938f-109">*Handlerroutine* \[ in, optional\]</span><span class="sxs-lookup"><span data-stu-id="6938f-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="6938f-110">Ein Zeiger auf die Anwendungs definierte [**Handlerroutine**](handlerroutine.md) -Funktion, die hinzugefügt oder entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="6938f-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="6938f-111">Dieser Parameter kann **null** sein.</span><span class="sxs-lookup"><span data-stu-id="6938f-111">This parameter can be **NULL** .</span></span>

<span data-ttu-id="6938f-112">*Hinzufügen* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6938f-112">*Add* \[in\]</span></span>  
<span data-ttu-id="6938f-113">Wenn dieser Parameter **true** ist, wird der Handler hinzugefügt. Wenn der Wert **false** ist, wird der Handler entfernt.</span><span class="sxs-lookup"><span data-stu-id="6938f-113">If this parameter is **TRUE** , the handler is added; if it is **FALSE** , the handler is removed.</span></span>

<span data-ttu-id="6938f-114">Wenn der *Handlerroutine* -Parameter **null** ist, bewirkt ein **true** -Wert, dass der aufrufenden Prozess <kbd>STRG</kbd> + <kbd>c</kbd> -Eingaben ignoriert, und ein **false** -Wert stellt die normale Verarbeitung von <kbd>STRG</kbd> + <kbd>c</kbd> -Eingaben wieder her.</span><span class="sxs-lookup"><span data-stu-id="6938f-114">If the *HandlerRoutine* parameter is **NULL** , a **TRUE** value causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> input, and a **FALSE** value restores normal processing of <kbd>CTRL</kbd>+<kbd>C</kbd> input.</span></span> <span data-ttu-id="6938f-115">Dieses Attribut zum ignorieren oder Verarbeiten von <kbd>STRG</kbd> + <kbd>C</kbd> wird von untergeordneten Prozessen geerbt.</span><span class="sxs-lookup"><span data-stu-id="6938f-115">This attribute of ignoring or processing <kbd>CTRL</kbd>+<kbd>C</kbd> is inherited by child processes.</span></span>

## <a name="return-value"></a><span data-ttu-id="6938f-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="6938f-116">Return value</span></span>

<span data-ttu-id="6938f-117">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="6938f-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6938f-118">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="6938f-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6938f-119">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="6938f-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="6938f-120">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="6938f-120">Remarks</span></span>

<span data-ttu-id="6938f-121">Diese Funktion bietet eine ähnliche Benachrichtigung für Konsolen Anwendungen und-Dienste, die [**WM \_ queryendsession**](https://msdn.microsoft.com/library/windows/desktop/aa376890) für grafische Anwendungen mit einem nachrichtenpump bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="6938f-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="6938f-122">Sie können diese Funktion auch aus einer grafischen Anwendung verwenden, aber es gibt keine Garantie, dass Sie vor der Benachrichtigung von **WM \_ queryendsession** eintreffen würde.</span><span class="sxs-lookup"><span data-stu-id="6938f-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION** .</span></span>

<span data-ttu-id="6938f-123">Jeder Konsolen Prozess verfügt über eine eigene Liste von Anwendungs definierten [**Handlerroutine**](handlerroutine.md) -Funktionen, die die Tastenkombination <kbd>STRG</kbd> + <kbd>C</kbd> und <kbd>STRG</kbd>drücken + <kbd>BREAK</kbd> .</span><span class="sxs-lookup"><span data-stu-id="6938f-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signals.</span></span> <span data-ttu-id="6938f-124">Die Handlerfunktionen behandeln auch Signale, die vom System generiert werden, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt.</span><span class="sxs-lookup"><span data-stu-id="6938f-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="6938f-125">Anfänglich enthält die Handlerliste für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="6938f-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="6938f-126">Bei einem Konsolen Prozess werden zusätzliche Handlerfunktionen durch Aufrufen der **SetConsoleCtrlHandler** -Funktion hinzugefügt oder entfernt, die sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt.</span><span class="sxs-lookup"><span data-stu-id="6938f-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="6938f-127">Wenn ein Konsolen Prozess eines der Steuersignale empfängt, werden seine Handlerfunktionen für eine zuletzt registrierte, erste Methode aufgerufen, bis einer der Handler zurückgibt `TRUE` .</span><span class="sxs-lookup"><span data-stu-id="6938f-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns `TRUE`.</span></span> <span data-ttu-id="6938f-128">Wenn keiner der Handler zurückgibt `TRUE` , wird der Standard Handler aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="6938f-128">If none of the handlers returns `TRUE`, the default handler is called.</span></span>

<span data-ttu-id="6938f-129">Bei Konsolen Prozessen werden die <kbd>CTRL</kbd> + Tastenkombinationen STRG <kbd>c</kbd> und <kbd>STRG</kbd>- + <kbd>BREAK</kbd> Taste normalerweise als Signale behandelt ( **Strg c- \_ \_ Ereignis** und **STRG-Break- \_ \_ Ereignis** ).</span><span class="sxs-lookup"><span data-stu-id="6938f-129">For console processes, the <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations are typically treated as signals ( **CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT** ).</span></span> <span data-ttu-id="6938f-130">Wenn ein Konsolenfenster mit dem Tastaturfokus <kbd>STRG</kbd> + <kbd>C</kbd> oder <kbd>STRG</kbd>-Taste erhält + <kbd>BREAK</kbd>, wird das Signal in der Regel an alle Prozesse weitergegeben, die die Konsole freigeben.</span><span class="sxs-lookup"><span data-stu-id="6938f-130">When a console window with the keyboard focus receives <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="6938f-131"><kbd>STRG</kbd> + " <kbd>Break</kbd> " wird immer als Signal behandelt, aber das typische <kbd>STRG</kbd>- + <kbd>C</kbd> -Verhalten kann auf drei Arten geändert werden, die verhindern, dass die Handlerfunktionen aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="6938f-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but typical <kbd>CTRL</kbd>+<kbd>C</kbd> behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="6938f-132">Die [**setconsolemode**](setconsolemode.md) -Funktion kann den aktivierte **\_ \_ Eingabe** Modus für den Eingabepuffer einer Konsole deaktivieren, sodass <kbd>STRG</kbd> + <kbd>C</kbd> als Tastatureingabe und nicht als Signal gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="6938f-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so <kbd>CTRL</kbd>+<kbd>C</kbd> is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="6938f-133">Der Aufruf von **SetConsoleCtrlHandler** mit den Argumenten **null** und **true** bewirkt, dass der aufrufende Prozess <kbd>STRG</kbd> + <kbd>C</kbd> -Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="6938f-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span> <span data-ttu-id="6938f-134">Dieses Attribut wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="6938f-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="6938f-135">Wenn ein Konsolen Prozess gedebuggt wird und <kbd>STRG</kbd> + <kbd>C</kbd> -Signale nicht deaktiviert wurden, generiert das System eine **dbg-Steuerungs- \_ \_ c** -Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="6938f-135">If a console process is being debugged and <kbd>CTRL</kbd>+<kbd>C</kbd> signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="6938f-136">Diese Ausnahme wird nur für den Vorteil des Debuggers ausgelöst, und eine Anwendung sollte niemals einen Ausnahmehandler verwenden, um Sie zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="6938f-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="6938f-137">Wenn der Debugger die Ausnahme behandelt, wird die <kbd>STRG</kbd>-Taste für eine Anwendung nicht bemerkt + <kbd>C</kbd>, mit einer Ausnahme: mindestwarnzeit-warte Vorgänge werden beendet.</span><span class="sxs-lookup"><span data-stu-id="6938f-137">If the debugger handles the exception, an application will not notice the <kbd>CTRL</kbd>+<kbd>C</kbd>, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="6938f-138">Wenn der Debugger die Ausnahme bei nicht behandelter übergibt, wird <kbd>STRG</kbd> + <kbd>C</kbd> an den Konsolen Prozess weitergeleitet und als Signal behandelt, wie bereits erläutert.</span><span class="sxs-lookup"><span data-stu-id="6938f-138">If the debugger passes the exception on unhandled, <kbd>CTRL</kbd>+<kbd>C</kbd> is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="6938f-139">Ein Konsolen Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um ein <kbd>STRG</kbd> + <kbd>C</kbd> -oder <kbd>STRG</kbd>-halte + <kbd>BREAK</kbd> Signal an eine Konsolen Prozessgruppe zu senden.</span><span class="sxs-lookup"><span data-stu-id="6938f-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signal to a console process group.</span></span>

<span data-ttu-id="6938f-140">Das System generiert das STRG-Schließ **\_ \_ Ereignis** , das STRG-Abmelde **\_ \_ Ereignis** und das **STRG-Shutdown- \_ \_ Ereignis** Signal, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt, sodass der Prozess vor dem beenden eine Bereinigung durchführt.</span><span class="sxs-lookup"><span data-stu-id="6938f-140">The system generates **CTRL\_CLOSE\_EVENT** , **CTRL\_LOGOFF\_EVENT** , and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="6938f-141">Konsolenfunktionen oder alle C-Lauf Zeitfunktionen, die Konsolenfunktionen aufzurufen, funktionieren möglicherweise nicht zuverlässig während der Verarbeitung der drei Signale, die zuvor erwähnt wurden.</span><span class="sxs-lookup"><span data-stu-id="6938f-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="6938f-142">Der Grund hierfür ist, dass möglicherweise einige oder alle der internen Konsolen Bereinigungs Routinen aufgerufen wurden, bevor der Prozess Signalhandler ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="6938f-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="6938f-143">**Windows 7, Windows 8, Windows 8.1 und Windows 10:**</span><span class="sxs-lookup"><span data-stu-id="6938f-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="6938f-144">Wenn eine Konsolenanwendung die gdi32.dll oder user32.dll Bibliothek lädt, wird die [**Handlerroutine**](handlerroutine.md) -Funktion, die Sie beim Aufrufen von **SetConsoleCtrlHandler** angeben, nicht für das STRG-Abmelde **\_ \_ Ereignis** und **STRG-Shutdown- \_ \_ Ereignis** Ereignisse aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="6938f-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="6938f-145">Das Betriebssystem erkennt Prozesse, die gdi32.dll oder user32.dll als Windows-Anwendungen und nicht als Konsolen Anwendungen laden.</span><span class="sxs-lookup"><span data-stu-id="6938f-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="6938f-146">Dieses Verhalten tritt auch bei Konsolen Anwendungen auf, die keine Funktionen in gdi32.dll oder user32.dll direkt aufzurufen, aber Funktionen wie [Shellfunktionen](https://msdn.microsoft.com/library/windows/desktop/bb776426) aufzurufen, die wiederum Funktionen in gdi32.dll oder user32.dll aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="6938f-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](https://msdn.microsoft.com/library/windows/desktop/bb776426) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="6938f-147">Um Ereignisse zu empfangen, wenn ein Benutzer sich abmeldet oder das Gerät unter diesen Umständen heruntergefahren wird, erstellen Sie ein ausgeblendetes Fenster in der Konsolenanwendung, und behandeln Sie dann die Nachrichten des WM-Fensters [**\_ queryendsession**](https://msdn.microsoft.com/library/windows/desktop/aa376890) und [**WM \_ EndSession**](https://msdn.microsoft.com/library/windows/desktop/aa376889) , die das verborgene Fenster empfängt.</span><span class="sxs-lookup"><span data-stu-id="6938f-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) and [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) window messages that the hidden window receives.</span></span> <span data-ttu-id="6938f-148">Sie können ein verborgenes Fenster erstellen, indem Sie die [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) -Methode aufrufen, wobei der *dwExStyle* -Parameter auf 0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="6938f-148">You can create a hidden window by calling the [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) method with the *dwExStyle* parameter set to 0.</span></span>

## <a name="examples"></a><span data-ttu-id="6938f-149">Beispiele</span><span class="sxs-lookup"><span data-stu-id="6938f-149">Examples</span></span>

<span data-ttu-id="6938f-150">Ein Beispiel finden Sie unter [Registrieren einer Steuerelement Handler-Funktion](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="6938f-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6938f-151">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="6938f-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6938f-152">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="6938f-152">Minimum supported client</span></span> | <span data-ttu-id="6938f-153">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6938f-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6938f-154">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="6938f-154">Minimum supported server</span></span> | <span data-ttu-id="6938f-155">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6938f-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6938f-156">Header</span><span class="sxs-lookup"><span data-stu-id="6938f-156">Header</span></span> | <span data-ttu-id="6938f-157">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6938f-157">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6938f-158">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="6938f-158">Library</span></span> | <span data-ttu-id="6938f-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="6938f-159">Kernel32.lib</span></span> |
| <span data-ttu-id="6938f-160">DLL</span><span class="sxs-lookup"><span data-stu-id="6938f-160">DLL</span></span> | <span data-ttu-id="6938f-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6938f-161">Kernel32.dll</span></span> |
| <span data-ttu-id="6938f-162">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="6938f-162">Unicode and ANSI names</span></span> | |

## <a name="see-also"></a><span data-ttu-id="6938f-163">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6938f-163">See also</span></span>

[<span data-ttu-id="6938f-164">Konsolen-Bearbeitungssteuerelemente</span><span class="sxs-lookup"><span data-stu-id="6938f-164">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="6938f-165">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="6938f-165">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6938f-166">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="6938f-166">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="6938f-167">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="6938f-167">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="6938f-168">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="6938f-168">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="6938f-169">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="6938f-169">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="6938f-170">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="6938f-170">**SetConsoleMode**</span></span>](setconsolemode.md)
