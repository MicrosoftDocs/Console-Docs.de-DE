---
title: CONSOLE_FONT_INFOEX Struktur
description: Siehe Referenzinformationen zur CONSOLE_FONT_INFOEX Struktur, die erweiterte Informationen für eine Konsolen Schriftart enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 12977e288a63397c581143683047239e4d410eec
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060099"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="c9a3c-104">Konsolen \_ Schriftart \_ INFOEX-Struktur</span><span class="sxs-lookup"><span data-stu-id="c9a3c-104">CONSOLE\_FONT\_INFOEX structure</span></span>


<span data-ttu-id="c9a3c-105">Enthält erweiterte Informationen für eine Konsolen Schriftart.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-105">Contains extended information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="c9a3c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9a3c-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

<a name="members"></a><span data-ttu-id="c9a3c-107">Member</span><span class="sxs-lookup"><span data-stu-id="c9a3c-107">Members</span></span>
-------

<span data-ttu-id="c9a3c-108">**CBSIZE**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-108">**cbSize**</span></span>  
<span data-ttu-id="c9a3c-109">Die Größe der-Struktur in Bytes.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="c9a3c-110">Dieser Member muss auf festgelegt werden, `sizeof(CONSOLE_FONT_INFOEX)` bevor [**getcurrentconsolefontex**](getcurrentconsolefontex.md) aufgerufen wird. andernfalls tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="c9a3c-111">**nschriftart**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-111">**nFont**</span></span>  
<span data-ttu-id="c9a3c-112">Der Index der Schriftart in der Konsolen Schriftart Tabelle des Systems.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="c9a3c-113">**dwfontsize**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-113">**dwFontSize**</span></span>  
<span data-ttu-id="c9a3c-114">Eine [**Koord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="c9a3c-115">Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="c9a3c-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-116">**FontFamily**</span></span>  
<span data-ttu-id="c9a3c-117">Der Schrift Schnitt und die Familie.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-117">The font pitch and family.</span></span> <span data-ttu-id="c9a3c-118">Informationen zu den möglichen Werten für diesen Member finden Sie in der Beschreibung des **tmpitchandfamily** -Members der [**TextMetric**](https://msdn.microsoft.com/library/windows/desktop/dd145132) -Struktur.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.</span></span>

<span data-ttu-id="c9a3c-119">**Schriftbreite**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-119">**FontWeight**</span></span>  
<span data-ttu-id="c9a3c-120">Die Schrift Breite.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-120">The font weight.</span></span> <span data-ttu-id="c9a3c-121">Die Gewichtung kann zwischen 100 und 1000 liegen, in Vielfachen von 100.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="c9a3c-122">Beispielsweise ist das normale Gewicht 400, während 700 fett formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="c9a3c-123">**Fakename**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-123">**FaceName**</span></span>  
<span data-ttu-id="c9a3c-124">Der Name der Schriftart (z. b. Courier oder Arial).</span><span class="sxs-lookup"><span data-stu-id="c9a3c-124">The name of the typeface (such as Courier or Arial).</span></span>

<a name="remarks"></a><span data-ttu-id="c9a3c-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c9a3c-125">Remarks</span></span>
-------

<span data-ttu-id="c9a3c-126">Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="c9a3c-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="c9a3c-127">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c9a3c-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c9a3c-128">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c9a3c-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c9a3c-129">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c9a3c-129">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c9a3c-130">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c9a3c-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c9a3c-131">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="c9a3c-131">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c9a3c-132">Header</span><span class="sxs-lookup"><span data-stu-id="c9a3c-132">Header</span></span></p></td>
<td><span data-ttu-id="c9a3c-133">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c9a3c-133">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c9a3c-134"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c9a3c-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c9a3c-135">**Getcurrentconsolefontex**</span><span class="sxs-lookup"><span data-stu-id="c9a3c-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)

 

 




