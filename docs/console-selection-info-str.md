---
title: CONSOLE_SELECTION_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_SELECTION_INFO Struktur, die Informationen zu einer Konsolen Auswahl enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038368"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="5071b-104">Konsolen \_ Auswahl \_ Info-Struktur</span><span class="sxs-lookup"><span data-stu-id="5071b-104">CONSOLE\_SELECTION\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5071b-105">Enthält Informationen für eine Konsolen Auswahl.</span><span class="sxs-lookup"><span data-stu-id="5071b-105">Contains information for a console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="5071b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5071b-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a><span data-ttu-id="5071b-107">Member</span><span class="sxs-lookup"><span data-stu-id="5071b-107">Members</span></span>

<span data-ttu-id="5071b-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="5071b-108">**dwFlags**</span></span>  
<span data-ttu-id="5071b-109">Der Auswahl Indikator.</span><span class="sxs-lookup"><span data-stu-id="5071b-109">The selection indicator.</span></span> <span data-ttu-id="5071b-110">Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="5071b-110">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="5071b-111">Wert</span><span class="sxs-lookup"><span data-stu-id="5071b-111">Value</span></span> | <span data-ttu-id="5071b-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="5071b-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="5071b-113">**CONSOLE_MOUSE_DOWN** 0x0008</span><span class="sxs-lookup"><span data-stu-id="5071b-113">**CONSOLE_MOUSE_DOWN** 0x0008</span></span> | <span data-ttu-id="5071b-114">Die Maus ist nicht gedrückt.</span><span class="sxs-lookup"><span data-stu-id="5071b-114">Mouse is down.</span></span> <span data-ttu-id="5071b-115">Der Benutzer passt das Auswahl Rechteck aktiv mit der Maus an.</span><span class="sxs-lookup"><span data-stu-id="5071b-115">The user is actively adjusting the selection rectangle with a mouse.</span></span> |
| <span data-ttu-id="5071b-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span><span class="sxs-lookup"><span data-stu-id="5071b-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span></span> | <span data-ttu-id="5071b-117">Auswählen mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="5071b-117">Selecting with the mouse.</span></span> <span data-ttu-id="5071b-118">Wenn OFF, wird der Benutzer im Betriebs `conhost.exe` markermodus mit der Tastatur ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="5071b-118">If off, the user is operating `conhost.exe` mark mode selection with the keyboard.</span></span> |
| <span data-ttu-id="5071b-119">**CONSOLE_NO_SELECTION** 0x0000</span><span class="sxs-lookup"><span data-stu-id="5071b-119">**CONSOLE_NO_SELECTION** 0x0000</span></span> | <span data-ttu-id="5071b-120">Keine Auswahl.</span><span class="sxs-lookup"><span data-stu-id="5071b-120">No selection.</span></span> |
| <span data-ttu-id="5071b-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span><span class="sxs-lookup"><span data-stu-id="5071b-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span></span> | <span data-ttu-id="5071b-122">Die Auswahl wurde begonnen.</span><span class="sxs-lookup"><span data-stu-id="5071b-122">Selection has begun.</span></span> <span data-ttu-id="5071b-123">Bei einer Maus Auswahl tritt dies in der Regel nicht ohne das- `CONSOLE_SELECTION_NOT_EMPTY` Flag auf.</span><span class="sxs-lookup"><span data-stu-id="5071b-123">If a mouse selection, this will typically not occur without the `CONSOLE_SELECTION_NOT_EMPTY` flag.</span></span> <span data-ttu-id="5071b-124">Bei einer Tastaturauswahl kann dies vorkommen, wenn der Markierungs Modus eingegeben wurde, der Benutzer aber immer noch zur ursprünglichen Position navigiert.</span><span class="sxs-lookup"><span data-stu-id="5071b-124">If a keyboard selection, this may occur when mark mode has been entered but the user is still navigating to the initial position.</span></span> |
| <span data-ttu-id="5071b-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span><span class="sxs-lookup"><span data-stu-id="5071b-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span></span> | <span data-ttu-id="5071b-126">Auswahl Rechteck ist nicht leer.</span><span class="sxs-lookup"><span data-stu-id="5071b-126">Selection rectangle not empty.</span></span> <span data-ttu-id="5071b-127">Die Nutzlast von *dwselectionanchor* und *srselection* ist gültig.</span><span class="sxs-lookup"><span data-stu-id="5071b-127">The payload of *dwSelectionAnchor* and *srSelection* are valid.</span></span>  |

<span data-ttu-id="5071b-128">**dwselectionanchor**</span><span class="sxs-lookup"><span data-stu-id="5071b-128">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="5071b-129">Eine [**Koord**](coord-str.md) -Struktur, die den Auswahl Anker in Zeichen angibt.</span><span class="sxs-lookup"><span data-stu-id="5071b-129">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="5071b-130">**srselection**</span><span class="sxs-lookup"><span data-stu-id="5071b-130">**srSelection**</span></span>  
<span data-ttu-id="5071b-131">Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die das Auswahl Rechteck angibt.</span><span class="sxs-lookup"><span data-stu-id="5071b-131">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

## <a name="requirements"></a><span data-ttu-id="5071b-132">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="5071b-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5071b-133">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="5071b-133">Minimum supported client</span></span> | <span data-ttu-id="5071b-134">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5071b-134">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="5071b-135">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="5071b-135">Minimum supported server</span></span> | <span data-ttu-id="5071b-136">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5071b-136">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="5071b-137">Header</span><span class="sxs-lookup"><span data-stu-id="5071b-137">Header</span></span> | <span data-ttu-id="5071b-138">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5071b-138">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="5071b-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5071b-139">See also</span></span>

[<span data-ttu-id="5071b-140">**Koord**</span><span class="sxs-lookup"><span data-stu-id="5071b-140">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="5071b-141">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="5071b-141">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="5071b-142">**kleine \_ Rect**</span><span class="sxs-lookup"><span data-stu-id="5071b-142">**SMALL\_RECT**</span></span>](small-rect-str.md)
