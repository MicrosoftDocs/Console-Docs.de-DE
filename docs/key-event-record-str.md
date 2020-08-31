---
title: KEY_EVENT_RECORD Struktur
description: Beschreibt ein Tastatureingabe Ereignis in einer Konsolen Eingabe \_ Daten Satzstruktur.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/KEY_EVENT_RECORD
- wincon/KEY_EVENT_RECORD
- KEY_EVENT_RECORD
- wincontypes/PKEY_EVENT_RECORD
- wincon/PKEY_EVENT_RECORD
- PKEY_EVENT_RECORD
MS-HAID:
- '\_win32\_key\_event\_record\_str'
- base.key\_event\_record\_str
- consoles.key\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b3fed86b-84ef-48e4-97e1-cb3d65f714a7
topic_type:
- apiref
api_name:
- KEY_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: fd7386d5796442d34cdaa29fcf52831bc6aa1d78
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060419"
---
# <a name="key_event_record-structure"></a>Struktur des Schlüssel \_ Ereignis \_ Datensatzes


Beschreibt ein Tastatureingabe Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.

<a name="syntax"></a>Syntax
------

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

<a name="members"></a>Member
-------

**bkeydown**  
Wenn die Taste gedrückt wird, ist dieser Member " **true**". Andernfalls ist dieser Member **false** (der Schlüssel wird freigegeben).

**wrepeatcount**  
Der Wiederholungs Zähler, der angibt, dass ein Schlüssel angehalten wird. Wenn eine Taste z. b. angehalten wird, können fünf Ereignisse mit diesem Element gleich 1, ein Ereignis mit diesem Element gleich 5 oder mehrere Ereignisse mit diesem Member größer oder gleich 1 sein.

**wvirtualkeycode**  
Ein [Code für den virtuellen Schlüssel](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) , der den angegebenen Schlüssel Geräte unabhängig identifiziert.

**wvirtualscancode**  
Der virtuelle Scan Code des angegebenen Schlüssels, der den von der Tastatur Hardware generierten geräteabhängigen Wert darstellt.

**uChar**  
Eine Union der folgenden Member.

**Unicodechar**  
Übersetzte Unicode-Zeichen.

**Asciichar**  
Übersetzte ASCII-Zeichen.

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

 

<a name="remarks"></a>Hinweise
-------

Erweiterte Schlüssel für die Tastaturen IBM® 101-und 102-Key sind die Tasten in, del, Home, End, page up, Page Down und Direction in den Clustern links neben der Tastatur. und die Unterteilung (/) und EINGABETASTE in der Tastatur.

Tastatureingabe Ereignisse werden generiert, wenn ein beliebiger Schlüssel, einschließlich der Steuerelement Schlüssel, gedrückt oder freigegeben wird. Die Alt-Taste, wenn Sie gedrückt und freigegeben wird, ohne mit einem anderen Zeichen zu kombinieren, hat jedoch eine besondere Bedeutung für das System und wird nicht an die Anwendung übermittelt. Außerdem wird die Tastenkombination STRG + C nicht durchlaufen, wenn sich das Eingabe Handle im verarbeiteten Modus befindet **( \_ verarbeitete \_ Eingaben aktivieren**).

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


[**"Etekconsoleinput"**](peekconsoleinput.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**Schreibconsoleinput**](writeconsoleinput.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)

 

 




