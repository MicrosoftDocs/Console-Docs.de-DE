---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT Struktur
description: Definiert die Koordinaten der oberen linken und unteren rechten Ecke eines Rechtecks.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: b0c0bfe93c85af89c5aaefeda032795de72ed627
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060555"
---
# <a name="small_rect-structure"></a><span data-ttu-id="b84a4-104">Kleine \_ Rect-Struktur</span><span class="sxs-lookup"><span data-stu-id="b84a4-104">SMALL\_RECT structure</span></span>


<span data-ttu-id="b84a4-105">Definiert die Koordinaten der oberen linken und unteren rechten Ecke eines Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="b84a4-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

<a name="syntax"></a><span data-ttu-id="b84a4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b84a4-106">Syntax</span></span>
------

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

<a name="members"></a><span data-ttu-id="b84a4-107">Member</span><span class="sxs-lookup"><span data-stu-id="b84a4-107">Members</span></span>
-------

<span data-ttu-id="b84a4-108">**Left**</span><span class="sxs-lookup"><span data-stu-id="b84a4-108">**Left**</span></span>  
<span data-ttu-id="b84a4-109">Die x-Koordinate der oberen linken Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="b84a4-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="b84a4-110">**Top**</span><span class="sxs-lookup"><span data-stu-id="b84a4-110">**Top**</span></span>  
<span data-ttu-id="b84a4-111">Die y-Koordinate der oberen linken Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="b84a4-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="b84a4-112">**Right**</span><span class="sxs-lookup"><span data-stu-id="b84a4-112">**Right**</span></span>  
<span data-ttu-id="b84a4-113">Die x-Koordinate der unteren rechten Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="b84a4-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="b84a4-114">**Unten**</span><span class="sxs-lookup"><span data-stu-id="b84a4-114">**Bottom**</span></span>  
<span data-ttu-id="b84a4-115">Die y-Koordinate der unteren rechten Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="b84a4-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

<a name="remarks"></a><span data-ttu-id="b84a4-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b84a4-116">Remarks</span></span>
-------

<span data-ttu-id="b84a4-117">Diese Struktur wird von Konsolenfunktionen verwendet, um rechteckige Bereiche von Konsolenbildschirm Puffern anzugeben, wobei die Koordinaten die Zeilen und Spalten von Bildschirm Puffer Zeichen Zellen angeben.</span><span class="sxs-lookup"><span data-stu-id="b84a4-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

<a name="examples"></a><span data-ttu-id="b84a4-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b84a4-118">Examples</span></span>
--------

<span data-ttu-id="b84a4-119">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="b84a4-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="b84a4-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b84a4-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b84a4-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b84a4-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b84a4-122">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b84a4-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b84a4-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b84a4-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b84a4-124">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b84a4-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b84a4-125">Header</span><span class="sxs-lookup"><span data-stu-id="b84a4-125">Header</span></span></p></td>
<td><span data-ttu-id="b84a4-126">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b84a4-126">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b84a4-127"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b84a4-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b84a4-128">**Rect**</span><span class="sxs-lookup"><span data-stu-id="b84a4-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="b84a4-129">**RECTL**</span><span class="sxs-lookup"><span data-stu-id="b84a4-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 




