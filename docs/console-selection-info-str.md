---
title: CONSOLE_SELECTION_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_SELECTION_INFO Struktur, die Informationen zu einer Konsolen Auswahl enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038368"
---
# <a name="console_selection_info-structure"></a>Konsolen \_ Auswahl \_ Info-Struktur

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Enthält Informationen für eine Konsolen Auswahl.

## <a name="syntax"></a>Syntax

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a>Member

**dwFlags**  
Der Auswahl Indikator. Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **CONSOLE_MOUSE_DOWN** 0x0008 | Die Maus ist nicht gedrückt. Der Benutzer passt das Auswahl Rechteck aktiv mit der Maus an. |
| **CONSOLE_MOUSE_SELECTION** 0x0004 | Auswählen mit der Maus. Wenn OFF, wird der Benutzer im Betriebs `conhost.exe` markermodus mit der Tastatur ausgewählt. |
| **CONSOLE_NO_SELECTION** 0x0000 | Keine Auswahl. |
| **CONSOLE_SELECTION_IN_PROGRESS** 0x0001 | Die Auswahl wurde begonnen. Bei einer Maus Auswahl tritt dies in der Regel nicht ohne das- `CONSOLE_SELECTION_NOT_EMPTY` Flag auf. Bei einer Tastaturauswahl kann dies vorkommen, wenn der Markierungs Modus eingegeben wurde, der Benutzer aber immer noch zur ursprünglichen Position navigiert. |
| **CONSOLE_SELECTION_NOT_EMPTY** 0x0002 | Auswahl Rechteck ist nicht leer. Die Nutzlast von *dwselectionanchor* und *srselection* ist gültig.  |

**dwselectionanchor**  
Eine [**Koord**](coord-str.md) -Struktur, die den Auswahl Anker in Zeichen angibt.

**srselection**  
Eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die das Auswahl Rechteck angibt.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows XP \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2003 \[ -Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**Koord**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**kleine \_ Rect**](small-rect-str.md)
