---
title: CONSOLE_CURSOR_INFO Struktur
description: Enthält die Größe und Sichtbarkeits Informationen über den Konsolen Cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037012"
---
# <a name="console_cursor_info-structure"></a><span data-ttu-id="109b8-104">Konsolen \_ Cursor- \_ Informationsstruktur</span><span class="sxs-lookup"><span data-stu-id="109b8-104">CONSOLE\_CURSOR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="109b8-105">Enthält Informationen über den Konsolen Cursor.</span><span class="sxs-lookup"><span data-stu-id="109b8-105">Contains information about the console cursor.</span></span>

## <a name="syntax"></a><span data-ttu-id="109b8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="109b8-106">Syntax</span></span>

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a><span data-ttu-id="109b8-107">Member</span><span class="sxs-lookup"><span data-stu-id="109b8-107">Members</span></span>

<span data-ttu-id="109b8-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="109b8-108">**dwSize**</span></span>  
<span data-ttu-id="109b8-109">Der Prozentsatz der Zeichen Zelle, die vom Cursor ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="109b8-109">The percentage of the character cell that is filled by the cursor.</span></span> <span data-ttu-id="109b8-110">Dieser Wert liegt zwischen 1 und 100.</span><span class="sxs-lookup"><span data-stu-id="109b8-110">This value is between 1 and 100.</span></span> <span data-ttu-id="109b8-111">Die Cursor Darstellung variiert, reicht von der vollständigen Füllung der Zelle bis zum erscheinen als horizontale Linie am unteren Rand der Zelle.</span><span class="sxs-lookup"><span data-stu-id="109b8-111">The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.</span></span>

> [!NOTE]
><span data-ttu-id="109b8-112">Während der **dwSize** -Wert normalerweise zwischen 1 und 100 liegt, kann unter bestimmten Umständen ein Wert außerhalb dieses Bereichs zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="109b8-112">While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned.</span></span> <span data-ttu-id="109b8-113">Wenn z. b. " **Cursor size** " in der Registrierung auf "0" festgelegt ist, wäre der zurückgegebene **dwSize** -Wert 0 (null).</span><span class="sxs-lookup"><span data-stu-id="109b8-113">For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.</span></span>

 <span data-ttu-id="109b8-114">**bvisible**</span><span class="sxs-lookup"><span data-stu-id="109b8-114">**bVisible**</span></span>  
<span data-ttu-id="109b8-115">Die Sichtbarkeit des Cursors.</span><span class="sxs-lookup"><span data-stu-id="109b8-115">The visibility of the cursor.</span></span> <span data-ttu-id="109b8-116">Wenn der Cursor sichtbar ist, ist dieser Member " **true** ".</span><span class="sxs-lookup"><span data-stu-id="109b8-116">If the cursor is visible, this member is **TRUE** .</span></span>

## <a name="requirements"></a><span data-ttu-id="109b8-117">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="109b8-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="109b8-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="109b8-118">Minimum supported client</span></span> | <span data-ttu-id="109b8-119">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="109b8-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="109b8-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="109b8-120">Minimum supported server</span></span> | <span data-ttu-id="109b8-121">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="109b8-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="109b8-122">Header</span><span class="sxs-lookup"><span data-stu-id="109b8-122">Header</span></span> | <span data-ttu-id="109b8-123">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="109b8-123">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="109b8-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="109b8-124">See also</span></span>

[<span data-ttu-id="109b8-125">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="109b8-125">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="109b8-126">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="109b8-126">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)
