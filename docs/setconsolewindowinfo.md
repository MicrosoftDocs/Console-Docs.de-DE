---
title: Setconsolewindowinfo-Funktion
description: Legt die aktuelle Größe und Position des Fensters eines Konsolenbildschirm Puffers fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc1190aee7cb1a29c60579f5e00daf1f7280d292
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039308"
---
# <a name="setconsolewindowinfo-function"></a>Setconsolewindowinfo-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Legt die aktuelle Größe und Position des Fensters eines Konsolenbildschirm Puffers fest.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*babsolute* \[ in\]  
Wenn dieser Parameter auf **true** festgelegt ist, geben die Koordinaten die neuen oberen linken und unteren rechten Ecke des Fensters an. Wenn der Wert **false** ist, sind die Koordinaten relativ zu den aktuellen Fenstern der Fenster Ecke.

*lpconsolewindow* \[ in\]  
Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, die die neuen oberen linken und unteren rechten Ecke des Fensters angibt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Die Funktion schlägt fehl, wenn das angegebene Fenster Rechteck die Grenzen des Konsolenbildschirm Puffers überschreitet. Dies bedeutet, dass die **oberen** und **linken** Member des *lpconsolewindow* -Rechtecks (oder die berechneten oberen und linken Koordinaten, wenn *babsolute* false ist) nicht kleiner als 0 (null) sein dürfen. Entsprechend dürfen die **unteren** und **rechten** Elemente (oder die berechneten unteren und rechten Koordinaten) nicht größer sein als (Bildschirm Puffer Höhe – 1) und (Bildschirm Puffer Breite – 1). Die-Funktion schlägt auch fehl, wenn das **Rechte** Element (oder die berechnete rechte Koordinate) kleiner als oder gleich dem **linken** Member (oder der berechneten linken Koordinate) ist oder wenn der **untere** Member (oder die berechnete untere Koordinate) kleiner oder gleich dem **oberen** Element (oder der berechneten oberen Koordinate) ist.

Bei-Konsolen mit mehr als einem Bildschirm Puffer wirkt sich das Ändern der Fensterposition für einen Bildschirm Puffer nicht auf die Fensterpositionen der anderen Bildschirm Puffer aus.

Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die aktuelle Größe und Position des Fensters eines Bildschirm Puffers zu bestimmen. Diese Funktion gibt auch die maximale Größe des Fensters zurück, wenn die aktuelle Bildschirm Puffergröße, die aktuelle Schriftgröße und die Bildschirmgröße angegeben sind. Die [**getlargestconsolewindowsize**](getlargestconsolewindowsize.md) -Funktion gibt die maximale Fenstergröße in Anbetracht der aktuellen Schriftart und Bildschirmgröße zurück, berücksichtigt jedoch nicht die Größe des Konsolenbildschirm Puffers.

**Setconsolewindowinfo** kann verwendet werden, um den Inhalt des Konsolenbildschirm Puffers durch Verschieben der Position des Fenster Rechtecks zu scrollen, ohne seine Größe zu ändern.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[Scrollen des Bildschirm Puffers](scrolling-the-screen-buffer.md)

[**kleine \_ Rect**](small-rect-str.md)
