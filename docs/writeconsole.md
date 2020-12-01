---
title: Funktion "Beschreib teconsole"
description: Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 426aa6711e46e0d5cda1eb1b7dab7b2b0b7156d6
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420289"
---
# <a name="writeconsole-function"></a><span data-ttu-id="4fee2-104">Funktion "Beschreib teconsole"</span><span class="sxs-lookup"><span data-stu-id="4fee2-104">WriteConsole function</span></span>

<span data-ttu-id="4fee2-105">Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition.</span><span class="sxs-lookup"><span data-stu-id="4fee2-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fee2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4fee2-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="4fee2-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="4fee2-107">Parameters</span></span>

<span data-ttu-id="4fee2-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4fee2-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4fee2-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="4fee2-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="4fee2-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="4fee2-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="4fee2-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4fee2-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4fee2-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4fee2-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="4fee2-113">Ein Zeiger auf einen Puffer, der Zeichen enthält, die in den Konsolenbildschirm Puffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4fee2-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="4fee2-114">Es wird davon ausgegangen, dass es sich um ein Array von `char` für `WriteConsoleA` oder handelt `wchar_t` `WriteConsoleW` .</span><span class="sxs-lookup"><span data-stu-id="4fee2-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="4fee2-115">*nnumofcharstowrite* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4fee2-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="4fee2-116">Die Anzahl der zu schreibenden Zeichen.</span><span class="sxs-lookup"><span data-stu-id="4fee2-116">The number of characters to be written.</span></span> <span data-ttu-id="4fee2-117">Wenn die Gesamtgröße der angegebenen Anzahl von Zeichen den verfügbaren Heap überschreitet, tritt bei der Funktion ein Fehler auf, und es ist **\_ nicht \_ genügend Arbeits \_ Speicher** vorhanden.</span><span class="sxs-lookup"><span data-stu-id="4fee2-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="4fee2-118">*lpnumofcharswritten* \[ Out, optional\]</span><span class="sxs-lookup"><span data-stu-id="4fee2-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="4fee2-119">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="4fee2-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="4fee2-120">*lbeibehalten* Bleiben muss **null** sein.</span><span class="sxs-lookup"><span data-stu-id="4fee2-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="4fee2-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="4fee2-121">Return value</span></span>

<span data-ttu-id="4fee2-122">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="4fee2-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4fee2-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="4fee2-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4fee2-124">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4fee2-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4fee2-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4fee2-125">Remarks</span></span>

