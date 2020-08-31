---
title: CONSOLE_READCONSOLE_CONTROL Struktur
description: Siehe Referenzinformationen zur CONSOLE_READCONSOLE_CONTROL Struktur, die Informationen zu einem Konsolen Lesevorgang enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4fc6af26cd540a7af207af252963c21ba216cdee
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060075"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="5185c-104">\_ \_ Steuerelement Struktur der Konsole</span><span class="sxs-lookup"><span data-stu-id="5185c-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>


<span data-ttu-id="5185c-105">Enthält Informationen zu einem Konsolen Lesevorgang.</span><span class="sxs-lookup"><span data-stu-id="5185c-105">Contains information for a console read operation.</span></span>

<a name="syntax"></a><span data-ttu-id="5185c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5185c-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

<a name="members"></a><span data-ttu-id="5185c-107">Member</span><span class="sxs-lookup"><span data-stu-id="5185c-107">Members</span></span>
-------

<span data-ttu-id="5185c-108">**nlength**</span><span class="sxs-lookup"><span data-stu-id="5185c-108">**nLength**</span></span>  
<span data-ttu-id="5185c-109">Die Größe der-Struktur.</span><span class="sxs-lookup"><span data-stu-id="5185c-109">The size of the structure.</span></span> <span data-ttu-id="5185c-110">Legen Sie diesen Member auf fest `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="5185c-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="5185c-111">**ninitialchars**</span><span class="sxs-lookup"><span data-stu-id="5185c-111">**nInitialChars**</span></span>  
<span data-ttu-id="5185c-112">Die Anzahl der zu über springenden Zeichen (und somit beibehalten), bevor neue Lese Eingaben in den Puffer geschrieben werden, der an die Funktion der Schreib [**Konsole**](readconsole.md) weitergegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="5185c-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="5185c-113">Dieser Wert muss kleiner als der *nnumofcharstoread* -Parameter der Read **Console** -Funktion sein.</span><span class="sxs-lookup"><span data-stu-id="5185c-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="5185c-114">**dwctrlwakeupmask**</span><span class="sxs-lookup"><span data-stu-id="5185c-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="5185c-115">Ein benutzerdefiniertes Steuerzeichen, das verwendet wird, um zu signalisieren, dass der Lesevorgang beendet ist.</span><span class="sxs-lookup"><span data-stu-id="5185c-115">A user-defined control character used to signal that the read is complete.</span></span>

<span data-ttu-id="5185c-116">**dwcontrolkeystate**</span><span class="sxs-lookup"><span data-stu-id="5185c-116">**dwControlKeyState**</span></span>  
<span data-ttu-id="5185c-117">Der Zustand der Steuerelement Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="5185c-117">The state of the control keys.</span></span> <span data-ttu-id="5185c-118">Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="5185c-118">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="5185c-119">Wert</span><span class="sxs-lookup"><span data-stu-id="5185c-119">Value</span></span></th>
<th><span data-ttu-id="5185c-120">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="5185c-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="5185c-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="5185c-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="5185c-122">Die Feststell Sperre ist auf on.</span><span class="sxs-lookup"><span data-stu-id="5185c-122">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5185c-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="5185c-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="5185c-124">Der Schlüssel ist erweitert.</span><span class="sxs-lookup"><span data-stu-id="5185c-124">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5185c-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="5185c-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="5185c-126">Die linke ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="5185c-126">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5185c-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="5185c-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="5185c-128">Die linke STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="5185c-128">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5185c-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="5185c-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="5185c-130">Der NUM-Sperr Licht ist on.</span><span class="sxs-lookup"><span data-stu-id="5185c-130">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5185c-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="5185c-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="5185c-132">Die Rechte ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="5185c-132">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5185c-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="5185c-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="5185c-134">Die Rechte STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="5185c-134">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5185c-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="5185c-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="5185c-136">Das Licht der Scrollsperre ist on.</span><span class="sxs-lookup"><span data-stu-id="5185c-136">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5185c-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="5185c-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="5185c-138">Die UMSCHALTTASTE wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="5185c-138">The SHIFT key is pressed.</span></span></p></td>
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

 

<a name="requirements"></a><span data-ttu-id="5185c-139">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5185c-139">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5185c-140">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="5185c-140">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5185c-141">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="5185c-141">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5185c-142">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="5185c-142">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5185c-143">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="5185c-143">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5185c-144">Header</span><span class="sxs-lookup"><span data-stu-id="5185c-144">Header</span></span></p></td>
<td><span data-ttu-id="5185c-145">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5185c-145">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5185c-146"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5185c-146"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5185c-147">**"Read Console"**</span><span class="sxs-lookup"><span data-stu-id="5185c-147">**ReadConsole**</span></span>](readconsole.md)

 

 




