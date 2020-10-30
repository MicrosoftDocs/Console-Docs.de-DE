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
# <a name="input_record-structure"></a><span data-ttu-id="8add2-104">Eingabe \_ Daten Satzstruktur</span><span class="sxs-lookup"><span data-stu-id="8add2-104">INPUT\_RECORD structure</span></span>

<span data-ttu-id="8add2-105">Beschreibt ein Eingabe Ereignis im Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="8add2-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="8add2-106">Diese Datensätze können mithilfe der Funktion " [**leseconsoleinput**](readconsoleinput.md) " oder "Peer- [**ConsoleInput**](peekconsoleinput.md) " aus dem Eingabepuffer gelesen oder mithilfe der Funktion " [**Write ConsoleInput**](writeconsoleinput.md) " in den Eingabepuffer geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="8add2-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="8add2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8add2-107">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="8add2-108">Member</span><span class="sxs-lookup"><span data-stu-id="8add2-108">Members</span></span>

<span data-ttu-id="8add2-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="8add2-109">**EventType**</span></span>  
<span data-ttu-id="8add2-110">Ein Handle für den Typ des Eingabe Ereignisses und den Ereignisdaten Satz, der im **Ereignismember** gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="8add2-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="8add2-111">Dieser Member kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="8add2-111">This member can be one of the following values.</span></span>

| <span data-ttu-id="8add2-112">Wert</span><span class="sxs-lookup"><span data-stu-id="8add2-112">Value</span></span> | <span data-ttu-id="8add2-113">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="8add2-113">Meaning</span></span> |
|-|-|
| <span data-ttu-id="8add2-114">**FOCUS_EVENT** 0x0010</span><span class="sxs-lookup"><span data-stu-id="8add2-114">**FOCUS_EVENT** 0x0010</span></span> | <span data-ttu-id="8add2-115">Das **Ereignismember** enthält eine **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** Struktur.</span><span class="sxs-lookup"><span data-stu-id="8add2-115">The **Event** member contains a **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** structure.</span></span> <span data-ttu-id="8add2-116">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="8add2-116">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="8add2-117">**KEY_EVENT** 0x0001</span><span class="sxs-lookup"><span data-stu-id="8add2-117">**KEY_EVENT** 0x0001</span></span> | <span data-ttu-id="8add2-118">Das **Ereignismember** enthält eine **[KEY_EVENT_RECORD](key-event-record-str.md)** -Struktur mit Informationen über ein Tastaturereignis.</span><span class="sxs-lookup"><span data-stu-id="8add2-118">The **Event** member contains a **[KEY_EVENT_RECORD](key-event-record-str.md)** structure with information about a keyboard event.</span></span> |
| <span data-ttu-id="8add2-119">**MENU_EVENT** 0x0008</span><span class="sxs-lookup"><span data-stu-id="8add2-119">**MENU_EVENT** 0x0008</span></span> | <span data-ttu-id="8add2-120">Das **Ereignismember** enthält eine **[MENU_EVENT_RECORD](menu-event-record-str.md)** Struktur.</span><span class="sxs-lookup"><span data-stu-id="8add2-120">The **Event** member contains a **[MENU_EVENT_RECORD](menu-event-record-str.md)** structure.</span></span> <span data-ttu-id="8add2-121">Diese Ereignisse werden intern verwendet und sollten ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="8add2-121">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="8add2-122">**MOUSE_EVENT** 0x0002</span><span class="sxs-lookup"><span data-stu-id="8add2-122">**MOUSE_EVENT** 0x0002</span></span> | <span data-ttu-id="8add2-123">Das **Ereignismember** enthält eine **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** -Struktur mit Informationen über eine Mausbewegung oder ein Schaltflächen-Press Ereignis.</span><span class="sxs-lookup"><span data-stu-id="8add2-123">The **Event** member contains a **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** structure with information about a mouse movement or button press event.</span></span> |
| <span data-ttu-id="8add2-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span><span class="sxs-lookup"><span data-stu-id="8add2-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span></span> | <span data-ttu-id="8add2-125">Das **Ereignismember** enthält eine **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** Struktur mit Informationen zur neuen Größe des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="8add2-125">The **Event** member contains a **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** structure with information about the new size of the console screen buffer.</span></span> |

<span data-ttu-id="8add2-126">**Event**</span><span class="sxs-lookup"><span data-stu-id="8add2-126">**Event**</span></span>  
<span data-ttu-id="8add2-127">Die Ereignisinformationen.</span><span class="sxs-lookup"><span data-stu-id="8add2-127">The event information.</span></span> <span data-ttu-id="8add2-128">Das Format dieses Members hängt von dem Ereignistyp ab, der vom **eventType** -Member angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8add2-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

## <a name="examples"></a><span data-ttu-id="8add2-129">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8add2-129">Examples</span></span>

<span data-ttu-id="8add2-130">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="8add2-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="8add2-131">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="8add2-131">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8add2-132">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="8add2-132">Minimum supported client</span></span> | <span data-ttu-id="8add2-133">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="8add2-133">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="8add2-134">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="8add2-134">Minimum supported server</span></span> | <span data-ttu-id="8add2-135">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="8add2-135">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="8add2-136">Header</span><span class="sxs-lookup"><span data-stu-id="8add2-136">Header</span></span> | <span data-ttu-id="8add2-137">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8add2-137">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="8add2-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8add2-138">See also</span></span>

[<span data-ttu-id="8add2-139">**Fokus \_ Ereignis \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="8add2-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="8add2-140">**Key- \_ Ereignis \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="8add2-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="8add2-141">**Menü \_ Ereignis \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="8add2-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="8add2-142">**\_Ereignis \_ Daten Satz für Maus**</span><span class="sxs-lookup"><span data-stu-id="8add2-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="8add2-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8add2-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="8add2-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8add2-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="8add2-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8add2-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
