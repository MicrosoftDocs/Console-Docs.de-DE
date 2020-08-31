---
title: CONSOLE_CURSOR_INFO Struktur
description: Enthält die Größe und Sichtbarkeits Informationen über den Konsolen Cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0ac3eb459810f2c8ebc861759312350a487abd3c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060131"
---
# <a name="console_cursor_info-structure"></a>Konsolen \_ Cursor- \_ Informationsstruktur


Enthält Informationen über den Konsolen Cursor.

<a name="syntax"></a>Syntax
------

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

<a name="members"></a>Member
-------

**dwSize**  
Der Prozentsatz der Zeichen Zelle, die vom Cursor ausgefüllt wird. Dieser Wert liegt zwischen 1 und 100. Die Cursor Darstellung variiert, reicht von der vollständigen Füllung der Zelle bis zum erscheinen als horizontale Linie am unteren Rand der Zelle.

**Hinweis**    Während der **dwSize** -Wert normalerweise zwischen 1 und 100 liegt, kann unter bestimmten Umständen ein Wert außerhalb dieses Bereichs zurückgegeben werden. Wenn z. b. " **Cursor size** " in der Registrierung auf "0" festgelegt ist, wäre der zurückgegebene **dwSize** -Wert 0 (null).

 

**bvisible**  
Die Sichtbarkeit des Cursors. Wenn der Cursor sichtbar ist, ist dieser Member " **true**".

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


[**Getconsolecursorinfo**](getconsolecursorinfo.md)

[**Setconsolecursorinfo**](setconsolecursorinfo.md)

 

 




