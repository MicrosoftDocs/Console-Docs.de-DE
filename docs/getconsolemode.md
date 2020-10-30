---
title: Getconsolemode-Funktion
description: Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 54667d92509687111cb562f517d488c8adbc2181
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038872"
---
# <a name="getconsolemode-function"></a>Getconsolemode-Funktion

Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a>Parameter

*hconsolehandle* \[ in\]  
Ein Handle des Konsolen Eingabe Puffers oder des Konsolenbildschirm Puffers. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpmode* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die den aktuellen Modus des angegebenen Puffers empfängt.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

Um die e/a-Modi einer Konsole zu ändern, müssen Sie die Funktion [**setconsolemode**](setconsolemode.md) aufrufen.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Consoleapi. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[Konsolen Modi](console-modes.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleMode**](setconsolemode.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
