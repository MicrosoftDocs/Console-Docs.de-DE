---
title: Funktion "Read Console"
description: Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: f38994156a8c8e58c952a2ffc3d5d9531ec027e7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037768"
---
# <a name="readconsole-function"></a><span data-ttu-id="28f26-104">Funktion "Read Console"</span><span class="sxs-lookup"><span data-stu-id="28f26-104">ReadConsole function</span></span>

<span data-ttu-id="28f26-105">Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.</span><span class="sxs-lookup"><span data-stu-id="28f26-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="28f26-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="28f26-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a><span data-ttu-id="28f26-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="28f26-107">Parameters</span></span>

<span data-ttu-id="28f26-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="28f26-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="28f26-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="28f26-109">A handle to the console input buffer.</span></span> <span data-ttu-id="28f26-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="28f26-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="28f26-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="28f26-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="28f26-112">*lpBuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="28f26-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="28f26-113">Ein Zeiger auf einen Puffer, der die aus dem Konsolen Eingabepuffer gelesenen Daten empfängt.</span><span class="sxs-lookup"><span data-stu-id="28f26-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="28f26-114">*nnumofcharstoread* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="28f26-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="28f26-115">Die Anzahl der zu lesenden Zeichen.</span><span class="sxs-lookup"><span data-stu-id="28f26-115">The number of characters to be read.</span></span> <span data-ttu-id="28f26-116">Die Größe des Puffers, auf den der *lpBuffer* -Parameter verweist, muss mindestens `nNumberOfCharsToRead * sizeof(TCHAR)` Bytes betragen.</span><span class="sxs-lookup"><span data-stu-id="28f26-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="28f26-117">*lpnumofcharsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="28f26-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="28f26-118">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="28f26-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="28f26-119">*pinputcontrol* \[ in, optional\]</span><span class="sxs-lookup"><span data-stu-id="28f26-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="28f26-120">Ein Zeiger auf eine [**Konsolen-einfügekonsolen- \_ \_ Steuer**](console-readconsole-control.md) Elementstruktur, die ein Steuerzeichen angibt, das das Ende des Lesevorgangs signalisiert.</span><span class="sxs-lookup"><span data-stu-id="28f26-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="28f26-121">Dieser Parameter kann **null** sein.</span><span class="sxs-lookup"><span data-stu-id="28f26-121">This parameter can be **NULL** .</span></span>

<span data-ttu-id="28f26-122">Dieser Parameter erfordert standardmäßig Unicode-Eingaben.</span><span class="sxs-lookup"><span data-stu-id="28f26-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="28f26-123">Legen Sie für den ANSI-Modus diesen Parameter auf **null** fest.</span><span class="sxs-lookup"><span data-stu-id="28f26-123">For ANSI mode, set this parameter to **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="28f26-124">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="28f26-124">Return value</span></span>

<span data-ttu-id="28f26-125">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="28f26-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="28f26-126">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="28f26-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="28f26-127">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="28f26-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="28f26-128">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="28f26-128">Remarks</span></span>

