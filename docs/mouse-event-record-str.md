---
title: MOUSE_EVENT_RECORD Struktur
description: Siehe Referenzinformationen zur MOUSE_EVENT_RECORD Struktur, die ein Mauseingabe Ereignis in einer Konsolen INPUT_RECORD Struktur beschreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a3e95e9d35cdf2af2ec6836021dd8819323a4790
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059586"
---
# <a name="mouse_event_record-structure"></a>\_ \_ Daten Satzstruktur des Maus Ereignisses


Beschreibt ein Mauseingabe Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.

<a name="syntax"></a>Syntax
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a>Member
-------

**dwmoupositionposition**  
Eine [**Koord**](coord-str.md) -Struktur, die die Position des Cursors in Bezug auf die Zeichen Zell Koordinaten des Konsolenbildschirm Puffers enthält.

**dwbuttonstate**  
Der Status der Maustasten. Das unwichtigste Bit entspricht der linken Maustaste. Das nächste signifikanteste Bit entspricht der rechten Maustaste. Das nächste Bit gibt die nächste Maustaste an. Die Bits entsprechen dann den Maustasten von links nach rechts. Ein Bit ist 1, wenn die Schaltfläche gedrückt wurde.

Die folgenden Konstanten werden für die ersten fünf Maustasten definiert.

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
<td><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</td>
<td><p>Die linke Maustaste.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</td>
<td><p>Die zweite Schaltfläche von Links.</p></td>
</tr>
<tr class="odd">
<td><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</td>
<td><p>Die dritte Schaltfläche von Links.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</td>
<td><p>Die vierte Schaltfläche von Links.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</td>
<td><p>Die Rechte Maustaste.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**dwcontrolkeystate**  
Der Zustand der Steuerelement Schlüssel. Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.

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
<td><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</td>
<td><p>Die Feststell Sperre ist auf on.</p></td>
</tr>
<tr class="even">
<td><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</td>
<td><p>Der Schlüssel ist erweitert.</p></td>
</tr>
<tr class="odd">
<td><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</td>
<td><p>Die linke ALT-Taste wird gedrückt.</p></td>
</tr>
<tr class="even">
<td><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</td>
<td><p>Die linke STRG-Taste wird gedrückt.</p></td>
</tr>
<tr class="odd">
<td><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</td>
<td><p>Der NUM-Sperr Licht ist on.</p></td>
</tr>
<tr class="even">
<td><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</td>
<td><p>Die Rechte ALT-Taste wird gedrückt.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</td>
<td><p>Die Rechte STRG-Taste wird gedrückt.</p></td>
</tr>
<tr class="even">
<td><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</td>
<td><p>Das Licht der Scrollsperre ist on.</p></td>
</tr>
<tr class="odd">
<td><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</td>
<td><p>Die UMSCHALTTASTE wird gedrückt.</p></td>
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

 

**dweventflags**  
Der Typ des Maus Ereignisses. Wenn dieser Wert 0 (null) ist, gibt er an, dass eine Maustaste gedrückt oder losgelassen wird. Andernfalls ist dieser Member einer der folgenden Werte.

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
<td><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</td>
<td><p>Der zweite Klick (Schaltflächen-Taste) mit einem Doppelklick ist aufgetreten. Der erste Klick wird als reguläres Button-Press-Ereignis zurückgegeben.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</td>
<td><p>Das horizontale Mausrad wurde verschoben.</p>
<p>Wenn das hohe Wort des <strong>dwbuttonstate</strong> -Members einen positiven Wert enthält, wurde das Rad nach rechts gedreht. Andernfalls wurde das Rad nach links gedreht.</p></td>
</tr>
<tr class="odd">
<td><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</td>
<td><p>Eine Änderung der Mausposition ist aufgetreten.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</td>
<td><p>Das vertikale Mausrad wurde verschoben.</p>
<p>Wenn das hohe Wort des <strong>dwbuttonstate</strong> -Members einen positiven Wert enthält, wurde das Rad vom Benutzer entfernt. Andernfalls wurde das Rad für den Benutzer rückwärts gedreht.</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a>Hinweise
-------

Mausereignisse werden in den Eingabepuffer eingefügt, wenn sich die Konsole im Mausmodus befindet (** \_ Maus \_ Eingabe aktivieren**).

Mausereignisse werden generiert, wenn der Benutzer die Maus bewegt oder eine der Maustasten drückt oder freigibt. Mausereignisse werden nur dann in den Eingabepuffer einer Konsole eingefügt, wenn die Konsolen Gruppe den Tastaturfokus besitzt und sich der Cursor innerhalb der Rahmen des Konsolenfensters befindet.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

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
<td>Wincontypes. h (über WinCon. h, Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Koord**](coord-str.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)

[**"Etekconsoleinput"**](peekconsoleinput.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**Schreibconsoleinput**](writeconsoleinput.md)

 

 




