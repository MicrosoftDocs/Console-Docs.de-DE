---
title: SetConsoleCtrlHandler-Funktion
description: Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt Sie.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: cd7b491c1a395483d4aef052d4147d3edf2514e5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060291"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="1eef0-104">SetConsoleCtrlHandler-Funktion</span><span class="sxs-lookup"><span data-stu-id="1eef0-104">SetConsoleCtrlHandler function</span></span>


<span data-ttu-id="1eef0-105">Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der [**Handlerfunktionen**](handlerroutine.md) für den aufrufenden Prozess hinzu oder entfernt Sie.</span><span class="sxs-lookup"><span data-stu-id="1eef0-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="1eef0-106">Wenn keine Handlerfunktion angegeben wird, legt die Funktion ein Vererb bares Attribut fest, das bestimmt, ob der aufrufende Prozess STRG + C-Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="1eef0-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores CTRL+C signals.</span></span>

<a name="syntax"></a><span data-ttu-id="1eef0-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="1eef0-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

<a name="parameters"></a><span data-ttu-id="1eef0-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="1eef0-108">Parameters</span></span>
----------

<span data-ttu-id="1eef0-109">*Handlerroutine* \[ in, optional\]</span><span class="sxs-lookup"><span data-stu-id="1eef0-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="1eef0-110">Ein Zeiger auf die Anwendungs definierte [**Handlerroutine**](handlerroutine.md) -Funktion, die hinzugefügt oder entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1eef0-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="1eef0-111">Dieser Parameter kann **null**sein.</span><span class="sxs-lookup"><span data-stu-id="1eef0-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="1eef0-112">*Hinzufügen* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1eef0-112">*Add* \[in\]</span></span>  
<span data-ttu-id="1eef0-113">Wenn dieser Parameter **true**ist, wird der Handler hinzugefügt. Wenn der Wert **false**ist, wird der Handler entfernt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="1eef0-114">Wenn der *Handlerroutine* -Parameter **null**ist, bewirkt ein **true** -Wert, dass der Aufrufprozess die Strg + c-Eingabe ignoriert, und ein **false** -Wert stellt die normale Verarbeitung der Strg + c-Eingabe wieder her.</span><span class="sxs-lookup"><span data-stu-id="1eef0-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore CTRL+C input, and a **FALSE** value restores normal processing of CTRL+C input.</span></span> <span data-ttu-id="1eef0-115">Dieses Attribut zum ignorieren oder Verarbeiten von STRG + C wird von untergeordneten Prozessen geerbt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-115">This attribute of ignoring or processing CTRL+C is inherited by child processes.</span></span>

<a name="return-value"></a><span data-ttu-id="1eef0-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1eef0-116">Return value</span></span>
------------

<span data-ttu-id="1eef0-117">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="1eef0-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1eef0-118">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="1eef0-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1eef0-119">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1eef0-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1eef0-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1eef0-120">Remarks</span></span>
-------

