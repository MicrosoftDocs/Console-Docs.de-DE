---
title: KEY_EVENT_RECORD-Struktur
description: Beschreibt ein Tastatureingabe Ereignis in einer Konsolen Eingabe \_ Daten Satzstruktur.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/KEY_EVENT_RECORD
- wincon/KEY_EVENT_RECORD
- KEY_EVENT_RECORD
- wincontypes/PKEY_EVENT_RECORD
- wincon/PKEY_EVENT_RECORD
- PKEY_EVENT_RECORD
MS-HAID:
- '\_win32\_key\_event\_record\_str'
- base.key\_event\_record\_str
- consoles.key\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b3fed86b-84ef-48e4-97e1-cb3d65f714a7
topic_type:
- apiref
api_name:
- KEY_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: bcc58b90e71b848e3b6e4b0bf5ba162323830529
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357800"
---
# <a name="key_event_record-structure"></a>Struktur des Schlüssel \_ Ereignis \_ Datensatzes

Beschreibt ein Tastatureingabe Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.

## <a name="syntax"></a>Syntax

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

## <a name="members"></a>Member

**bkeydown**  
Wenn die Taste gedrückt wird, ist dieser Member " **true**". Andernfalls ist dieser Member **false** (der Schlüssel wird freigegeben).

**wrepeatcount**  
Der Wiederholungs Zähler, der angibt, dass ein Schlüssel angehalten wird. Wenn eine Taste z. b. angehalten wird, können fünf Ereignisse mit diesem Element gleich 1, ein Ereignis mit diesem Element gleich 5 oder mehrere Ereignisse mit diesem Member größer oder gleich 1 sein.

**wvirtualkeycode**  
Ein [Code für den virtuellen Schlüssel](/windows/win32/inputdev/virtual-key-codes) , der den angegebenen Schlüssel Geräte unabhängig identifiziert.

**wvirtualscancode**  
Der virtuelle Scan Code des angegebenen Schlüssels, der den von der Tastatur Hardware generierten geräteabhängigen Wert darstellt.

**uChar**  
Eine Union der folgenden Member.

**Unicodechar**  
Übersetzte Unicode-Zeichen.

**Asciichar**  
Übersetzte ASCII-Zeichen.

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

## <a name="remarks"></a>Bemerkungen

Erweiterte Schlüssel für die Tastaturen IBM® 101-und 102-Key sind die Tasten in, del, Home, End, page up, Page Down und Direction in den Clustern links neben der Tastatur. und die Unterteilung (/) und EINGABETASTE in der Tastatur.

Tastatureingabe Ereignisse werden generiert, wenn ein beliebiger Schlüssel, einschließlich der Steuerelement Schlüssel, gedrückt oder freigegeben wird. Die Alt-Taste, wenn Sie gedrückt und freigegeben wird, ohne mit einem anderen Zeichen zu kombinieren, hat jedoch eine besondere Bedeutung für das System und wird nicht an die Anwendung übermittelt. Außerdem wird die Tastenkombination STRG + C nicht durchlaufen, wenn sich das Eingabe Handle im verarbeiteten Modus befindet **( \_ verarbeitete \_ Eingaben aktivieren**).

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen von Eingabepufferereignissen](reading-input-buffer-events.md).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | Wincontypes. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)