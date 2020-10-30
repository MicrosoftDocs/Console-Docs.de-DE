---
title: Getconsoleskreenbufferinfoex-Funktion
description: Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 5f4b0f11821b7d5b61c61d4ab8f9774c4a69eec0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037938"
---
# <a name="getconsolescreenbufferinfoex-function"></a>Getconsoleskreenbufferinfoex-Funktion

Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpconsoleskreenbufferinfoex* \[ vorgenommen\]  
Eine [**\_ \_ \_ INFOEX-Struktur des Konsolenbildschirm Puffers**](console-screen-buffer-infoex.md) , die die angeforderten Konsolenbildschirm Puffer Informationen empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Das Rechteck, das im **srwindow** -Member der [**\_ \_ \_ INFOEX-Struktur der Konsolenbildschirm Puffer**](console-screen-buffer-infoex.md) zurückgegeben wurde, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf im Fenster des Konsolenbildschirm Puffers durchführen, um die Größe des Fensters oder beides zu ändern.

Alle in der INFOEX-Struktur des [**Konsolen \_ Bildschirm \_ Puffers \_**](console-screen-buffer-infoex.md) zurückgegebenen Koordinaten befinden sich in Zeichen Zellen Koordinaten, wobei sich der Ursprung (0, 0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.

> [!TIP]
> Diese API weist keine Entsprechung für ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** auf. Diese Verwendung ist möglicherweise trotzdem für Anwendungen erforderlich, die versuchen, Spalten, Raster oder die Anzeige zu zeichnen, um die Fenstergröße abzurufen. Dieser Fenster Zustand wird von der TTY/Pty/pseudoconsole außerhalb des normalen streamflows verwaltet und in der Regel als Benutzer Berechtigung betrachtet, die von der Client Anwendung nicht angepasst werden kann. Updates können für "read [**ConsoleInput**](readconsoleinput.md)" empfangen werden.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Konsolen \_ Bildschirm- \_ Puffer \_ INFOEX**](console-screen-buffer-infoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)
