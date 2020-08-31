---
title: MOUSE_EVENT_RECORD Struktur
description: Siehe Referenzinformationen zur MOUSE_EVENT_RECORD Struktur, die ein Mauseingabe Ereignis in einer Konsolen INPUT_RECORD Struktur beschreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a3e95e9d35cdf2af2ec6836021dd8819323a4790
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059586"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="4e263-104">\_ \_ Daten Satzstruktur des Maus Ereignisses</span><span class="sxs-lookup"><span data-stu-id="4e263-104">MOUSE\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="4e263-105">Beschreibt ein Mauseingabe Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur.</span><span class="sxs-lookup"><span data-stu-id="4e263-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

<a name="syntax"></a><span data-ttu-id="4e263-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e263-106">Syntax</span></span>
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="4e263-107">Member</span><span class="sxs-lookup"><span data-stu-id="4e263-107">Members</span></span>
-------

<span data-ttu-id="4e263-108">**dwmoupositionposition**</span><span class="sxs-lookup"><span data-stu-id="4e263-108">**dwMousePosition**</span></span>  
<span data-ttu-id="4e263-109">Eine [**Koord**](coord-str.md) -Struktur, die die Position des Cursors in Bezug auf die Zeichen Zell Koordinaten des Konsolenbildschirm Puffers enthält.</span><span class="sxs-lookup"><span data-stu-id="4e263-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="4e263-110">**dwbuttonstate**</span><span class="sxs-lookup"><span data-stu-id="4e263-110">**dwButtonState**</span></span>  
<span data-ttu-id="4e263-111">Der Status der Maustasten.</span><span class="sxs-lookup"><span data-stu-id="4e263-111">The status of the mouse buttons.</span></span> <span data-ttu-id="4e263-112">Das unwichtigste Bit entspricht der linken Maustaste.</span><span class="sxs-lookup"><span data-stu-id="4e263-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="4e263-113">Das nächste signifikanteste Bit entspricht der rechten Maustaste.</span><span class="sxs-lookup"><span data-stu-id="4e263-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="4e263-114">Das nächste Bit gibt die nächste Maustaste an.</span><span class="sxs-lookup"><span data-stu-id="4e263-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="4e263-115">Die Bits entsprechen dann den Maustasten von links nach rechts.</span><span class="sxs-lookup"><span data-stu-id="4e263-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="4e263-116">Ein Bit ist 1, wenn die Schaltfläche gedrückt wurde.</span><span class="sxs-lookup"><span data-stu-id="4e263-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="4e263-117">Die folgenden Konstanten werden für die ersten fünf Maustasten definiert.</span><span class="sxs-lookup"><span data-stu-id="4e263-117">The following constants are defined for the first five mouse buttons.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="4e263-118">Wert</span><span class="sxs-lookup"><span data-stu-id="4e263-118">Value</span></span></th>
<th><span data-ttu-id="4e263-119">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="4e263-119">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="4e263-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="4e263-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="4e263-121">Die linke Maustaste.</span><span class="sxs-lookup"><span data-stu-id="4e263-121">The leftmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="4e263-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="4e263-123">Die zweite Schaltfläche von Links.</span><span class="sxs-lookup"><span data-stu-id="4e263-123">The second button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="4e263-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="4e263-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="4e263-125">Die dritte Schaltfläche von Links.</span><span class="sxs-lookup"><span data-stu-id="4e263-125">The third button from the left.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="4e263-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="4e263-127">Die vierte Schaltfläche von Links.</span><span class="sxs-lookup"><span data-stu-id="4e263-127">The fourth button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="4e263-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="4e263-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="4e263-129">Die Rechte Maustaste.</span><span class="sxs-lookup"><span data-stu-id="4e263-129">The rightmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="4e263-130">**dwcontrolkeystate**</span><span class="sxs-lookup"><span data-stu-id="4e263-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="4e263-131">Der Zustand der Steuerelement Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="4e263-131">The state of the control keys.</span></span> <span data-ttu-id="4e263-132">Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="4e263-132">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="4e263-133">Wert</span><span class="sxs-lookup"><span data-stu-id="4e263-133">Value</span></span></th>
<th><span data-ttu-id="4e263-134">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="4e263-134">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="4e263-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="4e263-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="4e263-136">Die Feststell Sperre ist auf on.</span><span class="sxs-lookup"><span data-stu-id="4e263-136">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="4e263-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="4e263-138">Der Schlüssel ist erweitert.</span><span class="sxs-lookup"><span data-stu-id="4e263-138">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="4e263-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="4e263-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="4e263-140">Die linke ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="4e263-140">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="4e263-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="4e263-142">Die linke STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="4e263-142">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="4e263-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="4e263-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="4e263-144">Der NUM-Sperr Licht ist on.</span><span class="sxs-lookup"><span data-stu-id="4e263-144">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="4e263-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="4e263-146">Die Rechte ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="4e263-146">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="4e263-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="4e263-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="4e263-148">Die Rechte STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="4e263-148">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="4e263-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="4e263-150">Das Licht der Scrollsperre ist on.</span><span class="sxs-lookup"><span data-stu-id="4e263-150">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="4e263-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="4e263-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="4e263-152">Die UMSCHALTTASTE wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="4e263-152">The SHIFT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="4e263-153">**dweventflags**</span><span class="sxs-lookup"><span data-stu-id="4e263-153">**dwEventFlags**</span></span>  
<span data-ttu-id="4e263-154">Der Typ des Maus Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="4e263-154">The type of mouse event.</span></span> <span data-ttu-id="4e263-155">Wenn dieser Wert 0 (null) ist, gibt er an, dass eine Maustaste gedrückt oder losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="4e263-155">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="4e263-156">Andernfalls ist dieser Member einer der folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="4e263-156">Otherwise, this member is one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="4e263-157">Wert</span><span class="sxs-lookup"><span data-stu-id="4e263-157">Value</span></span></th>
<th><span data-ttu-id="4e263-158">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="4e263-158">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="4e263-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="4e263-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="4e263-160">Der zweite Klick (Schaltflächen-Taste) mit einem Doppelklick ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="4e263-160">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="4e263-161">Der erste Klick wird als reguläres Button-Press-Ereignis zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="4e263-161">The first click is returned as a regular button-press event.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="4e263-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="4e263-163">Das horizontale Mausrad wurde verschoben.</span><span class="sxs-lookup"><span data-stu-id="4e263-163">The horizontal mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="4e263-164">Wenn das hohe Wort des <strong>dwbuttonstate</strong> -Members einen positiven Wert enthält, wurde das Rad nach rechts gedreht.</span><span class="sxs-lookup"><span data-stu-id="4e263-164">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="4e263-165">Andernfalls wurde das Rad nach links gedreht.</span><span class="sxs-lookup"><span data-stu-id="4e263-165">Otherwise, the wheel was rotated to the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="4e263-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="4e263-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="4e263-167">Eine Änderung der Mausposition ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="4e263-167">A change in mouse position occurred.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="4e263-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="4e263-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="4e263-169">Das vertikale Mausrad wurde verschoben.</span><span class="sxs-lookup"><span data-stu-id="4e263-169">The vertical mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="4e263-170">Wenn das hohe Wort des <strong>dwbuttonstate</strong> -Members einen positiven Wert enthält, wurde das Rad vom Benutzer entfernt.</span><span class="sxs-lookup"><span data-stu-id="4e263-170">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="4e263-171">Andernfalls wurde das Rad für den Benutzer rückwärts gedreht.</span><span class="sxs-lookup"><span data-stu-id="4e263-171">Otherwise, the wheel was rotated backward, toward the user.</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a><span data-ttu-id="4e263-172">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4e263-172">Remarks</span></span>
-------

