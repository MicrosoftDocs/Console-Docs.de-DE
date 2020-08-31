---
title: Getlargestconsolewindowsize-Funktion
description: Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059690"
---
# <a name="getlargestconsolewindowsize-function"></a><span data-ttu-id="4f0b1-104">Getlargestconsolewindowsize-Funktion</span><span class="sxs-lookup"><span data-stu-id="4f0b1-104">GetLargestConsoleWindowSize function</span></span>


<span data-ttu-id="4f0b1-105">Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.</span><span class="sxs-lookup"><span data-stu-id="4f0b1-105">Retrieves the size of the largest possible console window, based on the current font and the size of the display.</span></span>

<a name="syntax"></a><span data-ttu-id="4f0b1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f0b1-106">Syntax</span></span>
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="4f0b1-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="4f0b1-107">Parameters</span></span>
----------

<span data-ttu-id="4f0b1-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="4f0b1-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4f0b1-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="4f0b1-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="4f0b1-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="4f0b1-110">Return value</span></span>
------------

<span data-ttu-id="4f0b1-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert eine [**coord**](coord-str.md) -Struktur, die die Anzahl der Zeichen Zellen Spalten (**X** -Member) und der Zeilen (**Y** -Member) im größtmöglichen Konsolenfenster angibt.</span><span class="sxs-lookup"><span data-stu-id="4f0b1-111">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns (**X** member) and rows (**Y** member) in the largest possible console window.</span></span> <span data-ttu-id="4f0b1-112">Andernfalls sind die Elemente der-Struktur 0 (null).</span><span class="sxs-lookup"><span data-stu-id="4f0b1-112">Otherwise, the members of the structure are zero.</span></span>

<span data-ttu-id="4f0b1-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4f0b1-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4f0b1-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4f0b1-114">Remarks</span></span>
-------

<span data-ttu-id="4f0b1-115">Die-Funktion berücksichtigt nicht die Größe des Bildschirm Puffers der Konsole. Dies bedeutet, dass die zurückgegebene Fenstergröße möglicherweise größer als die Größe des Konsolenbildschirm Puffers ist.</span><span class="sxs-lookup"><span data-stu-id="4f0b1-115">The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer.</span></span> <span data-ttu-id="4f0b1-116">Mithilfe der [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion kann die maximale Größe des Konsolenfensters anhand der aktuellen Bildschirm Puffergröße, der aktuellen Schriftart und der Anzeige Größe bestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="4f0b1-116">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.</span></span>

<a name="requirements"></a><span data-ttu-id="4f0b1-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4f0b1-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4f0b1-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="4f0b1-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4f0b1-119">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4f0b1-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4f0b1-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="4f0b1-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4f0b1-121">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4f0b1-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4f0b1-122">Header</span><span class="sxs-lookup"><span data-stu-id="4f0b1-122">Header</span></span></p></td>
<td><span data-ttu-id="4f0b1-123">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4f0b1-123">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4f0b1-124">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="4f0b1-124">Library</span></span></p></td>
<td><span data-ttu-id="4f0b1-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4f0b1-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4f0b1-126">DLL</span><span class="sxs-lookup"><span data-stu-id="4f0b1-126">DLL</span></span></p></td>
<td><span data-ttu-id="4f0b1-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4f0b1-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4f0b1-128"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4f0b1-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4f0b1-129">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="4f0b1-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4f0b1-130">**Koord**</span><span class="sxs-lookup"><span data-stu-id="4f0b1-130">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="4f0b1-131">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="4f0b1-131">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="4f0b1-132">**Setconsolewindowinfo**</span><span class="sxs-lookup"><span data-stu-id="4f0b1-132">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="4f0b1-133">Fenster-und Bildschirm Puffergröße</span><span class="sxs-lookup"><span data-stu-id="4f0b1-133">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 




