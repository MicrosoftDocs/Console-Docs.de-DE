---
title: CONSOLE_CURSOR_INFO Struktur
description: Enthält die Größe und Sichtbarkeits Informationen über den Konsolen Cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037012"
---
# <a name="console_cursor_info-structure"></a>Konsolen \_ Cursor- \_ Informationsstruktur

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Enthält Informationen über den Konsolen Cursor.

## <a name="syntax"></a>Syntax

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a>Member

**dwSize**  
Der Prozentsatz der Zeichen Zelle, die vom Cursor ausgefüllt wird. Dieser Wert liegt zwischen 1 und 100. Die Cursor Darstellung variiert, reicht von der vollständigen Füllung der Zelle bis zum erscheinen als horizontale Linie am unteren Rand der Zelle.

> [!NOTE]
>Während der **dwSize** -Wert normalerweise zwischen 1 und 100 liegt, kann unter bestimmten Umständen ein Wert außerhalb dieses Bereichs zurückgegeben werden. Wenn z. b. " **Cursor size** " in der Registrierung auf "0" festgelegt ist, wäre der zurückgegebene **dwSize** -Wert 0 (null).

 **bvisible**  
Die Sichtbarkeit des Cursors. Wenn der Cursor sichtbar ist, ist dieser Member " **true** ".

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | WinCon. h (Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)
