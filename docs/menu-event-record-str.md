---
title: MENU_EVENT_RECORD-Struktur
description: Beschreibt ein Menü Ereignis in einer Konsolen Eingabe \_ Daten Satzstruktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dfca825c03dbf0e63041e68adc5e43f2ca0ef669
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039518"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="63817-105">Struktur des Menü \_ Ereignis \_ Datensatzes</span><span class="sxs-lookup"><span data-stu-id="63817-105">MENU\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="63817-106">Beschreibt ein Menü Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.</span><span class="sxs-lookup"><span data-stu-id="63817-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="63817-107">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="63817-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="63817-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="63817-108">Syntax</span></span>

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="63817-109">Member</span><span class="sxs-lookup"><span data-stu-id="63817-109">Members</span></span>

<span data-ttu-id="63817-110">**dwcommandid**</span><span class="sxs-lookup"><span data-stu-id="63817-110">**dwCommandId**</span></span>  
<span data-ttu-id="63817-111">Reserviert.</span><span class="sxs-lookup"><span data-stu-id="63817-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="63817-112">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="63817-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="63817-113">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="63817-113">Minimum supported client</span></span> | <span data-ttu-id="63817-114">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="63817-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="63817-115">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="63817-115">Minimum supported server</span></span> | <span data-ttu-id="63817-116">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="63817-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="63817-117">Header</span><span class="sxs-lookup"><span data-stu-id="63817-117">Header</span></span> | <span data-ttu-id="63817-118">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="63817-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="63817-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="63817-119">See also</span></span>

[<span data-ttu-id="63817-120">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="63817-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
