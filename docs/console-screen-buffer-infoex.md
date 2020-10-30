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
ms.openlocfilehash: baf6eeb51cbae5ce410c190852c22ae237e6a367
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038348"
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
Die Attribute der Zeichen, die von den Funktionen " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " und " [**Write-Console**](writeconsole.md) " in einen Bildschirm Puffer geschrieben wurden oder von den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und "read [**Console**](readconsole.md) " auf einen Bildschirm Puffer gespiegelt werden. Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).

**srwindow**  
Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die Konsolenbildschirm Puffer Koordinaten der oberen linken und unteren rechten Ecke des Anzeige Fensters enthält.

**dwmaximumwindowsize**  
Eine [**Koord**](coord-str.md) -Struktur, die die maximale Größe des Konsolenfensters in Zeichen Spalten und Zeilen enthält, wenn die aktuelle Bildschirm Puffergröße und-Schriftart und die Bildschirmgröße angegeben sind.

**wpopupattribute**  
Das Füll Attribut für Konsolen-Popups.

**bfullscreensupported**  
Wenn dieser Member ist `TRUE` , wird der Vollbildmodus unterstützt, andernfalls ist dies nicht der Fall. Dabei handelt es sich immer `FALSE` um Systeme nach Windows Vista mit dem [WDDM-Treibermodell](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , da der echte direkte VGA-Zugriff auf den Monitor nicht mehr möglich ist.

**ColorTable**  
Ein Array von [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) -Werten, die die Farbeinstellungen der Konsole beschreiben.

## <a name="requirements"></a>Requirements (Anforderungen)

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