<span data-ttu-id="1eef0-121">Diese Funktion bietet eine ähnliche Benachrichtigung für Konsolen Anwendungen und-Dienste, die [**WM \_ queryendsession**](https://msdn.microsoft.com/library/windows/desktop/aa376890) für grafische Anwendungen mit einem nachrichtenpump bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="1eef0-122">Sie können diese Funktion auch aus einer grafischen Anwendung verwenden, aber es gibt keine Garantie, dass Sie vor der Benachrichtigung von **WM \_ queryendsession**eintreffen würde.</span><span class="sxs-lookup"><span data-stu-id="1eef0-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="1eef0-123">Jeder Konsolen Prozess verfügt über eine eigene Liste von Anwendungs definierten [**Handlerroutine**](handlerroutine.md) -Funktionen, die die Signale STRG + C und STRG + UN-Taste verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="1eef0-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle CTRL+C and CTRL+BREAK signals.</span></span> <span data-ttu-id="1eef0-124">Die Handlerfunktionen behandeln auch Signale, die vom System generiert werden, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="1eef0-125">Anfänglich enthält die Handlerliste für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="1eef0-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="1eef0-126">Bei einem Konsolen Prozess werden zusätzliche Handlerfunktionen durch Aufrufen der **SetConsoleCtrlHandler** -Funktion hinzugefügt oder entfernt, die sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="1eef0-127">Wenn ein Konsolen Prozess eines der Steuersignale empfängt, werden seine Handlerfunktionen für eine zuletzt registrierte, erste aufrufende Basis aufgerufen, bis einer der Handler "true" zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns TRUE.</span></span> <span data-ttu-id="1eef0-128">Wenn keiner der Handler true zurückgibt, wird der Standard Handler aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="1eef0-128">If none of the handlers returns TRUE, the default handler is called.</span></span>

<span data-ttu-id="1eef0-129">Bei Konsolen Prozessen werden die Tastenkombinationen STRG + C und STRG + Unterbrechung normalerweise als Signale behandelt (**STRG \_ C- \_ Ereignis** und **STRG-Break- \_ \_ Ereignis**).</span><span class="sxs-lookup"><span data-stu-id="1eef0-129">For console processes, the CTRL+C and CTRL+BREAK key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="1eef0-130">Wenn ein Konsolenfenster mit dem Tastaturfokus STRG + C oder STRG + UNTBR erhält, wird das Signal in der Regel an alle Prozesse weitergegeben, die die Konsole freigeben.</span><span class="sxs-lookup"><span data-stu-id="1eef0-130">When a console window with the keyboard focus receives CTRL+C or CTRL+BREAK, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="1eef0-131">STRG + UNTBR wird immer als Signal behandelt, aber das typische STRG + C-Verhalten kann auf drei Arten geändert werden, die verhindern, dass die Handlerfunktionen aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="1eef0-131">CTRL+BREAK is always treated as a signal, but typical CTRL+C behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="1eef0-132">Die [**setconsolemode**](setconsolemode.md) -Funktion kann den aktivierte \*\* \_ \_ Eingabe\*\* Modus für den Eingabepuffer einer Konsole deaktivieren, sodass STRG + C als Tastatureingabe und nicht als Signal gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="1eef0-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="1eef0-133">Der Aufruf von **SetConsoleCtrlHandler** mit den Argumenten **null** und **true** bewirkt, dass der aufrufende Prozess STRG + C-Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="1eef0-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="1eef0-134">Dieses Attribut wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="1eef0-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="1eef0-135">Wenn ein Konsolen Prozess gedebuggt wird und STRG + C-Signale nicht deaktiviert wurden, generiert das System eine **dbg- \_ Steuerungs- \_ C** -Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="1eef0-135">If a console process is being debugged and CTRL+C signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="1eef0-136">Diese Ausnahme wird nur für den Vorteil des Debuggers ausgelöst, und eine Anwendung sollte niemals einen Ausnahmehandler verwenden, um Sie zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="1eef0-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="1eef0-137">Wenn der Debugger die Ausnahme behandelt, wird die Tastenkombination STRG + C von der Anwendung nicht bemerkt, mit einer Ausnahme: mindestwarnzeit-warte Vorgänge werden beendet.</span><span class="sxs-lookup"><span data-stu-id="1eef0-137">If the debugger handles the exception, an application will not notice the CTRL+C, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="1eef0-138">Wenn der Debugger die Ausnahme bei nicht behandelten übergibt, wird STRG + C an den Konsolen Prozess weitergeleitet und als Signal behandelt, wie bereits erläutert.</span><span class="sxs-lookup"><span data-stu-id="1eef0-138">If the debugger passes the exception on unhandled, CTRL+C is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="1eef0-139">Ein Konsolen Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um das Signal STRG + C oder STRG + UNTBR an eine Konsolen Prozessgruppe zu senden.</span><span class="sxs-lookup"><span data-stu-id="1eef0-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to a console process group.</span></span>

<span data-ttu-id="1eef0-140">Das System generiert das STRG-Schließ \*\* \_ \_ Ereignis**, das STRG-Abmelde \*\* \_ \_ Ereignis**und das **STRG-Shutdown- \_ \_ Ereignis** Signal, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt, sodass der Prozess vor dem beenden eine Bereinigung durchführt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="1eef0-141">Konsolenfunktionen oder alle C-Lauf Zeitfunktionen, die Konsolenfunktionen aufzurufen, funktionieren möglicherweise nicht zuverlässig während der Verarbeitung der drei Signale, die zuvor erwähnt wurden.</span><span class="sxs-lookup"><span data-stu-id="1eef0-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="1eef0-142">Der Grund hierfür ist, dass möglicherweise einige oder alle der internen Konsolen Bereinigungs Routinen aufgerufen wurden, bevor der Prozess Signalhandler ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="1eef0-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="1eef0-143">**Windows 7, Windows 8, Windows 8.1 und Windows 10:**</span><span class="sxs-lookup"><span data-stu-id="1eef0-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="1eef0-144">Wenn eine Konsolenanwendung die gdi32.dll oder user32.dll Bibliothek lädt, wird die [**Handlerroutine**](handlerroutine.md) -Funktion, die Sie beim Aufrufen von **SetConsoleCtrlHandler** angeben, nicht für das STRG-Abmelde \*\* \_ \_ Ereignis\*\* und **STRG-Shutdown- \_ \_ Ereignis** Ereignisse aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="1eef0-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="1eef0-145">Das Betriebssystem erkennt Prozesse, die gdi32.dll oder user32.dll als Windows-Anwendungen und nicht als Konsolen Anwendungen laden.</span><span class="sxs-lookup"><span data-stu-id="1eef0-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="1eef0-146">Dieses Verhalten tritt auch bei Konsolen Anwendungen auf, die keine Funktionen in gdi32.dll oder user32.dll direkt aufzurufen, aber Funktionen wie [Shellfunktionen](https://msdn.microsoft.com/library/windows/desktop/bb776426) aufzurufen, die wiederum Funktionen in gdi32.dll oder user32.dll aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="1eef0-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](https://msdn.microsoft.com/library/windows/desktop/bb776426) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="1eef0-147">Um Ereignisse zu empfangen, wenn ein Benutzer sich abmeldet oder das Gerät unter diesen Umständen heruntergefahren wird, erstellen Sie ein ausgeblendetes Fenster in der Konsolenanwendung, und behandeln Sie dann die Nachrichten des WM-Fensters [\*\* \_ queryendsession\*\*](https://msdn.microsoft.com/library/windows/desktop/aa376890) und [**WM \_ EndSession**](https://msdn.microsoft.com/library/windows/desktop/aa376889) , die das verborgene Fenster empfängt.</span><span class="sxs-lookup"><span data-stu-id="1eef0-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) and [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) window messages that the hidden window receives.</span></span> <span data-ttu-id="1eef0-148">Sie können ein verborgenes Fenster erstellen, indem Sie die [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) -Methode aufrufen, wobei der *dwExStyle* -Parameter auf 0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1eef0-148">You can create a hidden window by calling the [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) method with the *dwExStyle* parameter set to 0.</span></span>

<a name="examples"></a><span data-ttu-id="1eef0-149">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1eef0-149">Examples</span></span>
--------

<span data-ttu-id="1eef0-150">Ein Beispiel finden Sie unter [Registrieren einer Steuerelement Handler-Funktion](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="1eef0-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

<a name="requirements"></a><span data-ttu-id="1eef0-151">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1eef0-151">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1eef0-152">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1eef0-152">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1eef0-153">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="1eef0-153">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1eef0-154">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1eef0-154">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1eef0-155">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="1eef0-155">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1eef0-156">Header</span><span class="sxs-lookup"><span data-stu-id="1eef0-156">Header</span></span></p></td>
<td><span data-ttu-id="1eef0-157">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1eef0-157">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1eef0-158">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1eef0-158">Library</span></span></p></td>
<td><span data-ttu-id="1eef0-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1eef0-159">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1eef0-160">DLL</span><span class="sxs-lookup"><span data-stu-id="1eef0-160">DLL</span></span></p></td>
<td><span data-ttu-id="1eef0-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1eef0-161">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1eef0-162"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1eef0-162"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1eef0-163">Konsolen Steuerungs Handler</span><span class="sxs-lookup"><span data-stu-id="1eef0-163">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="1eef0-164">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1eef0-164">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1eef0-165">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="1eef0-165">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="1eef0-166">**Generateconsolectrlevent**</span><span class="sxs-lookup"><span data-stu-id="1eef0-166">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="1eef0-167">**Getconsolemode**</span><span class="sxs-lookup"><span data-stu-id="1eef0-167">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="1eef0-168">**Handlerroutine**</span><span class="sxs-lookup"><span data-stu-id="1eef0-168">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="1eef0-169">**Setconsolemode**</span><span class="sxs-lookup"><span data-stu-id="1eef0-169">**SetConsoleMode**</span></span>](setconsolemode.md)

 

 