<span data-ttu-id="4fee2-126">Die Funktion " **Write Console** " schreibt Zeichen an der aktuellen Cursorposition in den Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="4fee2-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="4fee2-127">Die Cursorposition wird beim Schreiben von Zeichen fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="4fee2-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="4fee2-128">Die [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Funktion legt die aktuelle Cursorposition fest.</span><span class="sxs-lookup"><span data-stu-id="4fee2-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="4fee2-129">Zeichen werden mithilfe der Vordergrund-und Hintergrundfarben Attribute geschrieben, die dem Konsolenbildschirm Puffer zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="4fee2-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="4fee2-130">Die [**SetConsoleTextAttribute**](setconsoletextattribute.md) -Funktion ändert diese Farben.</span><span class="sxs-lookup"><span data-stu-id="4fee2-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="4fee2-131">Zum Ermitteln der aktuellen Farb Attribute und der aktuellen Cursorposition verwenden Sie [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="4fee2-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="4fee2-132">Alle Eingabemodi, die das Verhalten der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " beeinflussen, haben dieselbe Auswirkung auf " **Write Console**".</span><span class="sxs-lookup"><span data-stu-id="4fee2-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="4fee2-133">Zum Abrufen und Festlegen der Ausgabe Modi eines Konsolenbildschirm Puffers verwenden Sie die Funktionen [**getconsolemode**](getconsolemode.md) und [**setconsolemode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="4fee2-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="4fee2-134">Die **Schreib Konsole** schlägt fehl, wenn Sie mit einem Standard Handle verwendet wird, das zu einer Datei umgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="4fee2-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="4fee2-135">Wenn eine Anwendung mehrsprachige Ausgaben verarbeitet, die umgeleitet werden können, bestimmen Sie, ob das Ausgabe Handle ein Konsolen Handle ist (eine Methode besteht darin, die [**getconsolemode**](getconsolemode.md) -Funktion aufzurufen und zu überprüfen, ob Sie erfolgreich ist).</span><span class="sxs-lookup"><span data-stu-id="4fee2-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="4fee2-136">Wenn das Handle ein Konsolen Handle ist, müssen Sie " **Write-Console**" anrufen.</span><span class="sxs-lookup"><span data-stu-id="4fee2-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="4fee2-137">Wenn das Handle kein Konsolen Handle ist, wird die Ausgabe umgeleitet, und Sie sollten " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " zum Ausführen des e/a-Vorgangs aufruft.</span><span class="sxs-lookup"><span data-stu-id="4fee2-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="4fee2-138">Stellen Sie sicher, dass eine Unicode-nur-Text-Datei mit einer Byte Reihenfolge Markierung versehen wird.</span><span class="sxs-lookup"><span data-stu-id="4fee2-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="4fee2-139">Weitere Informationen finden Sie unter [Verwenden von Byte Reihenfolge Markierungen](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="4fee2-139">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="4fee2-140">Obwohl eine Anwendung die Schreib **Konsole** im ANSI-Modus zum Schreiben von ANSI-Zeichen verwenden kann, unterstützen-Konsolen keine "ANSI-Escapezeichen" oder "virtuelle Terminal"-Sequenzen, sofern diese nicht aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="4fee2-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="4fee2-141">Weitere Informationen und die Anwendbarkeit der Betriebssystemversion finden Sie unter [**Konsolen-virtuelle Terminal Sequenzen**](console-virtual-terminal-sequences.md) .</span><span class="sxs-lookup"><span data-stu-id="4fee2-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="4fee2-142">Wenn virtuelle Terminal-Escapesequenzen nicht aktiviert sind, können Konsolenfunktionen entsprechende Funktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4fee2-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="4fee2-143">Weitere Informationen finden Sie unter [**setcurrsorpos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)und [**getconsolecursorinfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="4fee2-143">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4fee2-144">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4fee2-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4fee2-145">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="4fee2-145">Minimum supported client</span></span> | <span data-ttu-id="4fee2-146">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="4fee2-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4fee2-147">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="4fee2-147">Minimum supported server</span></span> | <span data-ttu-id="4fee2-148">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="4fee2-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4fee2-149">Header</span><span class="sxs-lookup"><span data-stu-id="4fee2-149">Header</span></span> | <span data-ttu-id="4fee2-150">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4fee2-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4fee2-151">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="4fee2-151">Library</span></span> | <span data-ttu-id="4fee2-152">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4fee2-152">Kernel32.lib</span></span> |
| <span data-ttu-id="4fee2-153">DLL</span><span class="sxs-lookup"><span data-stu-id="4fee2-153">DLL</span></span> | <span data-ttu-id="4fee2-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4fee2-154">Kernel32.dll</span></span> |
| <span data-ttu-id="4fee2-155">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="4fee2-155">Unicode and ANSI names</span></span> | <span data-ttu-id="4fee2-156">" **Schreibconsolew** (Unicode)" und " **Beschreib teconsolea** " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="4fee2-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4fee2-157">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4fee2-157">See also</span></span>

[<span data-ttu-id="4fee2-158">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="4fee2-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4fee2-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="4fee2-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="4fee2-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="4fee2-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="4fee2-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="4fee2-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="4fee2-162">Eingabe-und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="4fee2-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="4fee2-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="4fee2-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="4fee2-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="4fee2-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="4fee2-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="4fee2-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="4fee2-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="4fee2-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="4fee2-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="4fee2-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="4fee2-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="4fee2-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="4fee2-169">[**Setcurrsorpos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="4fee2-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="4fee2-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="4fee2-170">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
