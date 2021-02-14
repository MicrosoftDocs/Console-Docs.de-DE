---
title: Setconsoleskreenbufferinfoex-Funktion
description: Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer auf den angegebenen Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 677df94d6397c1515ad96757788c9a044b6ed87e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358650"
---
# <a name="setconsolescreenbufferinfoex-function"></a>Setconsoleskreenbufferinfoex-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer fest.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>Parameter

*hConsoleOutput* \[in\]  
Ein Handle für den Konsolenbildschirm-Puffer. Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).

*lpconsoleskreenbufferinfoex* \[ in\]  
Eine [**\_ \_ \_ INFOEX-Struktur des Konsolenbildschirm Puffers**](console-screen-buffer-infoex.md) , die die Bildschirm Puffer Informationen der Konsole enthält.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

> [!TIP]
> Diese API verfügt über ein teilweises **[virtuelles Terminal](console-virtual-terminal-sequences.md)** . **[Cursor Positions Puffer](console-virtual-terminal-sequences.md#cursor-positioning)** -und **[Text Attribute](console-virtual-terminal-sequences.md#text-formatting)** weisen bestimmte Sequenz Entsprechungen auf. Die Farbtabelle ist nicht konfigurierbar, aber **[Erweiterte Farben](console-virtual-terminal-sequences.md#extended-colors)** sind über die normal verfügbaren **[Funktionen über Konsolenfunktionen](console-functions.md)** hinaus verfügbar. Popup Attribute haben keine Entsprechung, da Popup Menüs für die Befehlszeilen-Client Anwendung in der **virtuellen Terminal** Welt zuständig sind. Zum Schluss werden die Größe des Fensters und der voll Bild Status als Berechtigungen betrachtet, die sich im Besitz des Benutzers in der **virtuellen Terminal** Welt befinden und keine äquivalente Reihenfolge aufweisen.

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[**Konsolen \_ Bildschirm- \_ Puffer \_ INFOEX**](console-screen-buffer-infoex.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)