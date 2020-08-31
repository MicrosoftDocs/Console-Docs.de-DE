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
# <a name="input_record-structure"></a><span data-ttu-id="a9dd7-104">Eingabe \_ Daten Satzstruktur</span><span class="sxs-lookup"><span data-stu-id="a9dd7-104">INPUT\_RECORD structure</span></span>


<span data-ttu-id="a9dd7-105">Beschreibt ein Eingabe Ereignis im Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="a9dd7-106">Diese Datensätze können mithilfe der Funktion " [**leseconsoleinput**](readconsoleinput.md) " oder "Peer- [**ConsoleInput**](peekconsoleinput.md) " aus dem Eingabepuffer gelesen oder mithilfe der Funktion " [**Write ConsoleInput**](writeconsoleinput.md) " in den Eingabepuffer geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="a9dd7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a9dd7-107">Syntax</span></span>
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

<a name="members"></a><span data-ttu-id="a9dd7-108">Member</span><span class="sxs-lookup"><span data-stu-id="a9dd7-108">Members</span></span>
-------

<span data-ttu-id="a9dd7-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-109">**EventType**</span></span>  
<span data-ttu-id="a9dd7-110">Ein Handle für den Typ des Eingabe Ereignisses und den Ereignisdaten Satz, der im **Ereignismember** gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="a9dd7-111">Dieser Member kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-111">This member can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="a9dd7-112">Wert</span><span class="sxs-lookup"><span data-stu-id="a9dd7-112">Value</span></span></th>
<th><span data-ttu-id="a9dd7-113">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="a9dd7-113">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="a9dd7-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="a9dd7-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="a9dd7-115">Das <strong>Ereignismember</strong> enthält eine <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> Struktur.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-115">The <strong>Event</strong> member contains a <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="a9dd7-116">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-116">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a9dd7-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="a9dd7-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="a9dd7-118">Das <strong>Ereignismember</strong> enthält eine <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> -Struktur mit Informationen über ein Tastaturereignis.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-118">The <strong>Event</strong> member contains a <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> structure with information about a keyboard event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a9dd7-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="a9dd7-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="a9dd7-120">Das <strong>Ereignismember</strong> enthält eine <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> Struktur.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-120">The <strong>Event</strong> member contains a <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="a9dd7-121">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-121">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a9dd7-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="a9dd7-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="a9dd7-123">Das <strong>Ereignismember</strong> enthält eine <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> -Struktur mit Informationen über eine Mausbewegung oder ein Schaltflächen-Press Ereignis.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-123">The <strong>Event</strong> member contains a <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> structure with information about a mouse movement or button press event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a9dd7-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="a9dd7-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="a9dd7-125">Das <strong>Ereignismember</strong> enthält eine <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> Struktur mit Informationen zur neuen Größe des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-125">The <strong>Event</strong> member contains a <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> structure with information about the new size of the console screen buffer.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="a9dd7-126">**Event**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-126">**Event**</span></span>  
<span data-ttu-id="a9dd7-127">Die Ereignisinformationen.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-127">The event information.</span></span> <span data-ttu-id="a9dd7-128">Das Format dieses Members hängt von dem Ereignistyp ab, der vom **eventType** -Member angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a9dd7-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

<a name="examples"></a><span data-ttu-id="a9dd7-129">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a9dd7-129">Examples</span></span>
--------

<span data-ttu-id="a9dd7-130">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="a9dd7-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="a9dd7-131">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a9dd7-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a9dd7-132">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="a9dd7-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a9dd7-133">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="a9dd7-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a9dd7-134">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="a9dd7-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a9dd7-135">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="a9dd7-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a9dd7-136">Header</span><span class="sxs-lookup"><span data-stu-id="a9dd7-136">Header</span></span></p></td>
<td><span data-ttu-id="a9dd7-137">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a9dd7-137">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a9dd7-138"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a9dd7-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a9dd7-139">**Fokus \_ Ereignis \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="a9dd7-140">**Key- \_ Ereignis \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="a9dd7-141">**Menü \_ Ereignis \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="a9dd7-142">**\_Ereignis \_ Daten Satz für Maus**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="a9dd7-143">**"Etekconsoleinput"**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="a9dd7-144">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="a9dd7-145">**Schreibconsoleinput**</span><span class="sxs-lookup"><span data-stu-id="a9dd7-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




