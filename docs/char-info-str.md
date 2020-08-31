---
title: CHAR_INFO Struktur
description: Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an. Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6244edaa06b6dd69f8ab3962cf42cb893d08f699
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060210"
---
# <a name="char_info-structure"></a><span data-ttu-id="0a00d-105">Char \_ Info-Struktur</span><span class="sxs-lookup"><span data-stu-id="0a00d-105">CHAR\_INFO structure</span></span>


<span data-ttu-id="0a00d-106">Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an.</span><span class="sxs-lookup"><span data-stu-id="0a00d-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="0a00d-107">Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="0a00d-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="0a00d-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a00d-108">Syntax</span></span>
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

<a name="members"></a><span data-ttu-id="0a00d-109">Member</span><span class="sxs-lookup"><span data-stu-id="0a00d-109">Members</span></span>
-------

<span data-ttu-id="0a00d-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="0a00d-110">**Char**</span></span>  
<span data-ttu-id="0a00d-111">Eine Union der folgenden Member.</span><span class="sxs-lookup"><span data-stu-id="0a00d-111">A union of the following members.</span></span>

<span data-ttu-id="0a00d-112">**Unicodechar**</span><span class="sxs-lookup"><span data-stu-id="0a00d-112">**UnicodeChar**</span></span>  
<span data-ttu-id="0a00d-113">Unicode-Zeichen einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="0a00d-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="0a00d-114">**Asciichar**</span><span class="sxs-lookup"><span data-stu-id="0a00d-114">**AsciiChar**</span></span>  
<span data-ttu-id="0a00d-115">ANSI-Zeichen einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="0a00d-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="0a00d-116">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="0a00d-116">**Attributes**</span></span>  
<span data-ttu-id="0a00d-117">Die Zeichen Attribute.</span><span class="sxs-lookup"><span data-stu-id="0a00d-117">The character attributes.</span></span> <span data-ttu-id="0a00d-118">Dieser Member kann NULL oder eine beliebige Kombination der folgenden Werte sein.</span><span class="sxs-lookup"><span data-stu-id="0a00d-118">This member can be zero or any combination of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="0a00d-119">Wert</span><span class="sxs-lookup"><span data-stu-id="0a00d-119">Value</span></span></th>
<th><span data-ttu-id="0a00d-120">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="0a00d-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="0a00d-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="0a00d-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="0a00d-122">Textfarbe enthält blau.</span><span class="sxs-lookup"><span data-stu-id="0a00d-122">Text color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="0a00d-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="0a00d-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="0a00d-124">Textfarbe enthält grün.</span><span class="sxs-lookup"><span data-stu-id="0a00d-124">Text color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="0a00d-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="0a00d-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="0a00d-126">Textfarbe enthält rot.</span><span class="sxs-lookup"><span data-stu-id="0a00d-126">Text color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="0a00d-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="0a00d-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="0a00d-128">Die Textfarbe wird verstärkt.</span><span class="sxs-lookup"><span data-stu-id="0a00d-128">Text color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="0a00d-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="0a00d-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="0a00d-130">Hintergrundfarbe enthält blau.</span><span class="sxs-lookup"><span data-stu-id="0a00d-130">Background color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="0a00d-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="0a00d-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="0a00d-132">Hintergrundfarbe enthält grün.</span><span class="sxs-lookup"><span data-stu-id="0a00d-132">Background color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="0a00d-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="0a00d-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="0a00d-134">Die Hintergrundfarbe enthält rot.</span><span class="sxs-lookup"><span data-stu-id="0a00d-134">Background color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="0a00d-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="0a00d-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="0a00d-136">Die Hintergrundfarbe wird verstärkt.</span><span class="sxs-lookup"><span data-stu-id="0a00d-136">Background color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="0a00d-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="0a00d-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="0a00d-138">Führendes Byte.</span><span class="sxs-lookup"><span data-stu-id="0a00d-138">Leading byte.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="0a00d-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="0a00d-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="0a00d-140">Nachfolgendes Byte.</span><span class="sxs-lookup"><span data-stu-id="0a00d-140">Trailing byte.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="0a00d-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span><span class="sxs-lookup"><span data-stu-id="0a00d-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span></span></td>
<td><p><span data-ttu-id="0a00d-142">Obere horizontale</span><span class="sxs-lookup"><span data-stu-id="0a00d-142">Top horizontal</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="0a00d-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span><span class="sxs-lookup"><span data-stu-id="0a00d-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span></span></td>
<td><p><span data-ttu-id="0a00d-144">Links vertikal.</span><span class="sxs-lookup"><span data-stu-id="0a00d-144">Left vertical.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="0a00d-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span><span class="sxs-lookup"><span data-stu-id="0a00d-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span></span></td>
<td><p><span data-ttu-id="0a00d-146">Rechts vertikal.</span><span class="sxs-lookup"><span data-stu-id="0a00d-146">Right vertical.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="0a00d-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span><span class="sxs-lookup"><span data-stu-id="0a00d-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span></span></td>
<td><p><span data-ttu-id="0a00d-148">Umgekehrtes Vordergrund-und Hintergrund Attribut.</span><span class="sxs-lookup"><span data-stu-id="0a00d-148">Reverse foreground and background attribute.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="0a00d-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0X8000</span><span class="sxs-lookup"><span data-stu-id="0a00d-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span></span></td>
<td><p><span data-ttu-id="0a00d-150">Unterstrich.</span><span class="sxs-lookup"><span data-stu-id="0a00d-150">Underscore.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="examples"></a><span data-ttu-id="0a00d-151">Beispiele</span><span class="sxs-lookup"><span data-stu-id="0a00d-151">Examples</span></span>
--------

<span data-ttu-id="0a00d-152">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="0a00d-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="0a00d-153">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0a00d-153">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0a00d-154">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0a00d-154">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0a00d-155">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0a00d-155">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0a00d-156">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0a00d-156">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0a00d-157">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0a00d-157">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0a00d-158">Header</span><span class="sxs-lookup"><span data-stu-id="0a00d-158">Header</span></span></p></td>
<td><span data-ttu-id="0a00d-159">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0a00d-159">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0a00d-160"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0a00d-160"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0a00d-161">**"Read consoleoutput"**</span><span class="sxs-lookup"><span data-stu-id="0a00d-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="0a00d-162">**Scrollconsoleskreenbuffer**</span><span class="sxs-lookup"><span data-stu-id="0a00d-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="0a00d-163">**Schreibconsoleoutput**</span><span class="sxs-lookup"><span data-stu-id="0a00d-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

 

 




