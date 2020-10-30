---
title: Setconsoleskreenbuffersize-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "setconsoleskreenbuffersize", die die Größe des angegebenen Konsolenbildschirm Puffers ändert.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 46c412ccb41ac17a8e7cf327c80d7f8330738d65
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039328"
---
# <a name="setconsolescreenbuffersize-function"></a>Setconsoleskreenbuffersize-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ändert die Größe des angegebenen Konsolenbildschirm Puffers.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*dwSize* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die neue Größe des Konsolenbildschirm Puffers in Zeichen Zeilen und-Spalten angibt. Die angegebene Breite und Höhe darf nicht kleiner sein als die Breite und Höhe des Fensters des Konsolenbildschirm Puffers. Die angegebenen Dimensionen dürfen auch nicht kleiner als die vom System zulässige Mindestgröße sein. Dieses Minimum hängt von der aktuellen Schriftgröße für die Konsole (vom Benutzer ausgewählt) und den von der [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) -Funktion zurückgegebenen **SM- \_ cxMin** -und **SM- \_ Cymin** -Werten ab.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

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

[Konsoleneingabepuffer](console-input-buffer.md)

[**Koord**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)
