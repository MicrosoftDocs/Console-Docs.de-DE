---
title: SetConsoleCursorPosition-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur SetConsoleCursorPosition-Funktion, mit der die Cursorposition im angegebenen Konsolenbildschirm Puffer festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039368"
---
# <a name="setconsolecursorposition-function"></a>SetConsoleCursorPosition-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Legt die Cursorposition im angegebenen Konsolenbildschirm Puffer fest.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*dwcurrsorposition* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die neue Cursorposition in Zeichen angibt. Die Koordinaten sind die Spalte und die Zeile einer Bildschirm Puffer-Zeichen Zelle. Die Koordinaten müssen sich innerhalb der Grenzen des Konsolenbildschirm Puffers befinden.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Die Cursorposition bestimmt, wo Zeichen, die von der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder " [**Write-Console**](writeconsole.md) " geschrieben wurden oder von der Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " angezeigt werden, angezeigt werden. Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die aktuelle Position des Cursors zu ermitteln.

Wenn sich die neue Cursorposition nicht innerhalb der Grenzen des Fensters des Konsolenbildschirm Puffers befindet, wird der Fenster Ursprung geändert, um den Cursor sichtbar zu machen.

> [!TIP]
> Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Abschnitten **[einfache Cursor Positionierung](console-virtual-terminal-sequences.md#simple-cursor-positioning)** und **[Cursor Positionierung](console-virtual-terminal-sequences.md#cursor-positioning)** . Die Verwendung von Zeilenumbruch-, Wagen Rücklauf-, Rücktaste-und Registerkarten-Steuersequenzen kann bei der Cursor Positionierung ebenfalls hilfreich sein.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Verwenden der High-Level Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).

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

[Konsolenbildschirmpuffer](console-screen-buffers.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
