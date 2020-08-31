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
# <a name="console-winevents"></a>Konsolen-WinEvents


Die folgenden Ereignis Konstanten werden im- *Ereignis* Parameter der [*wineventproc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) -Rückruffunktion verwendet. Weitere Informationen finden Sie unter [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Konstante/Wert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</td>
<td><p>Die Konsolen Einfügemarke wurde verschoben. Der <em>idobject</em> -Parameter hat einen oder mehrere der folgenden Werte: <strong>CONSOLE_CARET_SELECTION</strong> oder <strong>CONSOLE_CARET_VISIBLE</strong>.</p>
<p>Der <em>idchild</em> -Parameter ist eine <strong><a href="https://docs.microsoft.com/windows/console/coord-str">coord</a></strong> -Struktur, die die aktuelle Position des Cursors angibt.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</td>
<td><p>Ein Konsolen Prozess wurde beendet. Der <em>idobject</em> -Parameter enthält den Prozess Bezeichner des beendeten Prozesses.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</td>
<td><p>Das Konsolen Layout wurde geändert.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</td>
<td><p>Ein neuer Konsolen Prozess wurde gestartet. Der <em>idobject</em> -Parameter enthält den Prozess Bezeichner des neu erstellten Prozesses. Wenn es sich bei der Anwendung um eine 16-Bit-Anwendung handelt, ist der <em>idchild</em> -Parameter <strong>CONSOLE_APPLICATION_16BIT</strong> und <em>idobject</em> ist die Prozess-ID der der Konsole zugeordneten NTVDM-Sitzung.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</td>
<td><p>Es wurden mehr als ein Zeichen geändert. Der <em>idobject</em> -Parameter ist eine <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coord</strong></a> -Struktur, die den Anfang des geänderten Bereichs angibt. Der <em>idchild</em> -Parameter ist eine <strong>coord</strong> -Struktur, die das Ende des geänderten Bereichs angibt.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</td>
<td><p>Die Konsole hat einen Rollup ausgeführt. Der <em>idobject</em> -Parameter ist die horizontale Entfernung der Konsole. Der <em>idchild</em> -Parameter ist die vertikale Entfernung der Konsole.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</td>
<td><p>Ein einzelnes Zeichen hat sich geändert. Der <em>idobject</em> -Parameter ist eine <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coord</strong></a> -Struktur, die das geänderte Zeichen angibt. Der <em>idchild</em> -Parameter gibt das Zeichen im niedrigen Wort und die <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">Zeichen Attribute</a> im hohen Wort an.</p></td>
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
<td>Winuser. h</td>
</tr>
</tbody>
</table>
