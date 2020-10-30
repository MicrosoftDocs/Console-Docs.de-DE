---
title: CONSOLE_FONT_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_FONT_INFO Struktur, die den Index und die Größe einer Konsolen Schriftart enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037138"
---
# <a name="console_font_info-structure"></a>Struktur der Konsolen \_ Schriftart \_ Info

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Enthält Informationen für eine Konsolen Schriftart.

## <a name="syntax"></a>Syntax

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a>Member

**nschriftart**  
Der Index der Schriftart in der Konsolen Schriftart Tabelle des Systems.

**dwfontsize**  
Eine [**Koord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält. Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.

## <a name="remarks"></a>Bemerkungen

Um die Größe der Schriftart zu erhalten, übergeben Sie den Schriftart Index an die [**getconsolefontsize**](getconsolefontsize.md) -Funktion.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows XP \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2003 \[ -Desktop-Apps\] |
| Header | WinCon. h (Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**Koord**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)
