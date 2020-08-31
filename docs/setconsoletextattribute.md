---
title: SetConsoleTextAttribute-Funktion
description: Legt die Attribute der Zeichen fest, die von der Funktion "Write file" oder der Funktion "Write-Console" auf den Konsolenbildschirm Puffer geschrieben wurden, oder von der Funktion "Read File" oder "Read Console"
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 2242466e4255b0d92c9bb1d1eac5431b59346e7b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060508"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="96359-104">SetConsoleTextAttribute-Funktion</span><span class="sxs-lookup"><span data-stu-id="96359-104">SetConsoleTextAttribute function</span></span>


<span data-ttu-id="96359-105">Legt die Attribute der Zeichen fest, die von der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder der Funktion " [**Write-Console**](writeconsole.md) " auf den Konsolenbildschirm Puffer geschrieben wurden, oder von der Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) "</span><span class="sxs-lookup"><span data-stu-id="96359-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="96359-106">Diese Funktion wirkt sich auf Text aus, der nach dem Funktions aufzurufen</span><span class="sxs-lookup"><span data-stu-id="96359-106">This function affects text written after the function call.</span></span>

<a name="syntax"></a><span data-ttu-id="96359-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="96359-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

<a name="parameters"></a><span data-ttu-id="96359-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="96359-108">Parameters</span></span>
----------

<span data-ttu-id="96359-109">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="96359-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="96359-110">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="96359-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="96359-111">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="96359-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="96359-112">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="96359-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="96359-113">*wattributes* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="96359-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="96359-114">Die [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="96359-114">The [character attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<a name="return-value"></a><span data-ttu-id="96359-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="96359-115">Return value</span></span>
------------

<span data-ttu-id="96359-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="96359-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="96359-117">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="96359-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="96359-118">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="96359-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="96359-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="96359-119">Remarks</span></span>
-------

<span data-ttu-id="96359-120">Um die aktuellen Farb Attribute eines Bildschirm Puffers zu bestimmen, müssen Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="96359-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="96359-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="96359-121">Examples</span></span>
--------

<span data-ttu-id="96359-122">Ein Beispiel finden Sie unter [Verwenden der übergeordneten Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="96359-122">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="96359-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="96359-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="96359-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="96359-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="96359-125">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="96359-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96359-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="96359-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="96359-127">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="96359-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96359-128">Header</span><span class="sxs-lookup"><span data-stu-id="96359-128">Header</span></span></p></td>
<td><span data-ttu-id="96359-129">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="96359-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96359-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="96359-130">Library</span></span></p></td>
<td><span data-ttu-id="96359-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="96359-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96359-132">DLL</span><span class="sxs-lookup"><span data-stu-id="96359-132">DLL</span></span></p></td>
<td><span data-ttu-id="96359-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="96359-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="96359-134"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="96359-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="96359-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="96359-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="96359-136">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="96359-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="96359-137">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="96359-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="96359-138">**"Read Console"**</span><span class="sxs-lookup"><span data-stu-id="96359-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="96359-139">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="96359-139">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="96359-140">**Schreib Konsole**</span><span class="sxs-lookup"><span data-stu-id="96359-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="96359-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="96359-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




