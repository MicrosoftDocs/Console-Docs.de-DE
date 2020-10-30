---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT-Struktur
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 93121864c8754b281b92051a5e4a174b2d5956a3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037098"
---
# <a name="small_rect-structure"></a>Kleine \_ Rect-Struktur

Definiert die Koordinaten der oberen linken und unteren rechten Ecke eines Rechtecks.

## <a name="syntax"></a>Syntax

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a>Member

**Left**  
Die x-Koordinate der oberen linken Ecke des Rechtecks.

**Top**  
Die y-Koordinate der oberen linken Ecke des Rechtecks.

**Right**  
Die x-Koordinate der unteren rechten Ecke des Rechtecks.

**bottom**  
Die y-Koordinate der unteren rechten Ecke des Rechtecks.

## <a name="remarks"></a>Bemerkungen

Diese Struktur wird von Konsolenfunktionen verwendet, um rechteckige Bereiche von Konsolenbildschirm Puffern anzugeben, wobei die Koordinaten die Zeilen und Spalten von Bildschirm Puffer Zeichen Zellen angeben.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Wincontypes. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**Rect**](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[**RECTL**](https://msdn.microsoft.com/library/windows/desktop/dd162907)
