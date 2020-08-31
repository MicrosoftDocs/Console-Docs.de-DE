---
title: CONSOLE_SCREEN_BUFFER_INFOEX Struktur
description: Siehe Referenzinformationen zur CONSOLE_SCREEN_BUFFER_INFOEX Struktur, die erweiterte Informationen zu einem Konsolenbildschirm Puffer enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 010120f2d925727e37bd72905bab4536db073371
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060050"
---
# <a name="console_screen_buffer_infoex-structure"></a>Konsolen \_ Bildschirm- \_ Puffer- \_ INFOEX-Struktur


Enthält erweiterte Informationen zu einem Konsolenbildschirm Puffer.

<a name="syntax"></a>Syntax
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

<a name="members"></a>Member
-------

**CBSIZE**  
Die Größe der-Struktur in Bytes.

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

**wpopupattribute**  
Das Füll Attribut für Konsolen-Popups.

**bfullscreensupported**  
Wenn dieser Member true ist, wird der Vollbildmodus unterstützt. Andernfalls ist dies nicht der Fall.

**ColorTable**  
Ein Array von [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) -Werten, die die Farbeinstellungen der Konsole beschreiben.

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
<td><p>Windows Vista [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2008 [nur Desktop-Apps]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>ConsoleApi2. h (über WinCon. h, Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Koord**](coord-str.md)

[**Getconsoleskreenbufferinfoex**](getconsolescreenbufferinfoex.md)

[**Setconsoleskreenbufferinfoex**](setconsolescreenbufferinfoex.md)

[**kleine \_ Rect**](small-rect-str.md)

 

 




