---
title: Konsolen-WinEvents
description: Die folgenden Ereignis Konstanten werden im-Ereignis Parameter der wineventproc-Rückruffunktion verwendet. Weitere Informationen finden Sie unter WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: 2c5d641140316089b38b836bf3fba7534ccd5600
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038328"
---
# <a name="console-winevents"></a><span data-ttu-id="c333c-105">Konsolen-WinEvents</span><span class="sxs-lookup"><span data-stu-id="c333c-105">Console WinEvents</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c333c-106">WinEvents sind Teil des Legacy- **[Microsoft Active Accessibility](https://docs.microsoft.com/windows/win32/winauto/microsoft-active-accessibility)** -Frameworks.</span><span class="sxs-lookup"><span data-stu-id="c333c-106">WinEvents are part of the legacy **[Microsoft Active Accessibility](https://docs.microsoft.com/windows/win32/winauto/microsoft-active-accessibility)** framework.</span></span> <span data-ttu-id="c333c-107">Bei der Entwicklung mit diesen Ereignissen wird dringend davon abgeraten, das **[Microsoft UI Automation](https://docs.microsoft.com/windows/win32/winauto/entry-uiauto-win32)** -Framework zu bevorzugen, das eine stabilere und umfassende Sammlung von Schnittstellen für Barrierefreiheits-und Automatisierungsanwendungen zur Interaktion mit der Konsole bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="c333c-107">Development using these events is strongly discouraged in favor of the **[Microsoft UI Automation](https://docs.microsoft.com/windows/win32/winauto/entry-uiauto-win32)** framework which provides a more robust and comprehensive suite of interfaces for accessibility and automation applications to interact with the console.</span></span> 

> [!WARNING]
> <span data-ttu-id="c333c-108">Die Registrierung für diese Ereignisse ist eine globale Aktivität und wirkt sich erheblich auf die Leistung aller Befehlszeilen Anwendungen aus, die auf einem System gleichzeitig ausgeführt werden, einschließlich der Dienste und Hintergrund Hilfsprogramme.</span><span class="sxs-lookup"><span data-stu-id="c333c-108">Registering for these events is a global activity and will significantly impact performance of all command-line applications running on a system at the same time, including services and background utilities.</span></span> <span data-ttu-id="c333c-109">Das **Microsoft UI Automation** -Framework ist eine spezifische Konsolen Sitzung und überschreitet diese Einschränkung.</span><span class="sxs-lookup"><span data-stu-id="c333c-109">The **Microsoft UI Automation** framework is console session specific and overcomes this limitation.</span></span>

