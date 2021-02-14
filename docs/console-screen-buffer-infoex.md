---
title: CONSOLE_SCREEN_BUFFER_INFOEX-Struktur
description: Siehe Referenzinformationen zur CONSOLE_SCREEN_BUFFER_INFOEX Struktur, die erweiterte Informationen zu einem Konsolenbildschirm Puffer enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 1e4e30601655190bc6f597bbd33dd99f14f8d488
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358081"
---
# <a name="console_screen_buffer_infoex-structure"></a>Konsolen \_ Bildschirm- \_ Puffer- \_ INFOEX-Struktur

Enthält erweiterte Informationen zu einem Konsolenbildschirm Puffer.

## <a name="syntax"></a>Syntax

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a>Member

**CBSIZE**  
Die Größe der-Struktur in Bytes.

**dwSize**  
Eine [**Koord**](coord-str.md) -Struktur, die die Größe des Konsolenbildschirm Puffers in Zeichen Spalten und Zeilen enthält.

**dwcurrsorposition**  
Eine [**Koord**](coord-str.md) -Struktur, die die Spalten-und Zeilen Koordinaten des Cursors im Konsolenbildschirm Puffer enthält.

**wattributes**  
Die Attribute der Zeichen, die von den Funktionen " [**Write File**](/windows/win32/api/fileapi/nf-fileapi-writefile) " und " [**Write-Console**](writeconsole.md) " in einen Bildschirm Puffer geschrieben wurden oder von den Funktionen "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) " und "read [**Console**](readconsole.md) " auf einen Bildschirm Puffer gespiegelt werden. Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).

**srwindow**  
Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die Konsolenbildschirm Puffer Koordinaten der oberen linken und unteren rechten Ecke des Anzeige Fensters enthält.

**dwmaximumwindowsize**  
Eine [**Koord**](coord-str.md) -Struktur, die die maximale Größe des Konsolenfensters in Zeichen Spalten und Zeilen enthält, wenn die aktuelle Bildschirm Puffergröße und-Schriftart und die Bildschirmgröße angegeben sind.

**wpopupattribute**  
Das Füll Attribut für Konsolen-Popups.

**bfullscreensupported**  
Wenn dieser Member ist `TRUE` , wird der Vollbildmodus unterstützt, andernfalls ist dies nicht der Fall. Dabei handelt es sich immer `FALSE` um Systeme nach Windows Vista mit dem [WDDM-Treibermodell](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , da der echte direkte VGA-Zugriff auf den Monitor nicht mehr möglich ist.

**ColorTable**  
Ein Array von [**COLORREF**](/windows/win32/gdi/colorref) -Werten, die die Farbeinstellungen der Konsole beschreiben.

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**Koord**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**kleine \_ Rect**](small-rect-str.md)