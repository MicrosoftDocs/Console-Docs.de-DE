---
title: CONSOLE_FONT_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_FONT_INFO Struktur, die den Index und die Größe einer Konsolen Schriftart enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c4218c53eacd95d67f3dc9056f5a1024ac1a8ab0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060130"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="67b80-104">Struktur der Konsolen \_ Schriftart \_ Info</span><span class="sxs-lookup"><span data-stu-id="67b80-104">CONSOLE\_FONT\_INFO structure</span></span>


<span data-ttu-id="67b80-105">Enthält Informationen für eine Konsolen Schriftart.</span><span class="sxs-lookup"><span data-stu-id="67b80-105">Contains information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="67b80-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="67b80-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

<a name="members"></a><span data-ttu-id="67b80-107">Member</span><span class="sxs-lookup"><span data-stu-id="67b80-107">Members</span></span>
-------

<span data-ttu-id="67b80-108">**nschriftart**</span><span class="sxs-lookup"><span data-stu-id="67b80-108">**nFont**</span></span>  
<span data-ttu-id="67b80-109">Der Index der Schriftart in der Konsolen Schriftart Tabelle des Systems.</span><span class="sxs-lookup"><span data-stu-id="67b80-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="67b80-110">**dwfontsize**</span><span class="sxs-lookup"><span data-stu-id="67b80-110">**dwFontSize**</span></span>  
<span data-ttu-id="67b80-111">Eine [**Koord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält.</span><span class="sxs-lookup"><span data-stu-id="67b80-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="67b80-112">Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.</span><span class="sxs-lookup"><span data-stu-id="67b80-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<a name="remarks"></a><span data-ttu-id="67b80-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="67b80-113">Remarks</span></span>
-------

<span data-ttu-id="67b80-114">Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="67b80-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="67b80-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="67b80-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="67b80-116">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="67b80-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="67b80-117">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="67b80-117">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67b80-118">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="67b80-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="67b80-119">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="67b80-119">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67b80-120">Header</span><span class="sxs-lookup"><span data-stu-id="67b80-120">Header</span></span></p></td>
<td><span data-ttu-id="67b80-121">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="67b80-121">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="67b80-122"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="67b80-122"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="67b80-123">**Koord**</span><span class="sxs-lookup"><span data-stu-id="67b80-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="67b80-124">**Getcurrentconsolefont**</span><span class="sxs-lookup"><span data-stu-id="67b80-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