<span data-ttu-id="c333c-110">Die folgenden Ereignis Konstanten werden im- *Ereignis* Parameter der [*wineventproc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) -Rückruffunktion verwendet.</span><span class="sxs-lookup"><span data-stu-id="c333c-110">The following event constants are used in the *event* parameter of the [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) callback function.</span></span> <span data-ttu-id="c333c-111">Weitere Informationen finden Sie unter [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="c333c-111">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

| <span data-ttu-id="c333c-112">Konstante/Wert</span><span class="sxs-lookup"><span data-stu-id="c333c-112">Constant/value</span></span> | <span data-ttu-id="c333c-113">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="c333c-113">Description</span></span> |
|-|-|
| <span data-ttu-id="c333c-114">**EVENT_CONSOLE_CARET** 0x4001</span><span class="sxs-lookup"><span data-stu-id="c333c-114">**EVENT_CONSOLE_CARET** 0x4001</span></span> | <span data-ttu-id="c333c-115">Die Konsolen Einfügemarke wurde verschoben.</span><span class="sxs-lookup"><span data-stu-id="c333c-115">The console caret has moved.</span></span> <span data-ttu-id="c333c-116">Der *idobject* -Parameter hat einen oder mehrere der folgenden Werte: **CONSOLE_CARET_SELECTION** oder **CONSOLE_CARET_VISIBLE** .</span><span class="sxs-lookup"><span data-stu-id="c333c-116">The *idObject* parameter is one or more of the following values: **CONSOLE_CARET_SELECTION** or **CONSOLE_CARET_VISIBLE** .</span></span> <span data-ttu-id="c333c-117">Der *idchild* -Parameter ist eine **[coord](coord-str.md)** -Struktur, die die aktuelle Position des Cursors angibt.</span><span class="sxs-lookup"><span data-stu-id="c333c-117">The *idChild* parameter is a **[COORD](coord-str.md)** structure that specifies the cursor's current position.</span></span> |
| <span data-ttu-id="c333c-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span><span class="sxs-lookup"><span data-stu-id="c333c-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span></span> | <span data-ttu-id="c333c-119">Ein Konsolen Prozess wurde beendet.</span><span class="sxs-lookup"><span data-stu-id="c333c-119">A console process has exited.</span></span> <span data-ttu-id="c333c-120">Der *idobject* -Parameter enthält den Prozess Bezeichner des beendeten Prozesses.</span><span class="sxs-lookup"><span data-stu-id="c333c-120">The *idObject* parameter contains the process identifier of the terminated process.</span></span> |
| <span data-ttu-id="c333c-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span><span class="sxs-lookup"><span data-stu-id="c333c-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span></span> | <span data-ttu-id="c333c-122">Das Konsolen Layout wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="c333c-122">The console layout has changed.</span></span> |
| <span data-ttu-id="c333c-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span><span class="sxs-lookup"><span data-stu-id="c333c-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span></span> | <span data-ttu-id="c333c-124">Ein neuer Konsolen Prozess wurde gestartet.</span><span class="sxs-lookup"><span data-stu-id="c333c-124">A new console process has started.</span></span> <span data-ttu-id="c333c-125">Der *idobject* -Parameter enthält den Prozess Bezeichner des neu erstellten Prozesses.</span><span class="sxs-lookup"><span data-stu-id="c333c-125">The *idObject* parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="c333c-126">Wenn es sich bei der Anwendung um eine 16-Bit-Anwendung handelt, ist der *idchild* -Parameter **CONSOLE_APPLICATION_16BIT** und *idobject* ist die Prozess-ID der der Konsole zugeordneten NTVDM-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="c333c-126">If the application is a 16-bit application, the *idChild* parameter is **CONSOLE_APPLICATION_16BIT** and *idObject* is the process identifier of the NTVDM session associated with the console.</span></span> |
|<span data-ttu-id="c333c-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span><span class="sxs-lookup"><span data-stu-id="c333c-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span></span> | <span data-ttu-id="c333c-128">Es wurden mehr als ein Zeichen geändert.</span><span class="sxs-lookup"><span data-stu-id="c333c-128">More than one character has changed.</span></span> <span data-ttu-id="c333c-129">Der  *idobject* -Parameter ist eine **[coord](coord-str.md)** -Struktur, die den Anfang des geänderten Bereichs angibt.</span><span class="sxs-lookup"><span data-stu-id="c333c-129">The  *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the start of the changed region.</span></span> <span data-ttu-id="c333c-130">Der *idchild* -Parameter ist eine **coord** -Struktur, die das Ende des geänderten Bereichs angibt.</span><span class="sxs-lookup"><span data-stu-id="c333c-130">The *idChild* parameter is a **COORD** structure that specifies the end of the changed region.</span></span> |
|<span data-ttu-id="c333c-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span><span class="sxs-lookup"><span data-stu-id="c333c-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span></span> | <span data-ttu-id="c333c-132">Die Konsole hat einen Rollup ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c333c-132">The console has scrolled.</span></span> <span data-ttu-id="c333c-133">Der *idobject* -Parameter ist die horizontale Entfernung der Konsole.</span><span class="sxs-lookup"><span data-stu-id="c333c-133">The *idObject* parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="c333c-134">Der *idchild* -Parameter ist die vertikale Entfernung der Konsole.</span><span class="sxs-lookup"><span data-stu-id="c333c-134">The *idChild* parameter is the vertical distance the console has scrolled.</span></span> |
|<span data-ttu-id="c333c-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span><span class="sxs-lookup"><span data-stu-id="c333c-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span></span> | <span data-ttu-id="c333c-136">Ein einzelnes Zeichen hat sich geändert.</span><span class="sxs-lookup"><span data-stu-id="c333c-136">A single character has changed.</span></span> <span data-ttu-id="c333c-137">Der *idobject* -Parameter ist eine **[coord](coord-str.md)** -Struktur, die das geänderte Zeichen angibt.</span><span class="sxs-lookup"><span data-stu-id="c333c-137">The *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the character that has changed.</span></span> <span data-ttu-id="c333c-138">Der *idchild* -Parameter gibt das Zeichen im niedrigen Wort und die **[Zeichen Attribute](console-screen-buffers.md#character-attributes)** im hohen Wort an.</span><span class="sxs-lookup"><span data-stu-id="c333c-138">The *idChild* parameter specifies the character in the low word and the **[character attributes](console-screen-buffers.md#character-attributes)** in the high word.</span></span> |

## <a name="requirements"></a><span data-ttu-id="c333c-139">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="c333c-139">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c333c-140">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c333c-140">Minimum supported client</span></span> | <span data-ttu-id="c333c-141">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c333c-141">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c333c-142">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c333c-142">Minimum supported server</span></span> | <span data-ttu-id="c333c-143">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c333c-143">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c333c-144">Header</span><span class="sxs-lookup"><span data-stu-id="c333c-144">Header</span></span> | <span data-ttu-id="c333c-145">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="c333c-145">Winuser.h</span></span> |
