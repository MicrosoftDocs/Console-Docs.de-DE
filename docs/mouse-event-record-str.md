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
# <a name="mouse_event_record-structure"></a><span data-ttu-id="02a11-104">\_ \_ Daten Satzstruktur des Maus Ereignisses</span><span class="sxs-lookup"><span data-stu-id="02a11-104">MOUSE\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="02a11-105">Beschreibt ein Mauseingabe Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.</span><span class="sxs-lookup"><span data-stu-id="02a11-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="02a11-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="02a11-106">Syntax</span></span>

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="02a11-107">Member</span><span class="sxs-lookup"><span data-stu-id="02a11-107">Members</span></span>

<span data-ttu-id="02a11-108">**dwmoupositionposition**</span><span class="sxs-lookup"><span data-stu-id="02a11-108">**dwMousePosition**</span></span>  
<span data-ttu-id="02a11-109">Eine [**Koord**](coord-str.md) -Struktur, die die Position des Cursors in Bezug auf die Zeichen Zell Koordinaten des Konsolenbildschirm Puffers enthält.</span><span class="sxs-lookup"><span data-stu-id="02a11-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="02a11-110">**dwbuttonstate**</span><span class="sxs-lookup"><span data-stu-id="02a11-110">**dwButtonState**</span></span>  
<span data-ttu-id="02a11-111">Der Status der Maustasten.</span><span class="sxs-lookup"><span data-stu-id="02a11-111">The status of the mouse buttons.</span></span> <span data-ttu-id="02a11-112">Das unwichtigste Bit entspricht der linken Maustaste.</span><span class="sxs-lookup"><span data-stu-id="02a11-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="02a11-113">Das nächste signifikanteste Bit entspricht der rechten Maustaste.</span><span class="sxs-lookup"><span data-stu-id="02a11-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="02a11-114">Das nächste Bit gibt die nächste Maustaste an.</span><span class="sxs-lookup"><span data-stu-id="02a11-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="02a11-115">Die Bits entsprechen dann den Maustasten von links nach rechts.</span><span class="sxs-lookup"><span data-stu-id="02a11-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="02a11-116">Ein Bit ist 1, wenn die Schaltfläche gedrückt wurde.</span><span class="sxs-lookup"><span data-stu-id="02a11-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="02a11-117">Die folgenden Konstanten werden für die ersten fünf Maustasten definiert.</span><span class="sxs-lookup"><span data-stu-id="02a11-117">The following constants are defined for the first five mouse buttons.</span></span>

| <span data-ttu-id="02a11-118">Wert</span><span class="sxs-lookup"><span data-stu-id="02a11-118">Value</span></span> | <span data-ttu-id="02a11-119">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="02a11-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="02a11-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="02a11-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span></span> | <span data-ttu-id="02a11-121">Die linke Maustaste.</span><span class="sxs-lookup"><span data-stu-id="02a11-121">The leftmost mouse button.</span></span> |
| <span data-ttu-id="02a11-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="02a11-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span></span> | <span data-ttu-id="02a11-123">Die zweite Schaltfläche der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="02a11-123">The second button fom the left.</span></span> |
| <span data-ttu-id="02a11-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="02a11-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span></span> | <span data-ttu-id="02a11-125">Die dritte Schaltfläche von Links.</span><span class="sxs-lookup"><span data-stu-id="02a11-125">The third button from the left.</span></span> |
| <span data-ttu-id="02a11-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="02a11-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span></span> | <span data-ttu-id="02a11-127">Die vierte Schaltfläche von Links.</span><span class="sxs-lookup"><span data-stu-id="02a11-127">The fourth button from the left.</span></span> |
| <span data-ttu-id="02a11-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="02a11-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span></span> | <span data-ttu-id="02a11-129">Die Rechte Maustaste.</span><span class="sxs-lookup"><span data-stu-id="02a11-129">The rightmost mouse button.</span></span> |

