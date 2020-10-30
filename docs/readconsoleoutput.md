---
title: Funktion "Read consoleoutput"
description: Liest Zeichen-und Farb Attributdaten aus einem rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer und schreibt Daten in den Ziel Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0ce2a5a62ee7719d0184247c9ef3327850e12c1b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037758"
---
# <a name="readconsoleoutput-function"></a>Funktion "Read consoleoutput"

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Liest Zeichen-und Farb Attributdaten aus einem rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer, und die-Funktion schreibt die Daten in einen rechteckigen Block an einer bestimmten Position im Ziel Puffer.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ vorgenommen\]  
Ein Zeiger auf einen Ziel Puffer, der die aus dem Konsolenbildschirm Puffer gelesenen Daten empfängt. Dieser Zeiger wird als Ursprung eines zweidimensionalen Arrays von [**Char \_ Info**](char-info-str.md) -Strukturen behandelt, deren Größe durch den *dwbuffersize* -Parameter angegeben wird.

*dwbuffersize* \[ in\]  
Die Größe des *lpBuffer* -Parameters in Zeichen Zellen. Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die Anzahl der Spalten. der **Y** -Member ist die Anzahl der Zeilen.

*dwbuffercoord* \[ in\]  
Die Koordinaten der linken oberen Zelle im *lpBuffer* -Parameter, die die aus dem Konsolenbildschirm Puffer gelesenen Daten empfängt. Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.

*lpreadregion* \[ in, out\]  
Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur. Bei der Eingabe geben die Strukturmember die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks an, von dem die Funktion gelesen werden soll. Bei der Ausgabe geben die Strukturmember das tatsächliche Rechteck an, das verwendet wurde.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Der Bildschirm Puffer der Konsole und der Ziel Puffer werden von "read **consoleoutput** " als zweidimensionale Arrays (Spalten und Zeilen von Zeichen Zellen) behandelt. Das Rechteck, auf das durch den *lpreadregion* -Parameter verwiesen wird, gibt die Größe und Position des Blocks an, der aus dem Konsolenbildschirm Puffer gelesen werden soll. Ein Ziel Rechteck derselben Größe befindet sich mit seiner oberen linken Zelle an den Koordinaten des Parameters " *dwbuffercoord* " im *lpBuffer* -Array. Aus den Zellen des Konsolenbildschirm-Puffer Quell Rechtecks gelesene Daten werden in die entsprechenden Zellen im Ziel Puffer kopiert. Wenn sich die entsprechende Zelle außerhalb der Grenzen des Ziel Puffer Rechtecks befindet (dessen Abmessungen durch den *dwbuffersize* -Parameter angegeben werden), werden die Daten nicht kopiert.

Zellen im Ziel Puffer, die den Koordinaten entsprechen, die sich nicht innerhalb der Grenzen des Konsolenbildschirm Puffers befinden, bleiben unverändert. Anders ausgedrückt: Dies sind die Zellen, für die keine Bildschirm Puffer Daten zum Lesen verfügbar sind.

Vor der Rückgabe von "read **consoleoutput** " werden die Member der Struktur, auf die durch den *lpreadregion* -Parameter verwiesen wird, auf das tatsächliche Bildschirm Puffer Rechteck festgelegt, dessen Zellen in den Ziel Puffer kopiert wurden. Dieses Rechteck reflektiert die Zellen im Quell Rechteck, für die im Ziel Puffer eine entsprechende Zelle vorhanden war, da die Dimensionen des Quell Rechtecks von "read **consoleoutput** " an die Grenzen des Konsolenbildschirm Puffers angepasst werden.

Wenn das von *lpreadregion* angegebene Rechteck vollständig außerhalb der Grenzen des Konsolenbildschirm Puffers liegt oder das entsprechende Rechteck vollständig außerhalb der Grenzen des Ziel Puffers positioniert ist, werden keine Daten kopiert. In diesem Fall gibt die-Funktion mit den Elementen der Struktur zurück, auf die durch den *lpreadregion* -Parametersatz verwiesen wird, sodass der **Rechte** Member kleiner als der **linke** Wert ist oder der **untere** Member kleiner als der **obere** Wert ist. Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die Größe des Konsolenbildschirm Puffers zu bestimmen.

Die Funktion "read **consoleoutput** " hat keine Auswirkung auf die Cursorposition des Konsolenbildschirm Puffers. Der Inhalt des Konsolenbildschirm Puffers wird von der-Funktion nicht geändert.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | "Read **consoleoutputw** (Unicode)" und "read **consoleoutputa** " (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**kleine \_ Rect**](small-rect-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**Char- \_ Informationen**](char-info-str.md)

[**Koord**](coord-str.md)
