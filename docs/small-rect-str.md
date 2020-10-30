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
ms.openlocfilehash: 93121864c8754b281b92051a5e4a174b2d5956a3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037098"
---
# <a name="small_rect-structure"></a><span data-ttu-id="1f916-104">Kleine \_ Rect-Struktur</span><span class="sxs-lookup"><span data-stu-id="1f916-104">SMALL\_RECT structure</span></span>

<span data-ttu-id="1f916-105">Definiert die Koordinaten der oberen linken und unteren rechten Ecke eines Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="1f916-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f916-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f916-106">Syntax</span></span>

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a><span data-ttu-id="1f916-107">Member</span><span class="sxs-lookup"><span data-stu-id="1f916-107">Members</span></span>

<span data-ttu-id="1f916-108">**Left**</span><span class="sxs-lookup"><span data-stu-id="1f916-108">**Left**</span></span>  
<span data-ttu-id="1f916-109">Die x-Koordinate der oberen linken Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="1f916-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="1f916-110">**Top**</span><span class="sxs-lookup"><span data-stu-id="1f916-110">**Top**</span></span>  
<span data-ttu-id="1f916-111">Die y-Koordinate der oberen linken Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="1f916-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="1f916-112">**Right**</span><span class="sxs-lookup"><span data-stu-id="1f916-112">**Right**</span></span>  
<span data-ttu-id="1f916-113">Die x-Koordinate der unteren rechten Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="1f916-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="1f916-114">**bottom**</span><span class="sxs-lookup"><span data-stu-id="1f916-114">**Bottom**</span></span>  
<span data-ttu-id="1f916-115">Die y-Koordinate der unteren rechten Ecke des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="1f916-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f916-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1f916-116">Remarks</span></span>

<span data-ttu-id="1f916-117">Diese Struktur wird von Konsolenfunktionen verwendet, um rechteckige Bereiche von Konsolenbildschirm Puffern anzugeben, wobei die Koordinaten die Zeilen und Spalten von Bildschirm Puffer Zeichen Zellen angeben.</span><span class="sxs-lookup"><span data-stu-id="1f916-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

## <a name="examples"></a><span data-ttu-id="1f916-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1f916-118">Examples</span></span>

<span data-ttu-id="1f916-119">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="1f916-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1f916-120">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="1f916-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1f916-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1f916-121">Minimum supported client</span></span> | <span data-ttu-id="1f916-122">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1f916-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1f916-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1f916-123">Minimum supported server</span></span> | <span data-ttu-id="1f916-124">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1f916-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1f916-125">Header</span><span class="sxs-lookup"><span data-stu-id="1f916-125">Header</span></span> | <span data-ttu-id="1f916-126">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1f916-126">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1f916-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1f916-127">See also</span></span>

[<span data-ttu-id="1f916-128">**Rect**</span><span class="sxs-lookup"><span data-stu-id="1f916-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="1f916-129">**RECTL**</span><span class="sxs-lookup"><span data-stu-id="1f916-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)
