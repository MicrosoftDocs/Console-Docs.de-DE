---
title: Setconsoledisplaymode-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur setconsoledisplaymode-Funktion, mit der der Anzeigemodus des angegebenen Konsolenbildschirm Puffers festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: af61d897269311ccfa9db336083e898f6d75da80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357700"
---
# <a name="setconsoledisplaymode-function"></a>Setconsoledisplaymode-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Legt den Anzeigemodus des angegebenen Konsolenbildschirm Puffers fest.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a>Parameter

*hConsoleOutput* \[in\]  
Ein Handle für den Konsolenbildschirm-Puffer.

*dwFlags* \[ in\]  
Der Anzeigemodus der Konsole. Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **CONSOLE_FULLSCREEN_MODE** 1 | Der Text wird im Vollbildmodus angezeigt. |
| **CONSOLE_WINDOWED_MODE** 2 | Der Text wird in einem Konsolenfenster angezeigt. |

*lpnewscreenbufferdimensions* \[ Out, optional\]  
Ein Zeiger auf eine [**Koord**](coord-str.md) -Struktur, die die neuen Abmessungen des Bildschirm Puffers empfängt, in Zeichen.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

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

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)