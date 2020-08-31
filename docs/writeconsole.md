---
title: Funktion "Beschreib teconsole"
description: Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060479"
---
# <a name="writeconsole-function"></a><span data-ttu-id="65c0b-104">Funktion "Beschreib teconsole"</span><span class="sxs-lookup"><span data-stu-id="65c0b-104">WriteConsole function</span></span>


<span data-ttu-id="65c0b-105">Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition.</span><span class="sxs-lookup"><span data-stu-id="65c0b-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

<a name="syntax"></a><span data-ttu-id="65c0b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="65c0b-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a><span data-ttu-id="65c0b-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="65c0b-107">Parameters</span></span>
----------

<span data-ttu-id="65c0b-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="65c0b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="65c0b-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="65c0b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="65c0b-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="65c0b-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="65c0b-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="65c0b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="65c0b-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="65c0b-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="65c0b-113">Ein Zeiger auf einen Puffer, der Zeichen enthält, die in den Konsolenbildschirm Puffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="65c0b-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="65c0b-114">*nnumofcharstowrite* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="65c0b-114">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="65c0b-115">Die Anzahl der zu schreibenden Zeichen.</span><span class="sxs-lookup"><span data-stu-id="65c0b-115">The number of characters to be written.</span></span> <span data-ttu-id="65c0b-116">Wenn die Gesamtgröße der angegebenen Anzahl von Zeichen den verfügbaren Heap überschreitet, tritt bei der Funktion ein Fehler auf, und es ist \*\* \_ nicht \_ genügend Arbeits \_ Speicher\*\*vorhanden.</span><span class="sxs-lookup"><span data-stu-id="65c0b-116">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="65c0b-117">*lpnumofcharswritten* \[ Out, optional\]</span><span class="sxs-lookup"><span data-stu-id="65c0b-117">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="65c0b-118">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="65c0b-118">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="65c0b-119">*lpReserved* </span><span class="sxs-lookup"><span data-stu-id="65c0b-119">*lpReserved* </span></span>  
<span data-ttu-id="65c0b-120">Bleiben muss **null**sein.</span><span class="sxs-lookup"><span data-stu-id="65c0b-120">Reserved; must be **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="65c0b-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="65c0b-121">Return value</span></span>
------------

<span data-ttu-id="65c0b-122">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="65c0b-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="65c0b-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="65c0b-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="65c0b-124">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="65c0b-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="65c0b-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="65c0b-125">Remarks</span></span>
-------

