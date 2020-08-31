---
title: Funktion "Read Console"
description: Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 16287bec8e690e5d70483d6e6055e6badaca40ce
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059578"
---
# <a name="readconsole-function"></a><span data-ttu-id="b290e-104">Funktion "Read Console"</span><span class="sxs-lookup"><span data-stu-id="b290e-104">ReadConsole function</span></span>


<span data-ttu-id="b290e-105">Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.</span><span class="sxs-lookup"><span data-stu-id="b290e-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="b290e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b290e-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

<a name="parameters"></a><span data-ttu-id="b290e-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="b290e-107">Parameters</span></span>
----------

<span data-ttu-id="b290e-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b290e-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="b290e-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="b290e-109">A handle to the console input buffer.</span></span> <span data-ttu-id="b290e-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="b290e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="b290e-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="b290e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b290e-112">*lpBuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="b290e-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="b290e-113">Ein Zeiger auf einen Puffer, der die aus dem Konsolen Eingabepuffer gelesenen Daten empfängt.</span><span class="sxs-lookup"><span data-stu-id="b290e-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="b290e-114">*nnumofcharstoread* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b290e-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="b290e-115">Die Anzahl der zu lesenden Zeichen.</span><span class="sxs-lookup"><span data-stu-id="b290e-115">The number of characters to be read.</span></span> <span data-ttu-id="b290e-116">Die Größe des Puffers, auf den der *lpBuffer* -Parameter verweist, muss mindestens `nNumberOfCharsToRead * sizeof(TCHAR)` Bytes betragen.</span><span class="sxs-lookup"><span data-stu-id="b290e-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="b290e-117">*lpnumofcharsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="b290e-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="b290e-118">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="b290e-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="b290e-119">*pinputcontrol* \[ in, optional\]</span><span class="sxs-lookup"><span data-stu-id="b290e-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="b290e-120">Ein Zeiger auf eine [**Konsolen-einfügekonsolen- \_ \_ Steuer**](console-readconsole-control.md) Elementstruktur, die ein Steuerzeichen angibt, das das Ende des Lesevorgangs signalisiert.</span><span class="sxs-lookup"><span data-stu-id="b290e-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="b290e-121">Dieser Parameter kann **null**sein.</span><span class="sxs-lookup"><span data-stu-id="b290e-121">This parameter can be **NULL**.</span></span>

<span data-ttu-id="b290e-122">Dieser Parameter erfordert standardmäßig Unicode-Eingaben.</span><span class="sxs-lookup"><span data-stu-id="b290e-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="b290e-123">Legen Sie für den ANSI-Modus diesen Parameter auf **null**fest.</span><span class="sxs-lookup"><span data-stu-id="b290e-123">For ANSI mode, set this parameter to **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="b290e-124">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b290e-124">Return value</span></span>
------------

<span data-ttu-id="b290e-125">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="b290e-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b290e-126">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="b290e-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b290e-127">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b290e-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b290e-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b290e-128">Remarks</span></span>
-------

