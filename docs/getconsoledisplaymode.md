---
title: Getconsoledisplaymode-Funktion
description: Siehe Referenzinformationen zur getconsoledisplaymode-Funktion, die den Anzeigemodus der aktuellen Konsole abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b9ec78dc6fe5d7baa1a9af64010fd577f101c47
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358350"
---
# <a name="getconsoledisplaymode-function"></a>Getconsoledisplaymode-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft den Anzeigemodus der aktuellen Konsole ab.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a>Parameter

*lpmodeflags* \[ vorgenommen\]  
Der Anzeigemodus der Konsole. Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **CONSOLE_FULLSCREEN** 1 | Voll Bild Konsole. Die Konsole befindet sich in diesem Modus, sobald das Fenster maximiert ist. An diesem Punkt kann der Übergang zum Vollbildmodus weiterhin fehlschlagen. |
| **CONSOLE_FULLSCREEN_HARDWARE** 2 | Voll Bild Konsole, die direkt mit der Video Hardware kommuniziert. Dieser Modus wird festgelegt, nachdem sich die Konsole im **CONSOLE_FULLSCREEN** Modus befindet, um anzugeben, dass der Übergang zum Vollbildmodus abgeschlossen wurde. |

> [!NOTE]
> Der Übergang zu einem 100%-Hardware Modus für den Vollbildmodus wurde in Windows Vista mit der Neuplatzierung des Grafik Stapels zu [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model)entfernt. Bei späteren Versionen von Windows ist der Höchstwert, der sich ergibt, **CONSOLE_FULLSCREEN** ein fragebess Fenster, das den Vollbildmodus darstellt, aber nicht die exklusive Kontrolle über die Hardware darstellt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows XP \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2003 \[ -Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[Konsolenmodi](console-modes.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)