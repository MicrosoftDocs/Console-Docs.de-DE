---
title: Scrollconsoleskreenbuffer-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur scrollconsoleskreenbuffer-Funktion, die einen Datenblock in einem Bildschirm Puffer verschiebt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4ebe6efa246d627add041a5ef188fbb81294fb61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039458"
---
# <a name="scrollconsolescreenbuffer-function"></a>Scrollconsoleskreenbuffer-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Verschiebt einen Datenblock in einem Bildschirm Puffer. Die Auswirkungen des Verschiebens können durch Angabe eines clippingrechtecks eingeschränkt werden, sodass der Inhalt des Konsolenbildschirm Puffers außerhalb des clippingrechtecks unverändert bleibt.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpscrollrechteck* \[ in\]  
Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, deren Member die Links oben und rechts unten des Konsolenbildschirm-Puffer Rechtecks angibt, das verschoben werden soll.

*lpcliprectangle* \[ in, optional\]  
Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, deren Member die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks angibt, das durch Scrollen beeinflusst wird. Dieser Zeiger kann **null** sein.

*dwdestinationorigin* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die linke obere Ecke der neuen Position des *lpscrollrechteck* -Inhalts in Zeichen angibt.

*lpfill* \[ in\]  
Ein Zeiger auf eine [**Char \_ Info**](char-info-str.md) -Struktur, die die Zeichen-und Farb Attribute angibt, die zum Auffüllen der Zellen innerhalb der Schnittmenge von *lpscrollrechteck* und *lpcliprectangle* verwendet werden sollen, die als Ergebnis der Verschiebung leer gelassen wurden.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

**Scrollconsoleskreenbuffer** kopiert den Inhalt eines rechteckigen Bereichs eines Bildschirm Puffers, der durch den *lpscrollrechteck* -Parameter angegeben ist, in einen anderen Bereich des Konsolenbildschirm Puffers. Das Ziel Rechteck hat die gleichen Dimensionen wie das *lpscrollrechteck* -Rechteck mit seiner oberen linken Ecke an den Koordinaten, die durch den *dwdestinationorigin* -Parameter angegeben werden. Die Teile von *lpscrollrechteck* , die sich nicht mit dem Ziel Rechteck überlappen, werden mit den Zeichen-und Farb Attributen aufgefüllt, die durch den *lpfill* -Parameter angegeben werden.

Das Clippingrechteck gilt für Änderungen, die sowohl im *lpscrollrechteck* -Rechteck als auch im Ziel Rechteck vorgenommen wurden. Wenn das Clippingrechteck z. b. keinen Bereich enthält, der durch den Inhalt von *lpfill* aufgefüllt wäre, bleibt der ursprüngliche Inhalt des Bereichs unverändert.

Wenn die Bild Lauf-oder Zielbereiche die Abmessungen des Konsolenbildschirm Puffers überschreiten, werden Sie abgeschnitten. Wenn z. b. *lpscrollrechteck* der in (0,0) und (19, 19) enthaltene Bereich und *dwdestinationorigin* (10, 15) ist, ist das Ziel Rechteck der Bereich, der in (10, 15) und (29, 34) enthalten ist. Wenn der Bildschirm Puffer der Konsole jedoch 50 Zeichen breit und 30 Zeichen hoch ist, wird das Ziel Rechteck auf (10, 15) und (29, 29) zugeschnitten. Änderungen am Konsolenbildschirm Puffer werden auch gemäß *lpcliprectangle* abgeschnitten, wenn der Parameter eine [**kleine \_ Rect**](small-rect-str.md) -Struktur angibt. Wenn das Clippingrechteck als (0,0) und (49, 19) angegeben wird, werden nur die Änderungen vorgenommen, die in diesem Bereich des Konsolenbildschirm Puffers auftreten.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** . Die Verwendung von kann mit Bild Lauf **[Rändern](console-virtual-terminal-sequences.md#scrolling-margins)** , die **[Cursor Positionierung](console-virtual-terminal-sequences.md#cursor-positioning)** zum Festlegen der aktiven Position außerhalb des Bereichs und Zeilen Vorgängen zum Erzwingen von Text verschoben werden. Der verbleibende Speicherplatz kann durch Verschieben des Cursors, **[festlegen grafischer Attribute](console-virtual-terminal-sequences.md#text-formatting)** und Schreiben von normalem Text aufgefüllt werden.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Scrollconsoleskreenbufferw** (Unicode) und **scrollconsoleskreenbuffera** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[**Char- \_ Informationen**](char-info-str.md)

[Konsolenfunktionen](console-functions.md)

[**Koord**](coord-str.md)

[Scrollen des Bildschirm Puffers](scrolling-the-screen-buffer.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[**kleine \_ Rect**](small-rect-str.md)
