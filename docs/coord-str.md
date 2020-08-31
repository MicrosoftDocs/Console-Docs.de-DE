---
title: Coord-Struktur
description: Definiert die Koordinaten einer Zeichen Zelle in einem Konsolenbildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059939"
---
# <a name="coord-structure"></a><span data-ttu-id="725cb-104">Coord-Struktur</span><span class="sxs-lookup"><span data-stu-id="725cb-104">COORD structure</span></span>


<span data-ttu-id="725cb-105">Definiert die Koordinaten einer Zeichen Zelle in einem Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="725cb-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="725cb-106">Der Ursprung des Koordinatensystems (0,0) befindet sich in der oberen, linken Zelle des Puffers.</span><span class="sxs-lookup"><span data-stu-id="725cb-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="725cb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="725cb-107">Syntax</span></span>
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a><span data-ttu-id="725cb-108">Member</span><span class="sxs-lookup"><span data-stu-id="725cb-108">Members</span></span>
-------

<span data-ttu-id="725cb-109">**X**</span><span class="sxs-lookup"><span data-stu-id="725cb-109">**X**</span></span>  
<span data-ttu-id="725cb-110">Der horizontale Koordinaten-oder Spaltenwert.</span><span class="sxs-lookup"><span data-stu-id="725cb-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="725cb-111">Die Einheiten sind vom Funktions aufrufsbefehl abhängig.</span><span class="sxs-lookup"><span data-stu-id="725cb-111">The units depend on the function call.</span></span>

<span data-ttu-id="725cb-112">**J**</span><span class="sxs-lookup"><span data-stu-id="725cb-112">**Y**</span></span>  
<span data-ttu-id="725cb-113">Der vertikale Koordinaten-oder Zeilen Wert.</span><span class="sxs-lookup"><span data-stu-id="725cb-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="725cb-114">Die Einheiten sind vom Funktions aufrufsbefehl abhängig.</span><span class="sxs-lookup"><span data-stu-id="725cb-114">The units depend on the function call.</span></span>

<a name="examples"></a><span data-ttu-id="725cb-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="725cb-115">Examples</span></span>
--------

<span data-ttu-id="725cb-116">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="725cb-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="725cb-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="725cb-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="725cb-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="725cb-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="725cb-119">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="725cb-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="725cb-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="725cb-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="725cb-121">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="725cb-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="725cb-122">Header</span><span class="sxs-lookup"><span data-stu-id="725cb-122">Header</span></span></p></td>
<td><span data-ttu-id="725cb-123">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="725cb-123">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="725cb-124"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="725cb-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="725cb-125">**Informationen zur Konsolen \_ Schriftart \_**</span><span class="sxs-lookup"><span data-stu-id="725cb-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="725cb-126">**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="725cb-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="725cb-127">**Konsolen \_ Auswahl \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="725cb-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="725cb-128">**Fillconsoleoutputattribute**</span><span class="sxs-lookup"><span data-stu-id="725cb-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="725cb-129">**Fillconsoleoutputcharacter**</span><span class="sxs-lookup"><span data-stu-id="725cb-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="725cb-130">**Getconsolefontsize**</span><span class="sxs-lookup"><span data-stu-id="725cb-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="725cb-131">**Getlargestconsolewindowsize**</span><span class="sxs-lookup"><span data-stu-id="725cb-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="725cb-132">**\_Ereignis \_ Daten Satz für Maus**</span><span class="sxs-lookup"><span data-stu-id="725cb-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="725cb-133">**"Read consoleoutput"**</span><span class="sxs-lookup"><span data-stu-id="725cb-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="725cb-134">**"Read consoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="725cb-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="725cb-135">**"Read consoleoutputcharacter"**</span><span class="sxs-lookup"><span data-stu-id="725cb-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="725cb-136">**Scrollconsoleskreenbuffer**</span><span class="sxs-lookup"><span data-stu-id="725cb-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="725cb-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="725cb-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="725cb-138">**Setconsoledisplaymode**</span><span class="sxs-lookup"><span data-stu-id="725cb-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="725cb-139">**Setconsoleskreenbuffersize**</span><span class="sxs-lookup"><span data-stu-id="725cb-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="725cb-140">**Datensatz der Fenster \_ Puffer \_ Größe \_**</span><span class="sxs-lookup"><span data-stu-id="725cb-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="725cb-141">**Schreibconsoleoutput**</span><span class="sxs-lookup"><span data-stu-id="725cb-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="725cb-142">**"Schreibconsoleoutputattribute"**</span><span class="sxs-lookup"><span data-stu-id="725cb-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="725cb-143">**Schreibconsoleoutputcharacter**</span><span class="sxs-lookup"><span data-stu-id="725cb-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




