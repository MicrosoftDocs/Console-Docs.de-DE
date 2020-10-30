---
title: CONSOLE_READCONSOLE_CONTROL-Struktur
description: Siehe Referenzinformationen zur CONSOLE_READCONSOLE_CONTROL Struktur, die Informationen zu einem Konsolen Lesevorgang enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039188"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="971fa-104">\_ \_ Steuerelement Struktur der Konsole</span><span class="sxs-lookup"><span data-stu-id="971fa-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>

<span data-ttu-id="971fa-105">Enthält Informationen zu einem Konsolen Lesevorgang.</span><span class="sxs-lookup"><span data-stu-id="971fa-105">Contains information for a console read operation.</span></span>

## <a name="syntax"></a><span data-ttu-id="971fa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="971fa-106">Syntax</span></span>

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a><span data-ttu-id="971fa-107">Member</span><span class="sxs-lookup"><span data-stu-id="971fa-107">Members</span></span>

<span data-ttu-id="971fa-108">**nlength**</span><span class="sxs-lookup"><span data-stu-id="971fa-108">**nLength**</span></span>  
<span data-ttu-id="971fa-109">Die Größe der-Struktur.</span><span class="sxs-lookup"><span data-stu-id="971fa-109">The size of the structure.</span></span> <span data-ttu-id="971fa-110">Legen Sie diesen Member auf fest `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="971fa-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="971fa-111">**ninitialchars**</span><span class="sxs-lookup"><span data-stu-id="971fa-111">**nInitialChars**</span></span>  
<span data-ttu-id="971fa-112">Die Anzahl der zu über springenden Zeichen (und somit beibehalten), bevor neue Lese Eingaben in den Puffer geschrieben werden, der an die Funktion der Schreib [**Konsole**](readconsole.md) weitergegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="971fa-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="971fa-113">Dieser Wert muss kleiner als der *nnumofcharstoread* -Parameter der Read **Console** -Funktion sein.</span><span class="sxs-lookup"><span data-stu-id="971fa-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="971fa-114">**dwctrlwakeupmask**</span><span class="sxs-lookup"><span data-stu-id="971fa-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="971fa-115">Eine Maske, die angibt, welche Steuerzeichen zwischen `0x00` und `0x1F` verwendet werden sollen, um zu signalisieren, dass der Lesevorgang beendet ist.</span><span class="sxs-lookup"><span data-stu-id="971fa-115">A mask specifying which control characters between `0x00` and `0x1F` should be used to signal that the read is complete.</span></span> <span data-ttu-id="971fa-116">Jedes Bit entspricht einem Zeichen mit dem am wenigsten signifikanten Bit, das `0x00` oder entspricht, `NUL` und dem signifikantesten Bit, das `0x1F` oder entspricht `US` .</span><span class="sxs-lookup"><span data-stu-id="971fa-116">Each bit corresponds to a character with the least significant bit corresponding to `0x00` or `NUL` and the most significant bit corresponding to `0x1F` or `US`.</span></span> <span data-ttu-id="971fa-117">Es können mehrere Bits (Steuerzeichen) angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="971fa-117">Multiple bits (control characters) can be specified.</span></span>

<span data-ttu-id="971fa-118">**dwcontrolkeystate**</span><span class="sxs-lookup"><span data-stu-id="971fa-118">**dwControlKeyState**</span></span>  
<span data-ttu-id="971fa-119">Der Zustand der Steuerelement Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="971fa-119">The state of the control keys.</span></span> <span data-ttu-id="971fa-120">Dieser Member kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="971fa-120">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="971fa-121">Wert</span><span class="sxs-lookup"><span data-stu-id="971fa-121">Value</span></span> | <span data-ttu-id="971fa-122">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="971fa-122">Meaning</span></span> |
|-|-|
| <span data-ttu-id="971fa-123">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="971fa-123">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="971fa-124">Die Feststell Sperre ist auf on.</span><span class="sxs-lookup"><span data-stu-id="971fa-124">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="971fa-125">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="971fa-125">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="971fa-126">Der Schlüssel ist erweitert.</span><span class="sxs-lookup"><span data-stu-id="971fa-126">The key is enhanced.</span></span> <span data-ttu-id="971fa-127">Siehe [Hinweise](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="971fa-127">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="971fa-128">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="971fa-128">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="971fa-129">Die linke ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="971fa-129">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="971fa-130">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="971fa-130">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="971fa-131">Die linke STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="971fa-131">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="971fa-132">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="971fa-132">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="971fa-133">Der NUM-Sperr Licht ist on.</span><span class="sxs-lookup"><span data-stu-id="971fa-133">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="971fa-134">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="971fa-134">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="971fa-135">Die Rechte ALT-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="971fa-135">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="971fa-136">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="971fa-136">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="971fa-137">Die Rechte STRG-Taste wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="971fa-137">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="971fa-138">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="971fa-138">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="971fa-139">Das Licht der Scrollsperre ist on.</span><span class="sxs-lookup"><span data-stu-id="971fa-139">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="971fa-140">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="971fa-140">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="971fa-141">Die UMSCHALTTASTE wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="971fa-141">The SHIFT key is pressed.</span></span> |

## <a name="requirements"></a><span data-ttu-id="971fa-142">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="971fa-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="971fa-143">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="971fa-143">Minimum supported client</span></span> | <span data-ttu-id="971fa-144">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="971fa-144">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="971fa-145">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="971fa-145">Minimum supported server</span></span> | <span data-ttu-id="971fa-146">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="971fa-146">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="971fa-147">Header</span><span class="sxs-lookup"><span data-stu-id="971fa-147">Header</span></span> | <span data-ttu-id="971fa-148">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="971fa-148">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="971fa-149">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="971fa-149">See also</span></span>

[<span data-ttu-id="971fa-150">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="971fa-150">**ReadConsole**</span></span>](readconsole.md)