<span data-ttu-id="4e263-173">Mausereignisse werden in den Eingabepuffer eingefügt, wenn sich die Konsole im Mausmodus befindet (\*\* \_ Maus \_ Eingabe aktivieren\*\*).</span><span class="sxs-lookup"><span data-stu-id="4e263-173">Mouse events are placed in the input buffer when the console is in mouse mode (**ENABLE\_MOUSE\_INPUT**).</span></span>

<span data-ttu-id="4e263-174">Mausereignisse werden generiert, wenn der Benutzer die Maus bewegt oder eine der Maustasten drückt oder freigibt.</span><span class="sxs-lookup"><span data-stu-id="4e263-174">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="4e263-175">Mausereignisse werden nur dann in den Eingabepuffer einer Konsole eingefügt, wenn die Konsolen Gruppe den Tastaturfokus besitzt und sich der Cursor innerhalb der Rahmen des Konsolenfensters befindet.</span><span class="sxs-lookup"><span data-stu-id="4e263-175">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

<a name="examples"></a><span data-ttu-id="4e263-176">Beispiele</span><span class="sxs-lookup"><span data-stu-id="4e263-176">Examples</span></span>
--------

<span data-ttu-id="4e263-177">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="4e263-177">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="4e263-178">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4e263-178">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4e263-179">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="4e263-179">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4e263-180">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4e263-180">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4e263-181">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="4e263-181">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4e263-182">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4e263-182">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4e263-183">Header</span><span class="sxs-lookup"><span data-stu-id="4e263-183">Header</span></span></p></td>
<td><span data-ttu-id="4e263-184">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4e263-184">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4e263-185"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4e263-185"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4e263-186">**Koord**</span><span class="sxs-lookup"><span data-stu-id="4e263-186">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="4e263-187">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="4e263-187">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="4e263-188">**"Etekconsoleinput"**</span><span class="sxs-lookup"><span data-stu-id="4e263-188">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="4e263-189">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4e263-189">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="4e263-190">**Schreibconsoleinput**</span><span class="sxs-lookup"><span data-stu-id="4e263-190">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