<span data-ttu-id="b290e-129">Die **Lese Konsole** liest Tastatureingaben aus dem Eingabepuffer einer Konsole.</span><span class="sxs-lookup"><span data-stu-id="b290e-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="b290e-130">Sie verhält sich wie die Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ", mit dem Unterschied, dass Sie entweder in Unicode (Wide-Character) oder ANSI-Modus gelesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b290e-130">It behaves like the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="b290e-131">Verwenden Sie die **infoconsole** anstelle von " **Infofile**", damit Anwendungen, die einen einzelnen Satz von Quellen verwalten, mit beiden Modi kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="b290e-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**.</span></span> <span data-ttu-id="b290e-132">Obwohl die **infoconsole** nur mit einem Konsolen Eingabepuffer Handle verwendet werden kann, kann die **Infodatei** mit anderen Handles (z. b. Dateien oder Pipes) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b290e-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="b290e-133">Der Wert von "read **Console** " schlägt fehl, wenn er mit einem Standard Handle verwendet wird, das zu einem anderen als einem Konsolen handle umgeleitet wurde.</span><span class="sxs-lookup"><span data-stu-id="b290e-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="b290e-134">Alle Eingabemodi, die das Verhalten von " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " beeinflussen, haben in der " **infoconsole**" dieselbe Wirkung.</span><span class="sxs-lookup"><span data-stu-id="b290e-134">All of the input modes that affect the behavior of [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) have the same effect on **ReadConsole**.</span></span> <span data-ttu-id="b290e-135">Um die Eingabemodi eines Konsolen Eingabe Puffers abzurufen und festzulegen, verwenden Sie die Funktionen [**getconsolemode**](getconsolemode.md) und [**setconsolemode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="b290e-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="b290e-136">Wenn der Eingabepuffer andere Eingabeereignisse als Tastatur Ereignisse enthält (z. b. Mausereignisse oder Ereignisse zum Ändern von Fenstern), werden diese verworfen.</span><span class="sxs-lookup"><span data-stu-id="b290e-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="b290e-137">Diese Ereignisse können nur mit der Funktion " [**leseconsoleinput**](readconsoleinput.md) " gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="b290e-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

<span data-ttu-id="b290e-138">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="b290e-138">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="b290e-139">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="b290e-139">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="b290e-140">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="b290e-140">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="b290e-141">Der *pinputcontrol* -Parameter kann verwendet werden, um zwischengeschaltete Aufwecken aus dem Lesevorgang in Reaktion auf ein Steuerzeichen zu aktivieren, das in der [\*\* \_ infoconsole- \_ Steuer\*\*](console-readconsole-control.md) Elementstruktur der Konsole angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b290e-141">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="b290e-142">Diese Funktion erfordert, dass Befehls Erweiterungen aktiviert werden, das Standardausgabe Handle als Konsolenausgabe Handle und Eingabe als Unicode.</span><span class="sxs-lookup"><span data-stu-id="b290e-142">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="b290e-143">**Windows Server 2003 und Windows XP/2000:** Das zwischen Lese Feature wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b290e-143">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

<a name="requirements"></a><span data-ttu-id="b290e-144">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b290e-144">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b290e-145">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b290e-145">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b290e-146">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b290e-146">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b290e-147">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b290e-147">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b290e-148">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b290e-148">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b290e-149">Header</span><span class="sxs-lookup"><span data-stu-id="b290e-149">Header</span></span></p></td>
<td><span data-ttu-id="b290e-150">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b290e-150">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b290e-151">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="b290e-151">Library</span></span></p></td>
<td><span data-ttu-id="b290e-152">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b290e-152">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b290e-153">DLL</span><span class="sxs-lookup"><span data-stu-id="b290e-153">DLL</span></span></p></td>
<td><span data-ttu-id="b290e-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b290e-154">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b290e-155">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="b290e-155">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="b290e-156">"Read <strong>consolew</strong> (Unicode)" und "read <strong>Consolea</strong> " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b290e-156"><strong>ReadConsoleW</strong> (Unicode) and <strong>ReadConsoleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b290e-157"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b290e-157"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b290e-158">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b290e-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b290e-159">**Steuerelement für die Konsole der Konsole \_ \_**</span><span class="sxs-lookup"><span data-stu-id="b290e-159">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="b290e-160">**Getconsolemode**</span><span class="sxs-lookup"><span data-stu-id="b290e-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="b290e-161">Eingabe-und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="b290e-161">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="b290e-162">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b290e-162">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="b290e-163">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="b290e-163">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="b290e-164">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="b290e-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b290e-165">**Setconsolemode**</span><span class="sxs-lookup"><span data-stu-id="b290e-165">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="b290e-166">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="b290e-166">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="b290e-167">**Schreib Konsole**</span><span class="sxs-lookup"><span data-stu-id="b290e-167">**WriteConsole**</span></span>](writeconsole.md)

 

 




