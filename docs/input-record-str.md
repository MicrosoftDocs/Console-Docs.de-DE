---
title: INPUT_RECORD-Struktur
description: Siehe Referenzinformationen zur INPUT_RECORD Struktur, die ein Eingabe Ereignis im Konsolen Eingabepuffer beschreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038538"
---
# <a name="input_record-structure"></a>Eingabe \_ Daten Satzstruktur

Beschreibt ein Eingabe Ereignis im Konsolen Eingabepuffer. Diese Datensätze können mithilfe der Funktion " [**leseconsoleinput**](readconsoleinput.md) " oder "Peer- [**ConsoleInput**](peekconsoleinput.md) " aus dem Eingabepuffer gelesen oder mithilfe der Funktion " [**Write ConsoleInput**](writeconsoleinput.md) " in den Eingabepuffer geschrieben werden.

## <a name="syntax"></a>Syntax

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a>Member

**EventType**  
Ein Handle für den Typ des Eingabe Ereignisses und den Ereignisdaten Satz, der im **Ereignismember** gespeichert ist.

Dieser Member kann einen der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **FOCUS_EVENT** 0x0010 | Das **Ereignismember** enthält eine **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** Struktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden. |
| **KEY_EVENT** 0x0001 | Das **Ereignismember** enthält eine **[KEY_EVENT_RECORD](key-event-record-str.md)** -Struktur mit Informationen über ein Tastaturereignis. |
| **MENU_EVENT** 0x0008 | Das **Ereignismember** enthält eine **[MENU_EVENT_RECORD](menu-event-record-str.md)** Struktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden. |
| **MOUSE_EVENT** 0x0002 | Das **Ereignismember** enthält eine **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** -Struktur mit Informationen über eine Mausbewegung oder ein Schaltflächen-Press Ereignis. |
| **WINDOW_BUFFER_SIZE_EVENT** 0x0004 | Das **Ereignismember** enthält eine **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** Struktur mit Informationen zur neuen Größe des Konsolenbildschirm Puffers. |

**Event**  
Die Ereignisinformationen. Das Format dieses Members hängt von dem Ereignistyp ab, der vom **eventType** -Member angegeben wird.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Wincontypes. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**Fokus \_ Ereignis \_ Daten Satz**](focus-event-record-str.md)

[**Key- \_ Ereignis \_ Daten Satz**](key-event-record-str.md)

[**Menü \_ Ereignis \_ Daten Satz**](menu-event-record-str.md)

[**\_Ereignis \_ Daten Satz für Maus**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
