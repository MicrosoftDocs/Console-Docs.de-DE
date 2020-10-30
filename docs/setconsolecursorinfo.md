---
title: Setconsolecursorinfo-Funktion
description: Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4bbb14dd501d483f35fbce5e1a729eaf002b1579
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039398"
---
# <a name="setconsolecursorinfo-function"></a>Setconsolecursorinfo-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Legt die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer fest.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpconsolecursorinfo* \[ in\]  
Ein Zeiger auf eine [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur, die die neuen Spezifikationen für den Cursor des Konsolenbildschirm Puffers bereitstellt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn der Cursor eines Bildschirm Puffers sichtbar ist, kann seine Darstellung variieren und reicht von der vollständigen Füllung einer Zeichen Zelle bis zum Anzeigen als horizontale Linie am unteren Rand der Zelle. Der **dwSize** -Member der [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur gibt den Prozentsatz einer Zeichen Zelle an, die vom Cursor ausgefüllt wird. Wenn dieser Member kleiner als 1 oder größer als 100 ist, schlägt **setconsolecursorinfo** fehl.

> [!TIP]
> Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent im **[Cursor Sichtbarkeits](console-virtual-terminal-sequences.md#cursor-visibility)** Abschnitt mit `^[[?25h` den `^[[?25l` Sequenzen und. 

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

[**Konsolen \_ Cursor \_ Informationen**](console-cursor-info-str.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)
