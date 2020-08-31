---
title: INPUT_RECORD Struktur
description: Siehe Referenzinformationen zur INPUT_RECORD Struktur, die ein Eingabe Ereignis im Konsolen Eingabepuffer beschreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 5d532b5a009681e650991fd083f7d6ab932a05da
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060434"
---
# <a name="input_record-structure"></a>Eingabe \_ Daten Satzstruktur


Beschreibt ein Eingabe Ereignis im Konsolen Eingabepuffer. Diese Datensätze können mithilfe der Funktion " [**leseconsoleinput**](readconsoleinput.md) " oder "Peer- [**ConsoleInput**](peekconsoleinput.md) " aus dem Eingabepuffer gelesen oder mithilfe der Funktion " [**Write ConsoleInput**](writeconsoleinput.md) " in den Eingabepuffer geschrieben werden.

<a name="syntax"></a>Syntax
------

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

<a name="members"></a>Member
-------

**EventType**  
Ein Handle für den Typ des Eingabe Ereignisses und den Ereignisdaten Satz, der im **Ereignismember** gespeichert ist.

Dieser Member kann einen der folgenden Werte aufweisen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</td>
<td><p>Das <strong>Ereignismember</strong> enthält eine <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> Struktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</p></td>
</tr>
<tr class="even">
<td><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</td>
<td><p>Das <strong>Ereignismember</strong> enthält eine <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> -Struktur mit Informationen über ein Tastaturereignis.</p></td>
</tr>
<tr class="odd">
<td><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</td>
<td><p>Das <strong>Ereignismember</strong> enthält eine <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> Struktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</td>
<td><p>Das <strong>Ereignismember</strong> enthält eine <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> -Struktur mit Informationen über eine Mausbewegung oder ein Schaltflächen-Press Ereignis.</p></td>
</tr>
<tr class="odd">
<td><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</td>
<td><p>Das <strong>Ereignismember</strong> enthält eine <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> Struktur mit Informationen zur neuen Größe des Konsolenbildschirm Puffers.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**Event**  
Die Ereignisinformationen. Das Format dieses Members hängt von dem Ereignistyp ab, der vom **eventType** -Member angegeben wird.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

<a name="requirements"></a>Anforderungen
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Unterstützte Mindestversion (Client)</p></td>
<td><p>Windows 2000 Professional [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows 2000 Server [nur Desktop-Apps]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wincontypes. h (über WinCon. h, Include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Fokus \_ Ereignis \_ Daten Satz**](focus-event-record-str.md)

[**Key- \_ Ereignis \_ Daten Satz**](key-event-record-str.md)

[**Menü \_ Ereignis \_ Daten Satz**](menu-event-record-str.md)

[**\_Ereignis \_ Daten Satz für Maus**](mouse-event-record-str.md)

[**"Etekconsoleinput"**](peekconsoleinput.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**Schreibconsoleinput**](writeconsoleinput.md)

 

 




