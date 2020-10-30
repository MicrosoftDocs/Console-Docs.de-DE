---
title: Getlargestconsolewindowsize-Funktion
description: Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ddaa4716886fccaaa87e86362719020eb2408765
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037838"
---
# <a name="getlargestconsolewindowsize-function"></a>Getlargestconsolewindowsize-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.

## <a name="syntax"></a>Syntax

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert eine [**coord**](coord-str.md) -Struktur, die die Anzahl der Zeichen Zellen Spalten ( **X** -Member) und der Zeilen ( **Y** -Member) im größtmöglichen Konsolenfenster angibt. Andernfalls sind die Elemente der-Struktur 0 (null).

Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Die-Funktion berücksichtigt nicht die Größe des Bildschirm Puffers der Konsole. Dies bedeutet, dass die zurückgegebene Fenstergröße möglicherweise größer als die Größe des Konsolenbildschirm Puffers ist. Mithilfe der [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion kann die maximale Größe des Konsolenfensters anhand der aktuellen Bildschirm Puffergröße, der aktuellen Schriftart und der Anzeige Größe bestimmt werden.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

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

[**Koord**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Fenster-und Bildschirm Puffergröße](window-and-screen-buffer-size.md)
