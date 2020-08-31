---
title: Coord-Struktur
description: Definiert die Koordinaten einer Zeichen Zelle in einem Konsolenbildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059939"
---
# <a name="coord-structure"></a>Coord-Struktur


Definiert die Koordinaten einer Zeichen Zelle in einem Konsolenbildschirm Puffer. Der Ursprung des Koordinatensystems (0,0) befindet sich in der oberen, linken Zelle des Puffers.

<a name="syntax"></a>Syntax
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a>Member
-------

**X**  
Der horizontale Koordinaten-oder Spaltenwert. Die Einheiten sind vom Funktions aufrufsbefehl abhängig.

**J**  
Der vertikale Koordinaten-oder Zeilen Wert. Die Einheiten sind vom Funktions aufrufsbefehl abhängig.

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


[**Informationen zur Konsolen \_ Schriftart \_**](console-font-info-str.md)

[**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**](console-screen-buffer-info-str.md)

[**Konsolen \_ Auswahl \_ Informationen**](console-selection-info-str.md)

[**Fillconsoleoutputattribute**](fillconsoleoutputattribute.md)

[**Fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md)

[**Getconsolefontsize**](getconsolefontsize.md)

[**Getlargestconsolewindowsize**](getlargestconsolewindowsize.md)

[**\_Ereignis \_ Daten Satz für Maus**](mouse-event-record-str.md)

[**"Read consoleoutput"**](readconsoleoutput.md)

[**"Read consoleoutputattribute"**](readconsoleoutputattribute.md)

[**"Read consoleoutputcharacter"**](readconsoleoutputcharacter.md)

[**Scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**Setconsoledisplaymode**](setconsoledisplaymode.md)

[**Setconsoleskreenbuffersize**](setconsolescreenbuffersize.md)

[**Datensatz der Fenster \_ Puffer \_ Größe \_**](window-buffer-size-record-str.md)

[**Schreibconsoleoutput**](writeconsoleoutput.md)

[**"Schreibconsoleoutputattribute"**](writeconsoleoutputattribute.md)

[**Schreibconsoleoutputcharacter**](writeconsoleoutputcharacter.md)

 

 




