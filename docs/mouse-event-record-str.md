---
title: MOUSE_EVENT_RECORD-Struktur
description: Siehe Referenzinformationen zur MOUSE_EVENT_RECORD Struktur, die ein Mauseingabe Ereignis in einer Konsolen INPUT_RECORD Struktur beschreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038518"
---
# <a name="mouse_event_record-structure"></a>\_ \_ Daten Satzstruktur des Maus Ereignisses

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Beschreibt ein Mauseingabe Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.

## <a name="syntax"></a>Syntax

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a>Member

**dwmoupositionposition**  
Eine [**Koord**](coord-str.md) -Struktur, die die Position des Cursors in Bezug auf die Zeichen Zell Koordinaten des Konsolenbildschirm Puffers enthält.

**dwbuttonstate**  
Der Status der Maustasten. Das unwichtigste Bit entspricht der linken Maustaste. Das nächste signifikanteste Bit entspricht der rechten Maustaste. Das nächste Bit gibt die nächste Maustaste an. Die Bits entsprechen dann den Maustasten von links nach rechts. Ein Bit ist 1, wenn die Schaltfläche gedrückt wurde.

Die folgenden Konstanten werden für die ersten fünf Maustasten definiert.

| Wert | Bedeutung |
|-|-|
| **FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001 | Die linke Maustaste. |
| **FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004 | Die zweite Schaltfläche der linken Seite. |
| **FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008 | Die dritte Schaltfläche von Links. |
| **FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010 | Die vierte Schaltfläche von Links. |
| **RIGHTMOST_BUTTON_PRESSED** 0x0002 | Die Rechte Maustaste. |

**dwcontrolkeystate**  
Der Zustand der Steuerelement Schlüssel. Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **CAPSLOCK_ON** 0x0080 | Die Feststell Sperre ist auf on. |
| **ENHANCED_KEY** 0x0100 | Der Schlüssel ist erweitert. Siehe [Hinweise](key-event-record-str.md#remarks). |
| **LEFT_ALT_PRESSED** 0x0002 | Die linke ALT-Taste wird gedrückt. |
| **LEFT_CTRL_PRESSED** 0x0008 | Die linke STRG-Taste wird gedrückt. |
| **NUMLOCK_ON** 0x0020 | Der NUM-Sperr Licht ist on. |
| **RIGHT_ALT_PRESSED** 0x0001 | Die Rechte ALT-Taste wird gedrückt. |
| **RIGHT_CTRL_PRESSED** 0x0004 | Die Rechte STRG-Taste wird gedrückt. |
| **SCROLLLOCK_ON** 0x0040 | Das Licht der Scrollsperre ist on. |
| **SHIFT_PRESSED** 0x0010 | Die UMSCHALTTASTE wird gedrückt. |

**dweventflags**  
Der Typ des Maus Ereignisses. Wenn dieser Wert 0 (null) ist, gibt er an, dass eine Maustaste gedrückt oder losgelassen wird. Andernfalls ist dieser Member einer der folgenden Werte.

| Wert | Bedeutung |
|-|-|
| **DOUBLE_CLICK** 0x0002 | Der zweite Klick (Schaltflächen-Taste) mit einem Doppelklick ist aufgetreten. Der erste Klick wird als reguläres Button-Press-Ereignis zurückgegeben. |
| **MOUSE_HWHEELED** 0x0008 | Das horizontale Mausrad wurde verschoben.<br /><br />Wenn das hohe Wort des **dwbuttonstate** -Members einen positiven Wert enthält, wurde das Rad nach rechts gedreht. Andernfalls wurde das Rad nach links gedreht. |
| **MOUSE_MOVED** 0x0001 | Eine Änderung der Mausposition ist aufgetreten. |
| **MOUSE_WHEELED** 0x0004 | Das vertikale Mausrad wurde verschoben.<br /><br />Wenn das hohe Wort des **dwbuttonstate** -Members einen positiven Wert enthält, wurde das Rad vom Benutzer entfernt. Andernfalls wurde das Rad für den Benutzer rückwärts gedreht. |

## <a name="remarks"></a>Bemerkungen

Mausereignisse werden in den Eingabepuffer eingefügt, wenn sich die Konsole im Mausmodus befindet ( **\_ Maus \_ Eingabe aktivieren** ).

Mausereignisse werden generiert, wenn der Benutzer die Maus bewegt oder eine der Maustasten drückt oder freigibt. Mausereignisse werden nur dann in den Eingabepuffer einer Konsole eingefügt, wenn die Konsolen Gruppe den Tastaturfokus besitzt und sich der Cursor innerhalb der Rahmen des Konsolenfensters befindet.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Wincontypes. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**Koord**](coord-str.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
