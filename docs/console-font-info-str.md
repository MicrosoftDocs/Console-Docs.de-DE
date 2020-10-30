---
title: CONSOLE_FONT_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_FONT_INFO Struktur, die den Index und die Größe einer Konsolen Schriftart enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037138"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="30d15-104">Struktur der Konsolen \_ Schriftart \_ Info</span><span class="sxs-lookup"><span data-stu-id="30d15-104">CONSOLE\_FONT\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="30d15-105">Enthält Informationen für eine Konsolen Schriftart.</span><span class="sxs-lookup"><span data-stu-id="30d15-105">Contains information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="30d15-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="30d15-106">Syntax</span></span>

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a><span data-ttu-id="30d15-107">Member</span><span class="sxs-lookup"><span data-stu-id="30d15-107">Members</span></span>

<span data-ttu-id="30d15-108">**nschriftart**</span><span class="sxs-lookup"><span data-stu-id="30d15-108">**nFont**</span></span>  
<span data-ttu-id="30d15-109">Der Index der Schriftart in der Konsolen Schriftart Tabelle des Systems.</span><span class="sxs-lookup"><span data-stu-id="30d15-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="30d15-110">**dwfontsize**</span><span class="sxs-lookup"><span data-stu-id="30d15-110">**dwFontSize**</span></span>  
<span data-ttu-id="30d15-111">Eine [**Koord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält.</span><span class="sxs-lookup"><span data-stu-id="30d15-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="30d15-112">Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.</span><span class="sxs-lookup"><span data-stu-id="30d15-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

## <a name="remarks"></a><span data-ttu-id="30d15-113">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="30d15-113">Remarks</span></span>

<span data-ttu-id="30d15-114">Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="30d15-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="30d15-115">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="30d15-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="30d15-116">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="30d15-116">Minimum supported client</span></span> | <span data-ttu-id="30d15-117">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="30d15-117">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="30d15-118">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="30d15-118">Minimum supported server</span></span> | <span data-ttu-id="30d15-119">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="30d15-119">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="30d15-120">Header</span><span class="sxs-lookup"><span data-stu-id="30d15-120">Header</span></span> | <span data-ttu-id="30d15-121">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="30d15-121">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="30d15-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="30d15-122">See also</span></span>

[<span data-ttu-id="30d15-123">**Koord**</span><span class="sxs-lookup"><span data-stu-id="30d15-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="30d15-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="30d15-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)
