---
title: Konsolen-WinEvents
description: Die folgenden Ereignis Konstanten werden im-Ereignis Parameter der wineventproc-Rückruffunktion verwendet. Weitere Informationen finden Sie unter WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: ab58df01b3fb29e6efea3ecd0aab145fe2f298c2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059947"
---
# <a name="console-winevents"></a><span data-ttu-id="5082e-105">Konsolen-WinEvents</span><span class="sxs-lookup"><span data-stu-id="5082e-105">Console WinEvents</span></span>


<span data-ttu-id="5082e-106">Die folgenden Ereignis Konstanten werden im- *Ereignis* Parameter der [*wineventproc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) -Rückruffunktion verwendet.</span><span class="sxs-lookup"><span data-stu-id="5082e-106">The following event constants are used in the *event* parameter of the [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) callback function.</span></span> <span data-ttu-id="5082e-107">Weitere Informationen finden Sie unter [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="5082e-107">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="5082e-108">Konstante/Wert</span><span class="sxs-lookup"><span data-stu-id="5082e-108">Constant/value</span></span></th>
<th><span data-ttu-id="5082e-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5082e-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="5082e-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span><span class="sxs-lookup"><span data-stu-id="5082e-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span></span></td>
<td><p><span data-ttu-id="5082e-111">Die Konsolen Einfügemarke wurde verschoben.</span><span class="sxs-lookup"><span data-stu-id="5082e-111">The console caret has moved.</span></span> <span data-ttu-id="5082e-112">Der <em>idobject</em> -Parameter hat einen oder mehrere der folgenden Werte: <strong>CONSOLE_CARET_SELECTION</strong> oder <strong>CONSOLE_CARET_VISIBLE</strong>.</span><span class="sxs-lookup"><span data-stu-id="5082e-112">The <em>idObject</em> parameter is one or more of the following values: <strong>CONSOLE_CARET_SELECTION</strong> or <strong>CONSOLE_CARET_VISIBLE</strong>.</span></span></p>
<p><span data-ttu-id="5082e-113">Der <em>idchild</em> -Parameter ist eine <strong><a href="https://docs.microsoft.com/windows/console/coord-str">coord</a></strong> -Struktur, die die aktuelle Position des Cursors angibt.</span><span class="sxs-lookup"><span data-stu-id="5082e-113">The <em>idChild</em> parameter is a <strong><a href="https://docs.microsoft.com/windows/console/coord-str">COORD</a></strong> structure that specifies the cursor's current position.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5082e-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span><span class="sxs-lookup"><span data-stu-id="5082e-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span></span></td>
<td><p><span data-ttu-id="5082e-115">Ein Konsolen Prozess wurde beendet.</span><span class="sxs-lookup"><span data-stu-id="5082e-115">A console process has exited.</span></span> <span data-ttu-id="5082e-116">Der <em>idobject</em> -Parameter enthält den Prozess Bezeichner des beendeten Prozesses.</span><span class="sxs-lookup"><span data-stu-id="5082e-116">The <em>idObject</em> parameter contains the process identifier of the terminated process.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5082e-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span><span class="sxs-lookup"><span data-stu-id="5082e-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span></span></td>
<td><p><span data-ttu-id="5082e-118">Das Konsolen Layout wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="5082e-118">The console layout has changed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5082e-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span><span class="sxs-lookup"><span data-stu-id="5082e-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span></span></td>
<td><p><span data-ttu-id="5082e-120">Ein neuer Konsolen Prozess wurde gestartet.</span><span class="sxs-lookup"><span data-stu-id="5082e-120">A new console process has started.</span></span> <span data-ttu-id="5082e-121">Der <em>idobject</em> -Parameter enthält den Prozess Bezeichner des neu erstellten Prozesses.</span><span class="sxs-lookup"><span data-stu-id="5082e-121">The <em>idObject</em> parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="5082e-122">Wenn es sich bei der Anwendung um eine 16-Bit-Anwendung handelt, ist der <em>idchild</em> -Parameter <strong>CONSOLE_APPLICATION_16BIT</strong> und <em>idobject</em> ist die Prozess-ID der der Konsole zugeordneten NTVDM-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="5082e-122">If the application is a 16-bit application, the <em>idChild</em> parameter is <strong>CONSOLE_APPLICATION_16BIT</strong> and <em>idObject</em> is the process identifier of the NTVDM session associated with the console.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5082e-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span><span class="sxs-lookup"><span data-stu-id="5082e-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span></span></td>
<td><p><span data-ttu-id="5082e-124">Es wurden mehr als ein Zeichen geändert.</span><span class="sxs-lookup"><span data-stu-id="5082e-124">More than one character has changed.</span></span> <span data-ttu-id="5082e-125">Der <em>idobject</em> -Parameter ist eine <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coord</strong></a> -Struktur, die den Anfang des geänderten Bereichs angibt.</span><span class="sxs-lookup"><span data-stu-id="5082e-125">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the start of the changed region.</span></span> <span data-ttu-id="5082e-126">Der <em>idchild</em> -Parameter ist eine <strong>coord</strong> -Struktur, die das Ende des geänderten Bereichs angibt.</span><span class="sxs-lookup"><span data-stu-id="5082e-126">The <em>idChild</em> parameter is a <strong>COORD</strong> structure that specifies the end of the changed region.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5082e-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span><span class="sxs-lookup"><span data-stu-id="5082e-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span></span></td>
<td><p><span data-ttu-id="5082e-128">Die Konsole hat einen Rollup ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5082e-128">The console has scrolled.</span></span> <span data-ttu-id="5082e-129">Der <em>idobject</em> -Parameter ist die horizontale Entfernung der Konsole.</span><span class="sxs-lookup"><span data-stu-id="5082e-129">The <em>idObject</em> parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="5082e-130">Der <em>idchild</em> -Parameter ist die vertikale Entfernung der Konsole.</span><span class="sxs-lookup"><span data-stu-id="5082e-130">The <em>idChild</em> parameter is the vertical distance the console has scrolled.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5082e-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span><span class="sxs-lookup"><span data-stu-id="5082e-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span></span></td>
<td><p><span data-ttu-id="5082e-132">Ein einzelnes Zeichen hat sich geändert.</span><span class="sxs-lookup"><span data-stu-id="5082e-132">A single character has changed.</span></span> <span data-ttu-id="5082e-133">Der <em>idobject</em> -Parameter ist eine <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coord</strong></a> -Struktur, die das geänderte Zeichen angibt.</span><span class="sxs-lookup"><span data-stu-id="5082e-133">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the character that has changed.</span></span> <span data-ttu-id="5082e-134">Der <em>idchild</em> -Parameter gibt das Zeichen im niedrigen Wort und die <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">Zeichen Attribute</a> im hohen Wort an.</span><span class="sxs-lookup"><span data-stu-id="5082e-134">The <em>idChild</em> parameter specifies the character in the low word and the <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">character attributes</a> in the high word.</span></span></p></td>
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

<a name="requirements"></a><span data-ttu-id="5082e-135">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5082e-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5082e-136">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="5082e-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5082e-137">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="5082e-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5082e-138">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="5082e-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5082e-139">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="5082e-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5082e-140">Header</span><span class="sxs-lookup"><span data-stu-id="5082e-140">Header</span></span></p></td>
<td><span data-ttu-id="5082e-141">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="5082e-141">Winuser.h</span></span></td>
</tr>
</tbody>
</table>
