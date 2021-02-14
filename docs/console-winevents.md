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
ms.openlocfilehash: 2cd48537ef79f09024a55b32a98e2aa85fe76f62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358050"
---
# <a name="console-winevents"></a>Konsolen-WinEvents

> [!IMPORTANT]
> WinEvents sind Teil des Legacy- **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** -Frameworks. Bei der Entwicklung mit diesen Ereignissen wird dringend davon abgeraten, das **[Microsoft UI Automation](/windows/win32/winauto/entry-uiauto-win32)** -Framework zu bevorzugen, das eine stabilere und umfassende Sammlung von Schnittstellen für Barrierefreiheits-und Automatisierungsanwendungen zur Interaktion mit der Konsole bereitstellt. 

> [!WARNING]
> Die Registrierung für diese Ereignisse ist eine globale Aktivität und wirkt sich erheblich auf die Leistung aller Befehlszeilen Anwendungen aus, die auf einem System gleichzeitig ausgeführt werden, einschließlich der Dienste und Hintergrund Hilfsprogramme. Das **Microsoft UI Automation** -Framework ist eine spezifische Konsolen Sitzung und überschreitet diese Einschränkung.

Die folgenden Ereignis Konstanten werden im- *Ereignis* Parameter der [*wineventproc*](/windows/win32/api/winuser/nc-winuser-wineventproc) -Rückruffunktion verwendet. Weitere Informationen finden Sie unter [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

| Konstante/Wert | BESCHREIBUNG |
|-|-|
| **EVENT_CONSOLE_CARET** 0x4001 | Die Konsolen Einfügemarke wurde verschoben. Der *idobject* -Parameter hat einen oder mehrere der folgenden Werte: **CONSOLE_CARET_SELECTION** oder **CONSOLE_CARET_VISIBLE**. Der *idchild* -Parameter ist eine **[coord](coord-str.md)** -Struktur, die die aktuelle Position des Cursors angibt. |
| **EVENT_CONSOLE_END_APPLICATION** 0x4007 | Ein Konsolen Prozess wurde beendet. Der *idobject* -Parameter enthält den Prozess Bezeichner des beendeten Prozesses. |
| **EVENT_CONSOLE_LAYOUT** 0x4005 | Das Konsolen Layout wurde geändert. |
| **EVENT_CONSOLE_START_APPLICATION** 0x4006 | Ein neuer Konsolen Prozess wurde gestartet. Der *idobject* -Parameter enthält den Prozess Bezeichner des neu erstellten Prozesses. Wenn es sich bei der Anwendung um eine 16-Bit-Anwendung handelt, ist der *idchild* -Parameter **CONSOLE_APPLICATION_16BIT** und *idobject* ist die Prozess-ID der der Konsole zugeordneten NTVDM-Sitzung. |
|**EVENT_CONSOLE_UPDATE_REGION** 0x4002 | Es wurden mehr als ein Zeichen geändert. Der  *idobject* -Parameter ist eine **[coord](coord-str.md)** -Struktur, die den Anfang des geänderten Bereichs angibt. Der *idchild* -Parameter ist eine **coord** -Struktur, die das Ende des geänderten Bereichs angibt. |
|**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004 | Die Konsole hat einen Rollup ausgeführt. Der *idobject* -Parameter ist die horizontale Entfernung der Konsole. Der *idchild* -Parameter ist die vertikale Entfernung der Konsole. |
|**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003 | Ein einzelnes Zeichen hat sich geändert. Der *idobject* -Parameter ist eine **[coord](coord-str.md)** -Struktur, die das geänderte Zeichen angibt. Der *idchild* -Parameter gibt das Zeichen im niedrigen Wort und die **[Zeichen Attribute](console-screen-buffers.md#character-attributes)** im hohen Wort an. |

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | Winuser. h |