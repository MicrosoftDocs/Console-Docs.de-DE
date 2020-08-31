---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT Struktur
description: Definiert die Koordinaten der oberen linken und unteren rechten Ecke eines Rechtecks.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: b0c0bfe93c85af89c5aaefeda032795de72ed627
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060555"
---
# <a name="small_rect-structure"></a>Kleine \_ Rect-Struktur


Definiert die Koordinaten der oberen linken und unteren rechten Ecke eines Rechtecks.

<a name="syntax"></a>Syntax
------

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

<a name="members"></a>Member
-------

**Left**  
Die x-Koordinate der oberen linken Ecke des Rechtecks.

**Top**  
Die y-Koordinate der oberen linken Ecke des Rechtecks.

**Right**  
Die x-Koordinate der unteren rechten Ecke des Rechtecks.

**Unten**  
Die y-Koordinate der unteren rechten Ecke des Rechtecks.

<a name="remarks"></a>Hinweise
-------

Diese Struktur wird von Konsolenfunktionen verwendet, um rechteckige Bereiche von Konsolenbildschirm Puffern anzugeben, wobei die Koordinaten die Zeilen und Spalten von Bildschirm Puffer Zeichen Zellen angeben.

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
<td>Wincontypes. h (über WinCon. h, Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Rect**](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[**RECTL**](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 




