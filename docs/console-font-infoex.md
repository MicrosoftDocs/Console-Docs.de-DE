---
title: CONSOLE_FONT_INFOEX Struktur
description: Siehe Referenzinformationen zur CONSOLE_FONT_INFOEX Struktur, die erweiterte Informationen für eine Konsolen Schriftart enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: ef89d1bf47a4153d44140d3f9f4845bb7496680e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039258"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="75d13-104">Konsolen \_ Schriftart \_ INFOEX-Struktur</span><span class="sxs-lookup"><span data-stu-id="75d13-104">CONSOLE\_FONT\_INFOEX structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="75d13-105">Enthält erweiterte Informationen für eine Konsolen Schriftart.</span><span class="sxs-lookup"><span data-stu-id="75d13-105">Contains extended information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="75d13-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="75d13-106">Syntax</span></span>

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## <a name="members"></a><span data-ttu-id="75d13-107">Member</span><span class="sxs-lookup"><span data-stu-id="75d13-107">Members</span></span>

<span data-ttu-id="75d13-108">**CBSIZE**</span><span class="sxs-lookup"><span data-stu-id="75d13-108">**cbSize**</span></span>  
<span data-ttu-id="75d13-109">Die Größe der-Struktur in Bytes.</span><span class="sxs-lookup"><span data-stu-id="75d13-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="75d13-110">Dieser Member muss auf festgelegt werden, `sizeof(CONSOLE_FONT_INFOEX)` bevor [**getcurrentconsolefontex**](getcurrentconsolefontex.md) aufgerufen wird. andernfalls tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="75d13-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="75d13-111">**nschriftart**</span><span class="sxs-lookup"><span data-stu-id="75d13-111">**nFont**</span></span>  
<span data-ttu-id="75d13-112">Der Index der Schriftart in der Konsolen Schriftart Tabelle des Systems.</span><span class="sxs-lookup"><span data-stu-id="75d13-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="75d13-113">**dwfontsize**</span><span class="sxs-lookup"><span data-stu-id="75d13-113">**dwFontSize**</span></span>  
<span data-ttu-id="75d13-114">Eine [**Koord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält.</span><span class="sxs-lookup"><span data-stu-id="75d13-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="75d13-115">Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.</span><span class="sxs-lookup"><span data-stu-id="75d13-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="75d13-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="75d13-116">**FontFamily**</span></span>  
<span data-ttu-id="75d13-117">Der Schrift Schnitt und die Familie.</span><span class="sxs-lookup"><span data-stu-id="75d13-117">The font pitch and family.</span></span> <span data-ttu-id="75d13-118">Informationen zu den möglichen Werten für diesen Member finden Sie in der Beschreibung des **tmpitchandfamily** -Members der [**TextMetric**](https://msdn.microsoft.com/library/windows/desktop/dd145132) -Struktur.</span><span class="sxs-lookup"><span data-stu-id="75d13-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.</span></span>

<span data-ttu-id="75d13-119">**Schriftbreite**</span><span class="sxs-lookup"><span data-stu-id="75d13-119">**FontWeight**</span></span>  
<span data-ttu-id="75d13-120">Die Schrift Breite.</span><span class="sxs-lookup"><span data-stu-id="75d13-120">The font weight.</span></span> <span data-ttu-id="75d13-121">Die Gewichtung kann zwischen 100 und 1000 liegen, in Vielfachen von 100.</span><span class="sxs-lookup"><span data-stu-id="75d13-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="75d13-122">Beispielsweise ist das normale Gewicht 400, während 700 fett formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="75d13-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="75d13-123">**Fakename**</span><span class="sxs-lookup"><span data-stu-id="75d13-123">**FaceName**</span></span>  
<span data-ttu-id="75d13-124">Der Name der Schriftart (z. b. Courier oder Arial).</span><span class="sxs-lookup"><span data-stu-id="75d13-124">The name of the typeface (such as Courier or Arial).</span></span>

## <a name="remarks"></a><span data-ttu-id="75d13-125">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="75d13-125">Remarks</span></span>

<span data-ttu-id="75d13-126">Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="75d13-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="75d13-127">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="75d13-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="75d13-128">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="75d13-128">Minimum supported client</span></span> | <span data-ttu-id="75d13-129">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="75d13-129">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="75d13-130">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="75d13-130">Minimum supported server</span></span> | <span data-ttu-id="75d13-131">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="75d13-131">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="75d13-132">Header</span><span class="sxs-lookup"><span data-stu-id="75d13-132">Header</span></span> | <span data-ttu-id="75d13-133">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="75d13-133">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="75d13-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="75d13-134">See also</span></span>

[<span data-ttu-id="75d13-135">**GetCurrentConsoleFontEx**</span><span class="sxs-lookup"><span data-stu-id="75d13-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)
