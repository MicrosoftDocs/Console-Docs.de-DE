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
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357850"
---
# `CHAR\_INFO structure`

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
| **FOREGROUND_BLUE**`0x0001` | Die Textfarbe enthält Blau. |
| **FOREGROUND_GREEN**`0x0002` | Die Textfarbe enthält Grün. |
| **FOREGROUND_RED**`0x0004` | Die Textfarbe enthält Rot. |
| **FOREGROUND_INTENSITY**`0x0008` | Die Textfarbe wird verstärkt. |
| **BACKGROUND_BLUE**`0x0010` | Die Hintergrundfarbe enthält Blau. |
| **BACKGROUND_GREEN**`0x0020` | Die Hintergrundfarbe enthält Grün. |
| **BACKGROUND_RED**`0x0040` | Die Hintergrundfarbe enthält Rot. |
| **BACKGROUND_INTENSITY**`0x0080` | Die Hintergrundfarbe wird verstärkt. |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | Führendes Byte. |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | Schließendes Byte. |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | Oben horizontal. |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | Links vertikal. |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | Rechts vertikal. |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | Umgekehrtes Vordergrund-und Hintergrund Attribut. |
| **COMMON_LVB_UNDERSCORE**`0x8000` | Unterstrich. |

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | WinCon. h (Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
