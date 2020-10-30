---
title: Flushconsoleingeputbuffer-Funktion
description: Leert den Konsolen Eingabepuffer. Alle Eingabedaten Sätze, die sich derzeit im Eingabepuffer befinden, werden verworfen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 543552e9252c1f28701a0b316b43597cdd9cd2c9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039048"
---
# <a name="flushconsoleinputbuffer-function"></a>Flushconsoleingeputbuffer-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Leert den Konsolen Eingabepuffer. Alle Eingabedaten Sätze, die sich derzeit im Eingabepuffer befinden, werden verworfen.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a>Parameter

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

> [!TIP]
> Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** . Wenn Sie versuchen, die Eingabe Warteschlange gleichzeitig zu leeren, kann der Status in der Warteschlange auf unerwartete Weise zerstört werden.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
