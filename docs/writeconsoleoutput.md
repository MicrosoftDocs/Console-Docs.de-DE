---
title: Funktion "Write-consoleoutput"
description: Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: b67f741aafcb067e85d339d550646261a46c273a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037258"
---
# <a name="writeconsoleoutput-function"></a>Funktion "Write-consoleoutput"

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer. Die zu schreibenden Daten werden aus einem rechteckigen rechteckigen Block an einer bestimmten Position im Quell Puffer entnommen.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ in\]  
Die Daten, die in den Konsolenbildschirm Puffer geschrieben werden sollen. Dieser Zeiger wird als Ursprung eines zweidimensionalen Arrays von [**Char \_ Info**](char-info-str.md) -Strukturen behandelt, deren Größe durch den *dwbuffersize* -Parameter angegeben wird.

*dwbuffersize* \[ in\]  
Die Größe des Puffers, auf den durch den *lpBuffer* -Parameter in Zeichen Zellen verwiesen wird. Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die Anzahl der Spalten. der **Y** -Member ist die Anzahl der Zeilen.

*dwbuffercoord* \[ in\]  
Die Koordinaten der linken oberen Zelle im Puffer, auf die durch den *lpBuffer* -Parameter verwiesen wird. Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.

*lpschreiteregion* \[ in, out\]  
Ein Zeiger auf eine [**kleine \_ Rect**](small-rect-str.md) -Struktur. Bei der Eingabe geben die Strukturmember die oberen linken und unteren rechten Koordinaten des Konsolenbildschirm-Puffer Rechtecks an, in das geschrieben werden soll. Bei der Ausgabe geben die Strukturmember das tatsächliche Rechteck an, das verwendet wurde.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

" **Write-consoleoutput** " behandelt den Quell-und den Zielbildschirm Puffer als zweidimensionale Arrays (Spalten und Zeilen von Zeichen Zellen). Das Rechteck, auf das durch den *lpschreiteregion* -Parameter verwiesen wird, gibt die Größe und Position des Blocks an, in den in den Konsolenbildschirm Puffer geschrieben werden soll. Ein Rechteck derselben Größe befindet sich mit seiner oberen linken Zelle an den Koordinaten des Parameters " *dwbuffercoord* " im *lpBuffer* -Array. Daten aus den Zellen, die sich in der Schnittmenge dieses Rechtecks und des Quell Puffer Rechtecks befinden (dessen Dimensionen durch den *dwbuffersize* -Parameter angegeben werden), werden in das Ziel Rechteck geschrieben.

Zellen im Ziel Rechteck, deren zugehöriger Quell Speicherort außerhalb der Grenzen des Quell Puffer Rechtecks liegt, bleiben beim Schreibvorgang unverändert. Das heißt, dass es sich hierbei um die Zellen handelt, für die keine Daten geschrieben werden können.

Vor der Rückgabe von " **Write-consoleoutput** " werden die Member von *lpbeschreib teregion* auf das tatsächliche Bildschirm Puffer Rechteck festgelegt, das von dem Schreibvorgang betroffen ist. Dieses Rechteck reflektiert die Zellen im Ziel Rechteck, für die im Quell Puffer eine entsprechende Zelle vorhanden war, da " **Write-consoleoutput** " die Dimensionen des Ziel Rechtecks auf die Begrenzungen des Konsolenbildschirm Puffers schneidet.

Wenn das von *lpschreiteregion* angegebene Rechteck vollständig außerhalb der Grenzen des Konsolenbildschirm Puffers liegt oder wenn das entsprechende Rechteck vollständig außerhalb der Grenzen des Quell Puffers positioniert ist, werden keine Daten geschrieben. In diesem Fall gibt die-Funktion mit den Elementen der Struktur zurück, auf die durch den *lpschreiteregion* -Parametersatz verwiesen wird, sodass der **Rechte** Member kleiner als der **linke** Wert ist oder der **untere** Member kleiner als der **obere** Wert ist. Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die Größe des Konsolenbildschirm Puffers zu bestimmen.

" **Schreiteconsoleoutput** " hat keine Auswirkung auf die Cursorposition.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Positions Sequenzen für **[Textformatierung](console-virtual-terminal-sequences.md#text-formatting)** und **[Cursor](console-virtual-terminal-sequences.md#cursor-positioning)** . Bewegen Sie den Cursor an den einzufügenden Speicherort, wenden Sie die gewünschte Formatierung an, und schreiben Sie den Text. _Virtuelle Terminal Sequenzen_ werden für alle neuen und laufenden Entwicklungen empfohlen.

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
| Unicode- und ANSI-Name | **Schreibconsoleoutputw** (Unicode) und **schreiteconsoleoutputa** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Char- \_ Informationen**](char-info-str.md)

[**Koord**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**kleine \_ Rect**](small-rect-str.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