<span data-ttu-id="65c0b-126">Die Funktion " **Write Console** " schreibt Zeichen an der aktuellen Cursorposition in den Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="65c0b-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="65c0b-127">Die Cursorposition wird beim Schreiben von Zeichen fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="65c0b-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="65c0b-128">Die [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Funktion legt die aktuelle Cursorposition fest.</span><span class="sxs-lookup"><span data-stu-id="65c0b-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="65c0b-129">Zeichen werden mithilfe der Vordergrund-und Hintergrundfarben Attribute geschrieben, die dem Konsolenbildschirm Puffer zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="65c0b-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="65c0b-130">Die [**SetConsoleTextAttribute**](setconsoletextattribute.md) -Funktion ändert diese Farben.</span><span class="sxs-lookup"><span data-stu-id="65c0b-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="65c0b-131">Zum Ermitteln der aktuellen Farb Attribute und der aktuellen Cursorposition verwenden Sie [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="65c0b-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="65c0b-132">Alle Eingabemodi, die das Verhalten der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " beeinflussen, haben dieselbe Auswirkung auf " **Write Console**".</span><span class="sxs-lookup"><span data-stu-id="65c0b-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="65c0b-133">Zum Abrufen und Festlegen der Ausgabe Modi eines Konsolenbildschirm Puffers verwenden Sie die Funktionen [**getconsolemode**](getconsolemode.md) und [**setconsolemode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="65c0b-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="65c0b-134">Die Funktion " **Beschreib teconsole** " verwendet entweder Unicode-Zeichen oder ANSI-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="65c0b-134">The **WriteConsole** function uses either Unicode characters or ANSI characters from the console's current code page.</span></span> <span data-ttu-id="65c0b-135">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="65c0b-135">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="65c0b-136">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="65c0b-136">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="65c0b-137">Die **Schreib Konsole** schlägt fehl, wenn Sie mit einem Standard Handle verwendet wird, das zu einer Datei umgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="65c0b-137">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="65c0b-138">Wenn eine Anwendung mehrsprachige Ausgaben verarbeitet, die umgeleitet werden können, bestimmen Sie, ob das Ausgabe Handle ein Konsolen Handle ist (eine Methode besteht darin, die [**getconsolemode**](getconsolemode.md) -Funktion aufzurufen und zu überprüfen, ob Sie erfolgreich ist).</span><span class="sxs-lookup"><span data-stu-id="65c0b-138">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="65c0b-139">Wenn das Handle ein Konsolen Handle ist, müssen Sie " **Write-Console**" anrufen.</span><span class="sxs-lookup"><span data-stu-id="65c0b-139">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="65c0b-140">Wenn das Handle kein Konsolen Handle ist, wird die Ausgabe umgeleitet, und Sie sollten " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " zum Ausführen des e/a-Vorgangs aufruft.</span><span class="sxs-lookup"><span data-stu-id="65c0b-140">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="65c0b-141">Stellen Sie sicher, dass eine Unicode-nur-Text-Datei mit einer Byte Reihenfolge Markierung versehen wird.</span><span class="sxs-lookup"><span data-stu-id="65c0b-141">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="65c0b-142">Weitere Informationen finden Sie unter [Verwenden von Byte Reihenfolge Markierungen](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="65c0b-142">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="65c0b-143">Obwohl eine Anwendung über die Schreib **Konsole** im ANSI-Modus zum Schreiben von ANSI-Zeichen verwendet werden kann, unterstützen-Konsolen keine ANSI-Escapesequenzen.</span><span class="sxs-lookup"><span data-stu-id="65c0b-143">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support ANSI escape sequences.</span></span> <span data-ttu-id="65c0b-144">Einige Funktionen bieten jedoch äquivalente Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="65c0b-144">However, some functions provide equivalent functionality.</span></span> <span data-ttu-id="65c0b-145">Weitere Informationen finden Sie unter [**setcurrsorpos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)und [**getconsolecursorinfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="65c0b-145">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

<a name="requirements"></a><span data-ttu-id="65c0b-146">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="65c0b-146">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="65c0b-147">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="65c0b-147">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="65c0b-148">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="65c0b-148">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="65c0b-149">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="65c0b-149">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="65c0b-150">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="65c0b-150">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="65c0b-151">Header</span><span class="sxs-lookup"><span data-stu-id="65c0b-151">Header</span></span></p></td>
<td><span data-ttu-id="65c0b-152">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="65c0b-152">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="65c0b-153">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="65c0b-153">Library</span></span></p></td>
<td><span data-ttu-id="65c0b-154">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="65c0b-154">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="65c0b-155">DLL</span><span class="sxs-lookup"><span data-stu-id="65c0b-155">DLL</span></span></p></td>
<td><span data-ttu-id="65c0b-156">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="65c0b-156">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="65c0b-157">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="65c0b-157">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="65c0b-158">" <strong>Schreibconsolew</strong> (Unicode)" und " <strong>Beschreib teconsolea</strong> " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="65c0b-158"><strong>WriteConsoleW</strong> (Unicode) and <strong>WriteConsoleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="65c0b-159"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="65c0b-159"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="65c0b-160">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="65c0b-160">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="65c0b-161">**Getconsolecursorinfo**</span><span class="sxs-lookup"><span data-stu-id="65c0b-161">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="65c0b-162">**Getconsolemode**</span><span class="sxs-lookup"><span data-stu-id="65c0b-162">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="65c0b-163">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="65c0b-163">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="65c0b-164">Eingabe-und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="65c0b-164">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="65c0b-165">**"Read Console"**</span><span class="sxs-lookup"><span data-stu-id="65c0b-165">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="65c0b-166">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="65c0b-166">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="65c0b-167">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="65c0b-167">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="65c0b-168">**Setconsolemode**</span><span class="sxs-lookup"><span data-stu-id="65c0b-168">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="65c0b-169">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="65c0b-169">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="65c0b-170">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="65c0b-170">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="65c0b-171">[**Setcurrsorpos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="65c0b-171">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="65c0b-172">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="65c0b-172">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




