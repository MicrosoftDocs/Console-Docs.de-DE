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
# <a name="char_info-structure"></a>Char \_ Info-Struktur


Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an. Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.

<a name="syntax"></a>Syntax
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

<a name="members"></a>Member
-------

**Char**  
Eine Union der folgenden Member.

**Unicodechar**  
Unicode-Zeichen einer Bildschirm Puffer-Zeichen Zelle.

**Asciichar**  
ANSI-Zeichen einer Bildschirm Puffer-Zeichen Zelle.

**Attribute**  
Die Zeichen Attribute. Dieser Member kann NULL oder eine beliebige Kombination der folgenden Werte sein.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</td>
<td><p>Textfarbe enthält blau.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</td>
<td><p>Textfarbe enthält grün.</p></td>
</tr>
<tr class="odd">
<td><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</td>
<td><p>Textfarbe enthält rot.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</td>
<td><p>Die Textfarbe wird verstärkt.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</td>
<td><p>Hintergrundfarbe enthält blau.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</td>
<td><p>Hintergrundfarbe enthält grün.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</td>
<td><p>Die Hintergrundfarbe enthält rot.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</td>
<td><p>Die Hintergrundfarbe wird verstärkt.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</td>
<td><p>Führendes Byte.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</td>
<td><p>Nachfolgendes Byte.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</td>
<td><p>Obere horizontale</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</td>
<td><p>Links vertikal.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</td>
<td><p>Rechts vertikal.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</td>
<td><p>Umgekehrtes Vordergrund-und Hintergrund Attribut.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0X8000</td>
<td><p>Unterstrich.</p></td>
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

 

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).

<a name="requirements"></a>Anforderungen
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Unterstützte Mindestversion (Client)</p></td>
<td><p>Windows 2000 Professional [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows 2000 Server [nur Desktop-Apps]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>WinCon. h (Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**"Read consoleoutput"**](readconsoleoutput.md)

[**Scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md)

[**Schreibconsoleoutput**](writeconsoleoutput.md)

 

 




