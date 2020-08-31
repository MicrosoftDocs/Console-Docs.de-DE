---
title: FOCUS_EVENT_RECORD Struktur
description: Beschreibt ein Fokus Ereignis in einer Konsolen Eingabe \_ Daten Satzstruktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 61f37e3645a66ca9f755f66f0baa03a2238983ad
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059874"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="ffe9e-105">Struktur des Fokus \_ Ereignis \_ Datensatzes</span><span class="sxs-lookup"><span data-stu-id="ffe9e-105">FOCUS\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="ffe9e-106">Beschreibt ein Fokus Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="ffe9e-107">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="ffe9e-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="ffe9e-108">Syntax</span></span>
------

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="ffe9e-109">Member</span><span class="sxs-lookup"><span data-stu-id="ffe9e-109">Members</span></span>
-------

<span data-ttu-id="ffe9e-110">**bsetfocus**</span><span class="sxs-lookup"><span data-stu-id="ffe9e-110">**bSetFocus**</span></span>  
<span data-ttu-id="ffe9e-111">Reserviert.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="ffe9e-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ffe9e-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ffe9e-113">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ffe9e-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ffe9e-114">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ffe9e-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ffe9e-115">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ffe9e-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ffe9e-116">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ffe9e-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ffe9e-117">Header</span><span class="sxs-lookup"><span data-stu-id="ffe9e-117">Header</span></span></p></td>
<td><span data-ttu-id="ffe9e-118">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ffe9e-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ffe9e-119"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ffe9e-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ffe9e-120">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="ffe9e-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




