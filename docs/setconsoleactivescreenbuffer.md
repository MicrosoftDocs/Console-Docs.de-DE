---
title: Setconsoleactiveskreenbuffer-Funktion
description: Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f3fa9d79705c95fc0737597886b5562ce1045c45
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060299"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="c26c6-104">Setconsoleactiveskreenbuffer-Funktion</span><span class="sxs-lookup"><span data-stu-id="c26c6-104">SetConsoleActiveScreenBuffer function</span></span>


<span data-ttu-id="c26c6-105">Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="c26c6-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="c26c6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c26c6-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="c26c6-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c26c6-107">Parameters</span></span>
----------

<span data-ttu-id="c26c6-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c26c6-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c26c6-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="c26c6-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="c26c6-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c26c6-110">Return value</span></span>
------------

<span data-ttu-id="c26c6-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="c26c6-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c26c6-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="c26c6-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c26c6-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c26c6-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="c26c6-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c26c6-114">Remarks</span></span>
-------

<span data-ttu-id="c26c6-115">Eine Konsole kann über mehrere Bildschirm Puffer verfügen.</span><span class="sxs-lookup"><span data-stu-id="c26c6-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="c26c6-116">**Setconsoleactiveskreenbuffer** bestimmt, welche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c26c6-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="c26c6-117">Sie können in einen inaktiven Bildschirm Puffer schreiben und dann **setconsoleactiveskreenbuffer** verwenden, um den Inhalt des Puffers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c26c6-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

<a name="examples"></a><span data-ttu-id="c26c6-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c26c6-118">Examples</span></span>
--------

<span data-ttu-id="c26c6-119">Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c26c6-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="c26c6-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c26c6-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c26c6-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c26c6-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c26c6-122">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c26c6-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c26c6-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c26c6-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c26c6-124">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c26c6-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c26c6-125">Header</span><span class="sxs-lookup"><span data-stu-id="c26c6-125">Header</span></span></p></td>
<td><span data-ttu-id="c26c6-126">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c26c6-126">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c26c6-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c26c6-127">Library</span></span></p></td>
<td><span data-ttu-id="c26c6-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c26c6-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c26c6-129">DLL</span><span class="sxs-lookup"><span data-stu-id="c26c6-129">DLL</span></span></p></td>
<td><span data-ttu-id="c26c6-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c26c6-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c26c6-131"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c26c6-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c26c6-132">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="c26c6-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c26c6-133">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="c26c6-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="c26c6-134">**"Kreateconsoleskreenbuffer"**</span><span class="sxs-lookup"><span data-stu-id="c26c6-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)

 

 