<span data-ttu-id="02a11-130">**dwcontrolkeystate**</span><span class="sxs-lookup"><span data-stu-id="02a11-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="02a11-131">Der Zustand der Steuerelement Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="02a11-131">The state of the control keys.</span></span> <span data-ttu-id="02a11-132">Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="02a11-132">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="02a11-133">Wert</span><span class="sxs-lookup"><span data-stu-id="02a11-133">Value</span></span> | <span data-ttu-id="02a11-134">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="02a11-134">Meaning</span></span> |
|-|-|
| <span data-ttu-id="02a11-135">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="02a11-135">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="02a11-136">Die Feststell Sperre ist auf on.</span><span class="sxs-lookup"><span data-stu-id="02a11-136">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="02a11-137">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="02a11-137">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="02a11-138">Der Schlüssel ist erweitert.</span><span class="sxs-lookup"><span data-stu-id="02a11-138">The key is enhanced.</span></span> <span data-ttu-id="02a11-139">Siehe [Hinweise](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="02a11-139">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="02a11-140">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="02a11-140">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="02a11-141">Die linke ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="02a11-141">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="02a11-142">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="02a11-142">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="02a11-143">Die linke STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="02a11-143">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="02a11-144">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="02a11-144">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="02a11-145">Der NUM-Sperr Licht ist on.</span><span class="sxs-lookup"><span data-stu-id="02a11-145">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="02a11-146">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="02a11-146">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="02a11-147">Die Rechte ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="02a11-147">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="02a11-148">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="02a11-148">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="02a11-149">Die Rechte STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="02a11-149">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="02a11-150">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="02a11-150">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="02a11-151">Das Licht der Scrollsperre ist on.</span><span class="sxs-lookup"><span data-stu-id="02a11-151">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="02a11-152">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="02a11-152">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="02a11-153">Die UMSCHALTTASTE wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="02a11-153">The SHIFT key is pressed.</span></span> |

<span data-ttu-id="02a11-154">**dweventflags**</span><span class="sxs-lookup"><span data-stu-id="02a11-154">**dwEventFlags**</span></span>  
<span data-ttu-id="02a11-155">Der Typ des Maus Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="02a11-155">The type of mouse event.</span></span> <span data-ttu-id="02a11-156">Wenn dieser Wert 0 (null) ist, gibt er an, dass eine Maustaste gedrückt oder losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="02a11-156">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="02a11-157">Andernfalls ist dieser Member einer der folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="02a11-157">Otherwise, this member is one of the following values.</span></span>

| <span data-ttu-id="02a11-158">Wert</span><span class="sxs-lookup"><span data-stu-id="02a11-158">Value</span></span> | <span data-ttu-id="02a11-159">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="02a11-159">Meaning</span></span> |
|-|-|
| <span data-ttu-id="02a11-160">**DOUBLE_CLICK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="02a11-160">**DOUBLE_CLICK** 0x0002</span></span> | <span data-ttu-id="02a11-161">Der zweite Klick (Schaltflächen-Taste) mit einem Doppelklick ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="02a11-161">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="02a11-162">Der erste Klick wird als reguläres Button-Press-Ereignis zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="02a11-162">The first click is returned as a regular button-press event.</span></span> |
| <span data-ttu-id="02a11-163">**MOUSE_HWHEELED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="02a11-163">**MOUSE_HWHEELED** 0x0008</span></span> | <span data-ttu-id="02a11-164">Das horizontale Mausrad wurde verschoben.</span><span class="sxs-lookup"><span data-stu-id="02a11-164">The horizontal mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="02a11-165">Wenn das hohe Wort des **dwbuttonstate** -Members einen positiven Wert enthält, wurde das Rad nach rechts gedreht.</span><span class="sxs-lookup"><span data-stu-id="02a11-165">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="02a11-166">Andernfalls wurde das Rad nach links gedreht.</span><span class="sxs-lookup"><span data-stu-id="02a11-166">Otherwise, the wheel was rotated to the left.</span></span> |
| <span data-ttu-id="02a11-167">**MOUSE_MOVED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="02a11-167">**MOUSE_MOVED** 0x0001</span></span> | <span data-ttu-id="02a11-168">Eine Änderung der Mausposition ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="02a11-168">A change in mouse position occurred.</span></span> |
| <span data-ttu-id="02a11-169">**MOUSE_WHEELED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="02a11-169">**MOUSE_WHEELED** 0x0004</span></span> | <span data-ttu-id="02a11-170">Das vertikale Mausrad wurde verschoben.</span><span class="sxs-lookup"><span data-stu-id="02a11-170">The vertical mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="02a11-171">Wenn das hohe Wort des **dwbuttonstate** -Members einen positiven Wert enthält, wurde das Rad vom Benutzer entfernt.</span><span class="sxs-lookup"><span data-stu-id="02a11-171">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="02a11-172">Andernfalls wurde das Rad für den Benutzer rückwärts gedreht.</span><span class="sxs-lookup"><span data-stu-id="02a11-172">Otherwise, the wheel was rotated backward, toward the user.</span></span> |

## <a name="remarks"></a><span data-ttu-id="02a11-173">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="02a11-173">Remarks</span></span>

<span data-ttu-id="02a11-174">Mausereignisse werden in den Eingabepuffer eingefügt, wenn sich die Konsole im Mausmodus befindet ( **\_ Maus \_ Eingabe aktivieren** ).</span><span class="sxs-lookup"><span data-stu-id="02a11-174">Mouse events are placed in the input buffer when the console is in mouse mode ( **ENABLE\_MOUSE\_INPUT** ).</span></span>

<span data-ttu-id="02a11-175">Mausereignisse werden generiert, wenn der Benutzer die Maus bewegt oder eine der Maustasten drückt oder freigibt.</span><span class="sxs-lookup"><span data-stu-id="02a11-175">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="02a11-176">Mausereignisse werden nur dann in den Eingabepuffer einer Konsole eingefügt, wenn die Konsolen Gruppe den Tastaturfokus besitzt und sich der Cursor innerhalb der Rahmen des Konsolenfensters befindet.</span><span class="sxs-lookup"><span data-stu-id="02a11-176">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

## <a name="examples"></a><span data-ttu-id="02a11-177">Beispiele</span><span class="sxs-lookup"><span data-stu-id="02a11-177">Examples</span></span>

<span data-ttu-id="02a11-178">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="02a11-178">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="02a11-179">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="02a11-179">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="02a11-180">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="02a11-180">Minimum supported client</span></span> | <span data-ttu-id="02a11-181">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="02a11-181">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="02a11-182">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="02a11-182">Minimum supported server</span></span> | <span data-ttu-id="02a11-183">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="02a11-183">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="02a11-184">Header</span><span class="sxs-lookup"><span data-stu-id="02a11-184">Header</span></span> | <span data-ttu-id="02a11-185">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="02a11-185">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="02a11-186">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="02a11-186">See also</span></span>

[<span data-ttu-id="02a11-187">**Koord**</span><span class="sxs-lookup"><span data-stu-id="02a11-187">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="02a11-188">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="02a11-188">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="02a11-189">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="02a11-189">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="02a11-190">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="02a11-190">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="02a11-191">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="02a11-191">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
