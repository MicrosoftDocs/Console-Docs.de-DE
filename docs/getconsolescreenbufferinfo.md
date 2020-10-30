---
title: Getconsoleskreenbufferinfo-Funktion
description: Siehe Referenzinformationen zur getconsoleskreenbufferinfo-Funktion, die Informationen zum angegebenen Konsolenbildschirm Puffer abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 251fc71ef58840a962e5c1e09e88474959de27ae
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038768"
---
# <a name="getconsolescreenbufferinfo-function"></a>Getconsoleskreenbufferinfo-Funktion

Ruft Informationen zum angegebenen Konsolenbildschirm Puffer ab.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpconsoleskreenbufferinfo* \[ vorgenommen\]  
Ein Zeiger auf eine [**Konsolen \_ Bildschirm- \_ Puffer \_ Info**](console-screen-buffer-info-str.md) Struktur, die die Bildschirm Puffer Informationen der Konsole empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Das Rechteck, das im **srwindow** -Member der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben wird, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf des Konsolenbildschirm Puffers im-Fenster durchführen, um die Größe des Fensters zu ändern oder beides.

Alle Koordinaten, die in der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben werden, sind in Zeichen Zell Koordinaten, wobei sich der Ursprung (0,0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.

> [!TIP]
> Diese API weist keine Entsprechung für ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** auf. Diese Verwendung ist möglicherweise trotzdem für Anwendungen erforderlich, die versuchen, Spalten, Raster oder die Anzeige zu zeichnen, um die Fenstergröße abzurufen. Dieser Fenster Zustand wird von der TTY/Pty/pseudoconsole außerhalb des normalen streamflows verwaltet und in der Regel als Benutzer Berechtigung betrachtet, die von der Client Anwendung nicht angepasst werden kann. Updates können für "read [**ConsoleInput**](readconsoleinput.md)" empfangen werden.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Scrollen des Fensters eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md).

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

[**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Fenster-und Bildschirm Puffergröße](window-and-screen-buffer-size.md)
