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
# <a name="console_font_info-structure"></a>Struktur der Konsolen \_ Schriftart \_ Info


Enthält Informationen für eine Konsolen Schriftart.

<a name="syntax"></a>Syntax
------

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

<a name="members"></a>Member
-------

**nschriftart**  
Der Index der Schriftart in der Konsolen Schriftart Tabelle des Systems.

**dwfontsize**  
Eine [**Koord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält. Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.

<a name="remarks"></a>Hinweise
-------

Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.

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
<td><p>Windows XP [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2003 [nur Desktop-Apps]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>WinCon. h (Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Koord**](coord-str.md)

[**Getcurrentconsolefont**](getcurrentconsolefont.md)

 

 




