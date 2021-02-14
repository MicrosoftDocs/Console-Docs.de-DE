---
title: WriteConsole-Funktion
description: Schreibt eine Zeichenfolge in einen Konsolenbildschirm-Puffer, beginnend an der aktuellen Cursorposition.
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
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357610"
---
# <a name="writeconsole-function"></a><span data-ttu-id="1593e-104">WriteConsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="1593e-104">WriteConsole function</span></span>

<span data-ttu-id="1593e-105">Schreibt eine Zeichenfolge in einen Konsolenbildschirm-Puffer, beginnend an der aktuellen Cursorposition.</span><span class="sxs-lookup"><span data-stu-id="1593e-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="1593e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1593e-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="1593e-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1593e-107">Parameters</span></span>

<span data-ttu-id="1593e-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1593e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1593e-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="1593e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1593e-110">Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen.</span><span class="sxs-lookup"><span data-stu-id="1593e-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="1593e-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="1593e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1593e-112">*lpBuffer* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1593e-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="1593e-113">Ein Zeiger auf einen Puffer, der Zeichen enthält, die in den Konsolenbildschirm-Puffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1593e-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="1593e-114">Es wird erwartet, dass es sich um ein Array von `char` für `WriteConsoleA` oder von `wchar_t` für `WriteConsoleW` handelt.</span><span class="sxs-lookup"><span data-stu-id="1593e-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="1593e-115">*nNumberOfCharsToWrite* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1593e-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="1593e-116">Die Anzahl der zu schreibenden Zeichen.</span><span class="sxs-lookup"><span data-stu-id="1593e-116">The number of characters to be written.</span></span> <span data-ttu-id="1593e-117">Wenn die Gesamtgröße der angegebenen Anzahl von Zeichen den verfügbaren Heap überschreitet, schlägt die Funktion mit **ERROR\_NOT\_ENOUGH\_MEMORY** fehl.</span><span class="sxs-lookup"><span data-stu-id="1593e-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="1593e-118">*lpNumberOfCharsWritten* \[out, optional\]</span><span class="sxs-lookup"><span data-stu-id="1593e-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="1593e-119">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="1593e-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="1593e-120">*lpReserved* reserviert; muss **NULL** sein.</span><span class="sxs-lookup"><span data-stu-id="1593e-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="1593e-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1593e-121">Return value</span></span>

<span data-ttu-id="1593e-122">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="1593e-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1593e-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="1593e-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1593e-124">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="1593e-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="1593e-125">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1593e-125">Remarks</span></span>

