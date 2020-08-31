---
title: Scrollconsoleskreenbuffer-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur scrollconsoleskreenbuffer-Funktion, die einen Datenblock in einem Bildschirm Puffer verschiebt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: f0dd67ecc28907913e10efa8c06a544656d08dc6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060338"
---
# <a name="scrollconsolescreenbuffer-function"></a>Scrollconsoleskreenbuffer-Funktion


Verschiebt einen Datenblock in einem Bildschirm Puffer. Die Auswirkungen des Verschiebens können durch Angabe eines clippingrechtecks eingeschränkt werden, sodass der Inhalt des Konsolenbildschirm Puffers außerhalb des clippingrechtecks unverändert bleibt.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpscrollrechteck* \[ in\]  
Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, deren Member die Links oben und rechts unten des Konsolenbildschirm-Puffer Rechtecks angibt, das verschoben werden soll.

*lpcliprectangle* \[ in, optional\]  
Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, deren Member die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks angibt, das durch Scrollen beeinflusst wird. Dieser Zeiger kann **null**sein.

*dwdestinationorigin* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die linke obere Ecke der neuen Position des *lpscrollrechteck* -Inhalts in Zeichen angibt.

*lpfill* \[ in\]  
Ein Zeiger auf eine [**Char \_ Info**](char-info-str.md) -Struktur, die die Zeichen-und Farb Attribute angibt, die zum Auffüllen der Zellen innerhalb der Schnittmenge von *lpscrollrechteck* und *lpcliprectangle* verwendet werden sollen, die als Ergebnis der Verschiebung leer gelassen wurden.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

**Scrollconsoleskreenbuffer** kopiert den Inhalt eines rechteckigen Bereichs eines Bildschirm Puffers, der durch den *lpscrollrechteck* -Parameter angegeben ist, in einen anderen Bereich des Konsolenbildschirm Puffers. Das Ziel Rechteck hat die gleichen Dimensionen wie das *lpscrollrechteck* -Rechteck mit seiner oberen linken Ecke an den Koordinaten, die durch den *dwdestinationorigin* -Parameter angegeben werden. Die Teile von *lpscrollrechteck* , die sich nicht mit dem Ziel Rechteck überlappen, werden mit den Zeichen-und Farb Attributen aufgefüllt, die durch den *lpfill* -Parameter angegeben werden.

Das Clippingrechteck gilt für Änderungen, die sowohl im *lpscrollrechteck* -Rechteck als auch im Ziel Rechteck vorgenommen wurden. Wenn das Clippingrechteck z. b. keinen Bereich enthält, der durch den Inhalt von *lpfill*aufgefüllt wäre, bleibt der ursprüngliche Inhalt des Bereichs unverändert.

Wenn die Bild Lauf-oder Zielbereiche die Abmessungen des Konsolenbildschirm Puffers überschreiten, werden Sie abgeschnitten. Wenn z. b. *lpscrollrechteck* der in (0,0) und (19, 19) enthaltene Bereich und *dwdestinationorigin* (10, 15) ist, ist das Ziel Rechteck der Bereich, der in (10, 15) und (29, 34) enthalten ist. Wenn der Bildschirm Puffer der Konsole jedoch 50 Zeichen breit und 30 Zeichen hoch ist, wird das Ziel Rechteck auf (10, 15) und (29, 29) zugeschnitten. Änderungen am Konsolenbildschirm Puffer werden auch gemäß *lpcliprectangle*abgeschnitten, wenn der Parameter eine [**kleine \_ Rect**](small-rect-str.md) -Struktur angibt. Wenn das Clippingrechteck als (0,0) und (49, 19) angegeben wird, werden nur die Änderungen vorgenommen, die in diesem Bereich des Konsolenbildschirm Puffers auftreten.

Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole. Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt. Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).

<a name="requirements"></a>Anforderungen
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Unterstützte Mindestversion (Client)</p></td>
<td><p>Windows 2000 Professional [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows 2000 Server [nur Desktop-Apps]</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>ConsoleApi2. h (über WinCon. h, Include Windows. h)</td>
</tr>
<tr class="even">
<td><p>Bibliothek</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
<td><p>Unicode- und ANSI-Name</p></td>
<td><p><strong>Scrollconsoleskreenbufferw</strong> (Unicode) und <strong>scrollconsoleskreenbuffera</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**Char- \_ Informationen**](char-info-str.md)

[Konsolenfunktionen](console-functions.md)

[**Koord**](coord-str.md)

[Scrollen des Bildschirm Puffers](scrolling-the-screen-buffer.md)

[**Setconsolecp**](setconsolecp.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

[**Setconsolewindowinfo**](setconsolewindowinfo.md)

[**kleine \_ Rect**](small-rect-str.md)

 

 




