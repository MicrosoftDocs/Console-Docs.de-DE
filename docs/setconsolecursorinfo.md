---
title: Setconsolecursorinfo-Funktion
description: Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 81f16e8c9d9cf90008bbd2e8619c2fa105d04212
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060290"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="78014-104">Setconsolecursorinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="78014-104">SetConsoleCursorInfo function</span></span>


<span data-ttu-id="78014-105">Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="78014-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="78014-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="78014-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="78014-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="78014-107">Parameters</span></span>
----------

<span data-ttu-id="78014-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="78014-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="78014-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="78014-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="78014-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="78014-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="78014-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="78014-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="78014-112">*lpconsolecursorinfo* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="78014-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="78014-113">Ein Zeiger auf eine [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur, die die neuen Spezifikationen für den Cursor des Konsolenbildschirm Puffers bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="78014-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="78014-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="78014-114">Return value</span></span>
------------

<span data-ttu-id="78014-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="78014-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="78014-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="78014-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="78014-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="78014-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="78014-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="78014-118">Remarks</span></span>
-------

<span data-ttu-id="78014-119">Wenn der Cursor eines Bildschirm Puffers sichtbar ist, kann seine Darstellung variieren und reicht von der vollständigen Füllung einer Zeichen Zelle bis zum Anzeigen als horizontale Linie am unteren Rand der Zelle.</span><span class="sxs-lookup"><span data-stu-id="78014-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="78014-120">Der **dwSize** -Member der [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur gibt den Prozentsatz einer Zeichen Zelle an, die vom Cursor ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="78014-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="78014-121">Wenn dieser Member kleiner als 1 oder größer als 100 ist, schlägt **setconsolecursorinfo** fehl.</span><span class="sxs-lookup"><span data-stu-id="78014-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

<a name="requirements"></a><span data-ttu-id="78014-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="78014-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="78014-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="78014-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="78014-124">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="78014-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="78014-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="78014-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="78014-126">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="78014-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="78014-127">Header</span><span class="sxs-lookup"><span data-stu-id="78014-127">Header</span></span></p></td>
<td><span data-ttu-id="78014-128">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="78014-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="78014-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="78014-129">Library</span></span></p></td>
<td><span data-ttu-id="78014-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="78014-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="78014-131">DLL</span><span class="sxs-lookup"><span data-stu-id="78014-131">DLL</span></span></p></td>
<td><span data-ttu-id="78014-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="78014-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="78014-133"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="78014-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="78014-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="78014-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="78014-135">Konsolenbildschirm Puffer</span><span class="sxs-lookup"><span data-stu-id="78014-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="78014-136">**Konsolen \_ Cursor \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="78014-136">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="78014-137">**Getconsolecursorinfo**</span><span class="sxs-lookup"><span data-stu-id="78014-137">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="78014-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="78014-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

 

 