<span data-ttu-id="1593e-126">Die **WriteConsole**-Funktion schreibt Zeichen an der aktuellen Cursorposition in den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="1593e-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="1593e-127">Die Cursorposition wird mit dem Schreiben von Zeichen vorgerückt.</span><span class="sxs-lookup"><span data-stu-id="1593e-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="1593e-128">Die [**SetConsoleCursorPosition**](setconsolecursorposition.md)-Funktion legt die aktuelle Cursorposition fest.</span><span class="sxs-lookup"><span data-stu-id="1593e-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="1593e-129">Zeichen werden unter Verwendung der Vordergrund- und Hintergrundfarbenattribute geschrieben, die dem Konsolenbildschirm-Puffer zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="1593e-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="1593e-130">Die [**SetConsoleTextAttribute**](setconsoletextattribute.md)-Funktion ändert diese Farben.</span><span class="sxs-lookup"><span data-stu-id="1593e-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="1593e-131">Um die aktuellen Farbattribute und die aktuelle Cursorposition zu bestimmen, verwenden Sie [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="1593e-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="1593e-132">Alle Eingabemodi, die sich auf das Verhalten der [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)-Funktion auswirken, haben denselben Effekt auf **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="1593e-132">All of the input modes that affect the behavior of the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="1593e-133">Zum Abrufen und Festlegen der Ausgabemodi eines Konsolenbildschirm-Puffers verwenden Sie die Funktionen [**GetConsoleMode**](getconsolemode.md) und [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="1593e-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="1593e-134">**WriteConsole** schlägt fehl, wenn sie mit einem Standardhandle verwendet wird, das an eine Datei umgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="1593e-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="1593e-135">Wenn eine Anwendung mehrsprachige Ausgaben verarbeitet, die umgeleitet werden können, stellen Sie fest, ob das Ausgabehandle ein Konsolenhandle ist (eine Methode besteht darin, die [**GetConsoleMode**](getconsolemode.md)-Funktion aufzurufen und zu überprüfen, ob sie erfolgreich ist).</span><span class="sxs-lookup"><span data-stu-id="1593e-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="1593e-136">Wenn das Handle ein Konsolenhandle ist, rufen Sie **WriteConsole** auf.</span><span class="sxs-lookup"><span data-stu-id="1593e-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="1593e-137">Wenn das Handle kein Konsolenhandle ist, wird die Ausgabe umgeleitet, und Sie sollten [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) aufrufen, um die E/A auszuführen.</span><span class="sxs-lookup"><span data-stu-id="1593e-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) to perform the I/O.</span></span> <span data-ttu-id="1593e-138">Stellen Sie sicher, dass Sie eine Unicode-Nur-Text-Datei mit einer Bytereihenfolge-Marke versehen.</span><span class="sxs-lookup"><span data-stu-id="1593e-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="1593e-139">Weitere Informationen finden Sie unter [Verwenden von Bytereihenfolge-Marken](/windows/win32/intl/using-byte-order-marks).</span><span class="sxs-lookup"><span data-stu-id="1593e-139">For more information, see [Using Byte Order Marks](/windows/win32/intl/using-byte-order-marks).</span></span>

<span data-ttu-id="1593e-140">Obwohl eine Anwendung **WriteConsole** im ANSI-Modus verwenden kann, um ANSI-Zeichen zu schreiben, unterstützen Konsolen keine „ANSI-Escapezeichen“ oder „virtuellen Terminal“sequenzen, sofern diese nicht aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="1593e-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="1593e-141">Weitere Informationen, auch zur Anwendbarkeit von Betriebssystemversionen, finden Sie unter [**Virtuelle Konsolenterminalsequenzen**](console-virtual-terminal-sequences.md).</span><span class="sxs-lookup"><span data-stu-id="1593e-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="1593e-142">Wenn virtuelle Terminal-Escapesequenzen nicht aktiviert sind, können Konsolenfunktionen entsprechende Funktionalitäten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1593e-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="1593e-143">Weitere Informationen finden Sie unter [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md)und [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="1593e-143">For more information, see [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1593e-144">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1593e-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1593e-145">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1593e-145">Minimum supported client</span></span> | <span data-ttu-id="1593e-146">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1593e-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1593e-147">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1593e-147">Minimum supported server</span></span> | <span data-ttu-id="1593e-148">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1593e-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1593e-149">Header</span><span class="sxs-lookup"><span data-stu-id="1593e-149">Header</span></span> | <span data-ttu-id="1593e-150">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="1593e-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1593e-151">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1593e-151">Library</span></span> | <span data-ttu-id="1593e-152">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="1593e-152">Kernel32.lib</span></span> |
| <span data-ttu-id="1593e-153">DLL</span><span class="sxs-lookup"><span data-stu-id="1593e-153">DLL</span></span> | <span data-ttu-id="1593e-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1593e-154">Kernel32.dll</span></span> |
| <span data-ttu-id="1593e-155">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="1593e-155">Unicode and ANSI names</span></span> | <span data-ttu-id="1593e-156">**WriteConsoleW** (Unicode) und **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="1593e-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1593e-157">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1593e-157">See also</span></span>

[<span data-ttu-id="1593e-158">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1593e-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1593e-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="1593e-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="1593e-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="1593e-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="1593e-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="1593e-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="1593e-162">Ein- und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="1593e-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="1593e-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="1593e-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="1593e-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="1593e-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="1593e-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="1593e-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="1593e-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="1593e-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="1593e-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="1593e-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="1593e-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="1593e-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="1593e-169">**SetCursorPos**</span><span class="sxs-lookup"><span data-stu-id="1593e-169">**SetCursorPos**</span></span>](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[<span data-ttu-id="1593e-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="1593e-170">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)