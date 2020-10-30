---
title: COORD-Struktur
description: Definiert die Koordinaten einer Zeichen Zelle in einem Konsolenbildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c8e6f87c3a2730a8af21b9bc064c71900fb82f5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038308"
---
# <a name="coord-structure"></a><span data-ttu-id="cb6f7-104">COORD-Struktur</span><span class="sxs-lookup"><span data-stu-id="cb6f7-104">COORD structure</span></span>

<span data-ttu-id="cb6f7-105">Definiert die Koordinaten einer Zeichen Zelle in einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="cb6f7-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="cb6f7-106">Der Ursprung des Koordinatensystems (0,0) befindet sich in der oberen, linken Zelle des Puffers.</span><span class="sxs-lookup"><span data-stu-id="cb6f7-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb6f7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb6f7-107">Syntax</span></span>

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

## <a name="members"></a><span data-ttu-id="cb6f7-108">Member</span><span class="sxs-lookup"><span data-stu-id="cb6f7-108">Members</span></span>

<span data-ttu-id="cb6f7-109">**X**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-109">**X**</span></span>  
<span data-ttu-id="cb6f7-110">Der horizontale Koordinaten-oder Spaltenwert.</span><span class="sxs-lookup"><span data-stu-id="cb6f7-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="cb6f7-111">Die Einheiten sind vom Funktions aufrufsbefehl abhängig.</span><span class="sxs-lookup"><span data-stu-id="cb6f7-111">The units depend on the function call.</span></span>

<span data-ttu-id="cb6f7-112">**J**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-112">**Y**</span></span>  
<span data-ttu-id="cb6f7-113">Der vertikale Koordinaten-oder Zeilen Wert.</span><span class="sxs-lookup"><span data-stu-id="cb6f7-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="cb6f7-114">Die Einheiten sind vom Funktions aufrufsbefehl abhängig.</span><span class="sxs-lookup"><span data-stu-id="cb6f7-114">The units depend on the function call.</span></span>

## <a name="examples"></a><span data-ttu-id="cb6f7-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="cb6f7-115">Examples</span></span>

<span data-ttu-id="cb6f7-116">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="cb6f7-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="cb6f7-117">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="cb6f7-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cb6f7-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="cb6f7-118">Minimum supported client</span></span> | <span data-ttu-id="cb6f7-119">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="cb6f7-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="cb6f7-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="cb6f7-120">Minimum supported server</span></span> | <span data-ttu-id="cb6f7-121">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="cb6f7-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="cb6f7-122">Header</span><span class="sxs-lookup"><span data-stu-id="cb6f7-122">Header</span></span> | <span data-ttu-id="cb6f7-123">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cb6f7-123">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="cb6f7-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cb6f7-124">See also</span></span>

[<span data-ttu-id="cb6f7-125">**Informationen zur Konsolen \_ Schriftart \_**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="cb6f7-126">**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="cb6f7-127">**Konsolen \_ Auswahl \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="cb6f7-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="cb6f7-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="cb6f7-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="cb6f7-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="cb6f7-132">**\_Ereignis \_ Daten Satz für Maus**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="cb6f7-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="cb6f7-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="cb6f7-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="cb6f7-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="cb6f7-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="cb6f7-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="cb6f7-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="cb6f7-140">**Datensatz der Fenster \_ Puffer \_ Größe \_**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="cb6f7-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="cb6f7-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="cb6f7-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="cb6f7-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
