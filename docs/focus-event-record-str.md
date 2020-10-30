---
title: FOCUS_EVENT_RECORD-Struktur
description: Beschreibt ein Fokus Ereignis in einer Konsolen Eingabe \_ Daten Satzstruktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dc86c1b5b1c42a9d905673da4ea368de76a5fae9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038168"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="e0441-105">Struktur des Fokus \_ Ereignis \_ Datensatzes</span><span class="sxs-lookup"><span data-stu-id="e0441-105">FOCUS\_EVENT\_RECORD structure</span></span>

<span data-ttu-id="e0441-106">Beschreibt ein Fokus Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.</span><span class="sxs-lookup"><span data-stu-id="e0441-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="e0441-107">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="e0441-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0441-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0441-108">Syntax</span></span>

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="e0441-109">Member</span><span class="sxs-lookup"><span data-stu-id="e0441-109">Members</span></span>

<span data-ttu-id="e0441-110">**bsetfocus**</span><span class="sxs-lookup"><span data-stu-id="e0441-110">**bSetFocus**</span></span>  
<span data-ttu-id="e0441-111">Reserviert.</span><span class="sxs-lookup"><span data-stu-id="e0441-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0441-112">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="e0441-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e0441-113">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e0441-113">Minimum supported client</span></span> | <span data-ttu-id="e0441-114">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e0441-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e0441-115">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e0441-115">Minimum supported server</span></span> | <span data-ttu-id="e0441-116">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e0441-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e0441-117">Header</span><span class="sxs-lookup"><span data-stu-id="e0441-117">Header</span></span> | <span data-ttu-id="e0441-118">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e0441-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e0441-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e0441-119">See also</span></span>

[<span data-ttu-id="e0441-120">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="e0441-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
