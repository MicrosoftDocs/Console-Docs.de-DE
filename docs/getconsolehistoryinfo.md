---
title: Getconsolehistoryinfo-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur getconsolehistoryinfo-Funktion, die die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8335b7e23ffec0e894221f97f2c01be5b081d31f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038028"
---
# <a name="getconsolehistoryinfo-function"></a>Getconsolehistoryinfo-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses ab.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a>Parameter

*lpconsolehistoryinfo* \[ vorgenommen\]  
Ein Zeiger auf eine [**Konsolen \_ Verlauf- \_ Informations**](console-history-info.md) Struktur, die die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn es sich bei dem aufrufenden Prozess nicht um einen Konsolen Prozess handelt, schlägt die Funktion fehl und legt den letzten Fehler auf " **Fehler \_ Zugriff \_ verweigert** " fest.

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Informationen zum Konsolen \_ Verlauf \_**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)
