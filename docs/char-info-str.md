---
title: CHAR_INFO Struktur
description: Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an. Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037378"
---
# <a name="char_info-structure"></a>Char \_ Info-Struktur

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an. Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.

## <a name="syntax"></a>Syntax

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a>Member

**Char**  
Eine Union der folgenden Member.

**Unicodechar**  
Unicode-Zeichen einer Bildschirm Puffer-Zeichen Zelle.

**Asciichar**  
ANSI-Zeichen einer Bildschirm Puffer-Zeichen Zelle.

**Attribute**  
Die Zeichen Attribute. Dieser Member kann NULL oder eine beliebige Kombination der folgenden Werte sein.

| Wert | Bedeutung |
|-|-|
| **FOREGROUND_BLUE**`0x0001` | Textfarbe enthält blau. |
| **FOREGROUND_GREEN**`0x0002` | Textfarbe enthält grün. |
| **FOREGROUND_RED**`0x0004` | Textfarbe enthält rot. |
| **FOREGROUND_INTENSITY**`0x0008` | Die Textfarbe wird verstärkt. |
| **BACKGROUND_BLUE**`0x0010` | Hintergrundfarbe enthält blau. |
| **BACKGROUND_GREEN**`0x0020` | Hintergrundfarbe enthält grün. |
| **BACKGROUND_RED**`0x0040` | Die Hintergrundfarbe enthält rot. |
| **BACKGROUND_INTENSITY**`0x0080` | Die Hintergrundfarbe wird verstärkt. |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | Führendes Byte. |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | Nachfolgendes Byte. |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | Obere horizontale. |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | Links vertikal. |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | Rechts vertikal. |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | Umgekehrtes Vordergrund-und Hintergrund Attribut. |
| **COMMON_LVB_UNDERSCORE**`0x8000` | Unterstrich. |

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | WinCon. h (Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
