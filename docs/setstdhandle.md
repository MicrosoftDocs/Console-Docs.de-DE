---
title: Setstdhandle-Funktion
description: Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039298"
---
# <a name="setstdhandle-function"></a>Setstdhandle-Funktion

Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.

## <a name="syntax"></a>Syntax

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a>Parameter

*nstdhandle* \[ in\]  
Das Standardgerät, für das das Handle festgelegt werden soll. Dieser Parameter kann einen der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | Das Standardeingabe Gerät. Anfänglich ist dies der Konsolen Eingabepuffer `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | Das Standardausgabe Gerät. Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | Das Standardfehler Gerät. Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` . |

*hHandle* \[ in\]  
Das Handle für das Standardgerät.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Die Standard Handles eines Prozesses wurden möglicherweise durch einen Aufrufen von **setstdhandle** umgeleitet. in diesem Fall gibt [**getstdhandle**](getstdhandle.md) das umgeleitete Handle zurück. Wenn die Standard Handles umgeleitet wurden, können Sie den Wert von "$" in einem Aufrufen der Funktion "angleichen [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " angeben, um ein Handle für den Eingabepuffer einer Konsole abzurufen. Entsprechend können Sie den Wert für "$ $" angeben, um ein Handle für den aktiven Bildschirm Puffer der Konsole zu erhalten.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Erstellen eines untergeordneten Prozesses mit umgeleiteter Eingabe und Ausgabe](https://msdn.microsoft.com/library/windows/desktop/ms682499).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Processenv. h (über Winbase. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[Konsolenhandles](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetStdHandle**](getstdhandle.md)
