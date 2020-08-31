---
title: CONSOLE_SCREEN_BUFFER_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_SCREEN_BUFFER_INFO Struktur, die Informationen zu einem Konsolenbildschirm Puffer enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4089541ddac93f5be61b7a21d5aa88a88061b261
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060051"
---
# <a name="console_screen_buffer_info-structure"></a>Konsolen \_ Bildschirm- \_ Puffer \_ Info Struktur


Enthält Informationen zu einem Konsolenbildschirm Puffer.

<a name="syntax"></a>Syntax
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

<a name="members"></a>Member
-------

**dwSize**  
Eine [**Koord**](coord-str.md) -Struktur, die die Größe des Konsolenbildschirm Puffers in Zeichen Spalten und Zeilen enthält.

**dwcurrsorposition**  
Eine [**Koord**](coord-str.md) -Struktur, die die Spalten-und Zeilen Koordinaten des Cursors im Konsolenbildschirm Puffer enthält.

**wattributes**  
Die Attribute der Zeichen, die von den Funktionen " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " und " [**Write-Console**](writeconsole.md) " in einen Bildschirm Puffer geschrieben wurden oder von den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und "read [**Console**](readconsole.md) " auf einen Bildschirm Puffer gespiegelt werden. Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).

**srwindow**  
Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die Konsolenbildschirm Puffer Koordinaten der oberen linken und unteren rechten Ecke des Anzeige Fensters enthält.

**dwmaximumwindowsize**  
Eine [**Koord**](coord-str.md) -Struktur, die die maximale Größe des Konsolenfensters in Zeichen Spalten und Zeilen enthält, wenn die aktuelle Bildschirm Puffergröße und-Schriftart und die Bildschirmgröße angegeben sind.

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
<td>ConsoleApi2. h (über WinCon. h, Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Koord**](coord-str.md)

[**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)

[**"Read Console"**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**kleine \_ Rect**](small-rect-str.md)

[**Schreib Konsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




