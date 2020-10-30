---
title: Generateconsolectrlevent-Funktion
description: Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f074ad87676673221d34461e8bae484895781f56
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038138"
---
# <a name="generateconsolectrlevent-function"></a>Generateconsolectrlevent-Funktion

Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a>Parameter

*dwctrlevent* \[ in\]  
Der Typ des zu generierenden Signals. Dieser Parameter kann einen der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **CTRL_C_EVENT** 0 | Generiert ein STRG + C-Signal. Dieses Signal kann nicht für Prozessgruppen generiert werden. Wenn *dwprocessgroupid* ungleich NULL ist, wird diese Funktion erfolgreich ausgeführt, aber das STRG + C-Signal wird nicht von Prozessen innerhalb der angegebenen Prozessgruppe empfangen. |
| **CTRL_BREAK_EVENT** 1 | Generiert ein STRG + UNTBR-Signal. |

*dwprocessgroupid* \[ in\]  
Der Bezeichner der Prozessgruppe, für die das Signal empfangen werden soll. Eine Prozessgruppe wird erstellt, wenn das Flag " **\_ neue \_ Prozess \_ Gruppe erstellen** " in einem Aufrufen der Funktion " [**deateprocess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) " angegeben wird. Der Prozess Bezeichner des neuen Prozesses ist auch der Prozessgruppen Bezeichner einer neuen Prozessgruppe. Die Prozessgruppe umfasst alle Prozesse, bei denen es sich um nachfolgende Elemente des Stamm Prozesses handelt. Nur die Prozesse in der Gruppe, die dieselbe Konsole wie der aufrufende Prozess nutzen, erhalten das Signal. Anders ausgedrückt: Wenn ein Prozess in der Gruppe eine neue Konsole erstellt, empfängt dieser Prozess weder das Signal noch seine Nachfolger.

Wenn dieser Parameter 0 (null) ist, wird das Signal in allen Prozessen generiert, die die Konsole des aufrufenden Prozesses gemeinsam verwenden.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

**Generateconsolectrlevent** bewirkt, dass die Handlerfunktionen der Prozesse in der Zielgruppe aufgerufen werden. Alle Konsolen Prozesse verfügen über eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion aufruft. Ein Konsolen Prozess kann die [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion verwenden, um andere Handlerfunktionen zu installieren oder zu entfernen.

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) kann auch ein Vererb bares Attribut aktivieren, das bewirkt, dass der aufrufende Prozess STRG + C-Signale ignoriert. Wenn **generateconsolectrlevent** ein STRG + C-Signal an einen Prozess sendet, für den dieses Attribut aktiviert ist, werden die Handlerfunktionen für diesen Prozess nicht aufgerufen. STRG + untbugsignale bewirken immer, dass die Handlerfunktionen aufgerufen werden.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolen-Bearbeitungssteuerelemente](console-control-handlers.md)

[Konsolenfunktionen](console-functions.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)
