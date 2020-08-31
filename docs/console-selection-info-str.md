---
title: CONSOLE_SELECTION_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_SELECTION_INFO Struktur, die Informationen zu einer Konsolen Auswahl enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fe43e7b7cc4b5890284921823aee7b79217b2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060002"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="f257e-104">Konsolen \_ Auswahl \_ Info-Struktur</span><span class="sxs-lookup"><span data-stu-id="f257e-104">CONSOLE\_SELECTION\_INFO structure</span></span>


<span data-ttu-id="f257e-105">Enthält Informationen für eine Konsolen Auswahl.</span><span class="sxs-lookup"><span data-stu-id="f257e-105">Contains information for a console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="f257e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f257e-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

<a name="members"></a><span data-ttu-id="f257e-107">Member</span><span class="sxs-lookup"><span data-stu-id="f257e-107">Members</span></span>
-------

<span data-ttu-id="f257e-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="f257e-108">**dwFlags**</span></span>  
<span data-ttu-id="f257e-109">Der Auswahl Indikator.</span><span class="sxs-lookup"><span data-stu-id="f257e-109">The selection indicator.</span></span> <span data-ttu-id="f257e-110">Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f257e-110">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="f257e-111">Wert</span><span class="sxs-lookup"><span data-stu-id="f257e-111">Value</span></span></th>
<th><span data-ttu-id="f257e-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="f257e-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="f257e-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="f257e-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="f257e-114">Maus ist nicht gedrückt</span><span class="sxs-lookup"><span data-stu-id="f257e-114">Mouse is down</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="f257e-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="f257e-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="f257e-116">Auswählen mit der Maus</span><span class="sxs-lookup"><span data-stu-id="f257e-116">Selecting with the mouse</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="f257e-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span><span class="sxs-lookup"><span data-stu-id="f257e-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span></span></td>
<td><p><span data-ttu-id="f257e-118">Keine Auswahl</span><span class="sxs-lookup"><span data-stu-id="f257e-118">No selection</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="f257e-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="f257e-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="f257e-120">Auswahl wurde begonnen.</span><span class="sxs-lookup"><span data-stu-id="f257e-120">Selection has begun</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="f257e-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="f257e-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="f257e-122">Auswahl Rechteck ist nicht leer.</span><span class="sxs-lookup"><span data-stu-id="f257e-122">Selection rectangle is not empty</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="f257e-123">**dwselectionanchor**</span><span class="sxs-lookup"><span data-stu-id="f257e-123">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="f257e-124">Eine [**Koord**](coord-str.md) -Struktur, die den Auswahl Anker in Zeichen angibt.</span><span class="sxs-lookup"><span data-stu-id="f257e-124">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="f257e-125">**srselection**</span><span class="sxs-lookup"><span data-stu-id="f257e-125">**srSelection**</span></span>  
<span data-ttu-id="f257e-126">Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die das Auswahl Rechteck angibt.</span><span class="sxs-lookup"><span data-stu-id="f257e-126">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

<a name="requirements"></a><span data-ttu-id="f257e-127">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f257e-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f257e-128">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="f257e-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f257e-129">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="f257e-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f257e-130">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="f257e-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f257e-131">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="f257e-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f257e-132">Header</span><span class="sxs-lookup"><span data-stu-id="f257e-132">Header</span></span></p></td>
<td><span data-ttu-id="f257e-133">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f257e-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f257e-134"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f257e-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f257e-135">**Koord**</span><span class="sxs-lookup"><span data-stu-id="f257e-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="f257e-136">**Getconsoleselectioninfo**</span><span class="sxs-lookup"><span data-stu-id="f257e-136">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="f257e-137">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="f257e-137">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




