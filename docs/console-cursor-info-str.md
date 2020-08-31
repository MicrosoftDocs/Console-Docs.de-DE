---
title: CONSOLE_CURSOR_INFO Struktur
description: Enthält die Größe und Sichtbarkeits Informationen über den Konsolen Cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0ac3eb459810f2c8ebc861759312350a487abd3c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060131"
---
# <a name="console_cursor_info-structure"></a><span data-ttu-id="230b1-104">Konsolen \_ Cursor- \_ Informationsstruktur</span><span class="sxs-lookup"><span data-stu-id="230b1-104">CONSOLE\_CURSOR\_INFO structure</span></span>


<span data-ttu-id="230b1-105">Enthält Informationen über den Konsolen Cursor.</span><span class="sxs-lookup"><span data-stu-id="230b1-105">Contains information about the console cursor.</span></span>

<a name="syntax"></a><span data-ttu-id="230b1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="230b1-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

<a name="members"></a><span data-ttu-id="230b1-107">Member</span><span class="sxs-lookup"><span data-stu-id="230b1-107">Members</span></span>
-------

<span data-ttu-id="230b1-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="230b1-108">**dwSize**</span></span>  
<span data-ttu-id="230b1-109">Der Prozentsatz der Zeichen Zelle, die vom Cursor ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="230b1-109">The percentage of the character cell that is filled by the cursor.</span></span> <span data-ttu-id="230b1-110">Dieser Wert liegt zwischen 1 und 100.</span><span class="sxs-lookup"><span data-stu-id="230b1-110">This value is between 1 and 100.</span></span> <span data-ttu-id="230b1-111">Die Cursor Darstellung variiert, reicht von der vollständigen Füllung der Zelle bis zum erscheinen als horizontale Linie am unteren Rand der Zelle.</span><span class="sxs-lookup"><span data-stu-id="230b1-111">The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.</span></span>

<span data-ttu-id="230b1-112">**Hinweis**    Während der **dwSize** -Wert normalerweise zwischen 1 und 100 liegt, kann unter bestimmten Umständen ein Wert außerhalb dieses Bereichs zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="230b1-112">**Note**  While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned.</span></span> <span data-ttu-id="230b1-113">Wenn z. b. " **Cursor size** " in der Registrierung auf "0" festgelegt ist, wäre der zurückgegebene **dwSize** -Wert 0 (null).</span><span class="sxs-lookup"><span data-stu-id="230b1-113">For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.</span></span>

 

<span data-ttu-id="230b1-114">**bvisible**</span><span class="sxs-lookup"><span data-stu-id="230b1-114">**bVisible**</span></span>  
<span data-ttu-id="230b1-115">Die Sichtbarkeit des Cursors.</span><span class="sxs-lookup"><span data-stu-id="230b1-115">The visibility of the cursor.</span></span> <span data-ttu-id="230b1-116">Wenn der Cursor sichtbar ist, ist dieser Member " **true**".</span><span class="sxs-lookup"><span data-stu-id="230b1-116">If the cursor is visible, this member is **TRUE**.</span></span>

<a name="requirements"></a><span data-ttu-id="230b1-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="230b1-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="230b1-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="230b1-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="230b1-119">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="230b1-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="230b1-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="230b1-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="230b1-121">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="230b1-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="230b1-122">Header</span><span class="sxs-lookup"><span data-stu-id="230b1-122">Header</span></span></p></td>
<td><span data-ttu-id="230b1-123">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="230b1-123">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="230b1-124"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="230b1-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="230b1-125">**Getconsolecursorinfo**</span><span class="sxs-lookup"><span data-stu-id="230b1-125">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="230b1-126">**Setconsolecursorinfo**</span><span class="sxs-lookup"><span data-stu-id="230b1-126">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 




