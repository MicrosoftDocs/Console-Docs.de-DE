---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT-Struktur
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: f9cbe94fff616a93d835f47b618a28bb9f521891
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358490"
---
# <a name="small_rect-structure"></a><span data-ttu-id="5b3d3-104">Kleine \_ Rect-Struktur</span><span class="sxs-lookup"><span data-stu-id="5b3d3-104">SMALL\_RECT structure</span></span>

<span data-ttu-id="5b3d3-105">Definiert die Koordinaten der oberen linken und unteren rechten Ecke eines Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="5b3d3-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b3d3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b3d3-106">Syntax</span></span>

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a><span data-ttu-id="5b3d3-107">Member</span><span class="sxs-lookup"><span data-stu-id="5b3d3-107">Members</span></span>

<span data-ttu-id="5b3d3-108">**Left**</span><span class="sxs-lookup"><span data-stu-id="5b3d3-108">**Left**</span></span>  
<span data-ttu-id="5b3d3-109">Die x-Koordinate der oberen linken Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="5b3d3-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="5b3d3-110">**Top**</span><span class="sxs-lookup"><span data-stu-id="5b3d3-110">**Top**</span></span>  
<span data-ttu-id="5b3d3-111">Die y-Koordinate der oberen linken Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="5b3d3-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="5b3d3-112">**Right**</span><span class="sxs-lookup"><span data-stu-id="5b3d3-112">**Right**</span></span>  
<span data-ttu-id="5b3d3-113">Die x-Koordinate der unteren rechten Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="5b3d3-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="5b3d3-114">**bottom**</span><span class="sxs-lookup"><span data-stu-id="5b3d3-114">**Bottom**</span></span>  
<span data-ttu-id="5b3d3-115">Die y-Koordinate der unteren rechten Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="5b3d3-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b3d3-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="5b3d3-116">Remarks</span></span>

<span data-ttu-id="5b3d3-117">Diese Struktur wird von Konsolenfunktionen verwendet, um rechteckige Bereiche von Konsolenbildschirm Puffern anzugeben, wobei die Koordinaten die Zeilen und Spalten von Bildschirm Puffer Zeichen Zellen angeben.</span><span class="sxs-lookup"><span data-stu-id="5b3d3-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

## <a name="examples"></a><span data-ttu-id="5b3d3-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5b3d3-118">Examples</span></span>

<span data-ttu-id="5b3d3-119">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="5b3d3-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="5b3d3-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5b3d3-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5b3d3-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="5b3d3-121">Minimum supported client</span></span> | <span data-ttu-id="5b3d3-122">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5b3d3-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="5b3d3-123">Minimum supported server</span></span> | <span data-ttu-id="5b3d3-124">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5b3d3-125">Header</span><span class="sxs-lookup"><span data-stu-id="5b3d3-125">Header</span></span> | <span data-ttu-id="5b3d3-126">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5b3d3-126">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="5b3d3-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5b3d3-127">See also</span></span>

<span data-ttu-id="5b3d3-128">[**Rect**](/previous-versions//dd162897(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5b3d3-128">[**RECT**](/previous-versions//dd162897(v=vs.85))</span></span>

<span data-ttu-id="5b3d3-129">[**RECTL**](/previous-versions//dd162907(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5b3d3-129">[**RECTL**](/previous-versions//dd162907(v=vs.85))</span></span>