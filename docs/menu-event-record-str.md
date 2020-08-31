---
title: MENU_EVENT_RECORD Struktur
description: Beschreibt ein Menü Ereignis in einer Konsolen Eingabe \_ Daten Satzstruktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- base.menu\_event\_record\_str
- consoles.menu\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd
topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8bbfbf6ad8bd885d69ce08e94dfced93b0bd3257
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059618"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="abb5b-105">Struktur des Menü \_ Ereignis \_ Datensatzes</span><span class="sxs-lookup"><span data-stu-id="abb5b-105">MENU\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="abb5b-106">Beschreibt ein Menü Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.</span><span class="sxs-lookup"><span data-stu-id="abb5b-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="abb5b-107">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="abb5b-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="abb5b-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="abb5b-108">Syntax</span></span>
------

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="abb5b-109">Member</span><span class="sxs-lookup"><span data-stu-id="abb5b-109">Members</span></span>
-------

<span data-ttu-id="abb5b-110">**dwcommandid**</span><span class="sxs-lookup"><span data-stu-id="abb5b-110">**dwCommandId**</span></span>  
<span data-ttu-id="abb5b-111">Reserviert.</span><span class="sxs-lookup"><span data-stu-id="abb5b-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="abb5b-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="abb5b-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="abb5b-113">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="abb5b-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="abb5b-114">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="abb5b-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="abb5b-115">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="abb5b-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="abb5b-116">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="abb5b-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="abb5b-117">Header</span><span class="sxs-lookup"><span data-stu-id="abb5b-117">Header</span></span></p></td>
<td><span data-ttu-id="abb5b-118">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="abb5b-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="abb5b-119"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="abb5b-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="abb5b-120">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="abb5b-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