<span data-ttu-id="28f26-129">Die **Lese Konsole** liest Tastatureingaben aus dem Eingabepuffer einer Konsole.</span><span class="sxs-lookup"><span data-stu-id="28f26-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="28f26-130">Sie verhält sich wie die Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ", mit dem Unterschied, dass Sie entweder in Unicode (Wide-Character) oder ANSI-Modus gelesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="28f26-130">It behaves like the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="28f26-131">Verwenden Sie die **infoconsole** anstelle von " **Infofile** ", damit Anwendungen, die einen einzelnen Satz von Quellen verwalten, mit beiden Modi kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="28f26-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile** .</span></span> <span data-ttu-id="28f26-132">Obwohl die **infoconsole** nur mit einem Konsolen Eingabepuffer Handle verwendet werden kann, kann die **Infodatei** mit anderen Handles (z. b. Dateien oder Pipes) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="28f26-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="28f26-133">Der Wert von "read **Console** " schlägt fehl, wenn er mit einem Standard Handle verwendet wird, das zu einem anderen als einem Konsolen handle umgeleitet wurde.</span><span class="sxs-lookup"><span data-stu-id="28f26-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="28f26-134">Alle Eingabemodi, die das Verhalten von " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " beeinflussen, haben in der " **infoconsole** " dieselbe Wirkung.</span><span class="sxs-lookup"><span data-stu-id="28f26-134">All of the input modes that affect the behavior of [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) have the same effect on **ReadConsole** .</span></span> <span data-ttu-id="28f26-135">Um die Eingabemodi eines Konsolen Eingabe Puffers abzurufen und festzulegen, verwenden Sie die Funktionen [**getconsolemode**](getconsolemode.md) und [**setconsolemode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="28f26-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="28f26-136">Wenn der Eingabepuffer andere Eingabeereignisse als Tastatur Ereignisse enthält (z. b. Mausereignisse oder Ereignisse zum Ändern von Fenstern), werden diese verworfen.</span><span class="sxs-lookup"><span data-stu-id="28f26-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="28f26-137">Diese Ereignisse können nur mit der Funktion " [**leseconsoleinput**](readconsoleinput.md) " gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="28f26-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="28f26-138">Der *pinputcontrol* -Parameter kann verwendet werden, um zwischengeschaltete Aufwecken aus dem Lesevorgang in Reaktion auf ein Steuerzeichen zu aktivieren, das in der [**\_ infoconsole- \_ Steuer**](console-readconsole-control.md) Elementstruktur der Konsole angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="28f26-138">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="28f26-139">Diese Funktion erfordert, dass Befehls Erweiterungen aktiviert werden, das Standardausgabe Handle als Konsolenausgabe Handle und Eingabe als Unicode.</span><span class="sxs-lookup"><span data-stu-id="28f26-139">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="28f26-140">**Windows Server 2003 und Windows XP/2000:** Das zwischen Lese Feature wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="28f26-140">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

## <a name="requirements"></a><span data-ttu-id="28f26-141">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="28f26-141">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="28f26-142">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="28f26-142">Minimum supported client</span></span> | <span data-ttu-id="28f26-143">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="28f26-143">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="28f26-144">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="28f26-144">Minimum supported server</span></span> | <span data-ttu-id="28f26-145">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="28f26-145">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="28f26-146">Header</span><span class="sxs-lookup"><span data-stu-id="28f26-146">Header</span></span> | <span data-ttu-id="28f26-147">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="28f26-147">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="28f26-148">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="28f26-148">Library</span></span> | <span data-ttu-id="28f26-149">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="28f26-149">Kernel32.lib</span></span> |
| <span data-ttu-id="28f26-150">DLL</span><span class="sxs-lookup"><span data-stu-id="28f26-150">DLL</span></span> | <span data-ttu-id="28f26-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="28f26-151">Kernel32.dll</span></span> |
| <span data-ttu-id="28f26-152">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="28f26-152">Unicode and ANSI names</span></span> | <span data-ttu-id="28f26-153">"Read **consolew** (Unicode)" und "read **Consolea** " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="28f26-153">**ReadConsoleW** (Unicode) and **ReadConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="28f26-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="28f26-154">See also</span></span>

[<span data-ttu-id="28f26-155">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="28f26-155">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="28f26-156">**Steuerelement für die Konsole der Konsole \_ \_**</span><span class="sxs-lookup"><span data-stu-id="28f26-156">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="28f26-157">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="28f26-157">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="28f26-158">Eingabe-und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="28f26-158">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="28f26-159">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="28f26-159">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="28f26-160">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="28f26-160">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="28f26-161">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="28f26-161">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="28f26-162">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="28f26-162">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="28f26-163">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="28f26-163">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="28f26-164">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="28f26-164">**WriteConsole**</span></span>](writeconsole.md)
