---
title: Funktion "Write-consoleoutput"
description: Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059563"
---
# <a name="writeconsoleoutput-function"></a>Funktion "Write-consoleoutput"


Schreibt Zeichen-und Farb Attributdaten in einen angegebenen rechteckigen Block von Zeichen Zellen in einem Konsolenbildschirm Puffer. Die zu schreibenden Daten werden aus einem rechteckigen rechteckigen Block an einer bestimmten Position im Quell Puffer entnommen.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a>Parameter
----------

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

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

" **Write-consoleoutput** " behandelt den Quell-und den Zielbildschirm Puffer als zweidimensionale Arrays (Spalten und Zeilen von Zeichen Zellen). Das Rechteck, auf das durch den *lpschreiteregion* -Parameter verwiesen wird, gibt die Größe und Position des Blocks an, in den in den Konsolenbildschirm Puffer geschrieben werden soll. Ein Rechteck derselben Größe befindet sich mit seiner oberen linken Zelle an den Koordinaten des Parameters " *dwbuffercoord* " im *lpBuffer* -Array. Daten aus den Zellen, die sich in der Schnittmenge dieses Rechtecks und des Quell Puffer Rechtecks befinden (dessen Dimensionen durch den *dwbuffersize* -Parameter angegeben werden), werden in das Ziel Rechteck geschrieben.

Zellen im Ziel Rechteck, deren zugehöriger Quell Speicherort außerhalb der Grenzen des Quell Puffer Rechtecks liegt, bleiben beim Schreibvorgang unverändert. Das heißt, dass es sich hierbei um die Zellen handelt, für die keine Daten geschrieben werden können.

Vor der Rückgabe von " **Write-consoleoutput** " werden die Member von *lpbeschreib teregion* auf das tatsächliche Bildschirm Puffer Rechteck festgelegt, das von dem Schreibvorgang betroffen ist. Dieses Rechteck reflektiert die Zellen im Ziel Rechteck, für die im Quell Puffer eine entsprechende Zelle vorhanden war, da " **Write-consoleoutput** " die Dimensionen des Ziel Rechtecks auf die Begrenzungen des Konsolenbildschirm Puffers schneidet.

Wenn das von *lpschreiteregion* angegebene Rechteck vollständig außerhalb der Grenzen des Konsolenbildschirm Puffers liegt oder wenn das entsprechende Rechteck vollständig außerhalb der Grenzen des Quell Puffers positioniert ist, werden keine Daten geschrieben. In diesem Fall gibt die-Funktion mit den Elementen der Struktur zurück, auf die durch den *lpschreiteregion* -Parametersatz verwiesen wird, sodass der **Rechte** Member kleiner als der **linke**Wert ist oder der **untere** Member kleiner als der **obere**Wert ist. Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die Größe des Konsolenbildschirm Puffers zu bestimmen.

" **Schreiteconsoleoutput** " hat keine Auswirkung auf die Cursorposition.

Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole. Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt. Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).

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
<td><p><strong>Schreibconsoleoutputw</strong> (Unicode) und <strong>schreiteconsoleoutputa</strong> (ANSI)</p></td>
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


[Konsolenfunktionen](console-functions.md)

[**Char- \_ Informationen**](char-info-str.md)

[**Koord**](coord-str.md)

[**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**"Read consoleoutput"**](readconsoleoutput.md)

[**"Read consoleoutputattribute"**](readconsoleoutputattribute.md)

[**"Read consoleoutputcharacter"**](readconsoleoutputcharacter.md)

[**Setconsolecp**](setconsolecp.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

[**kleine \_ Rect**](small-rect-str.md)

[**"Schreibconsoleoutputattribute"**](writeconsoleoutputattribute.md)

[**Schreibconsoleoutputcharacter**](writeconsoleoutputcharacter.md)

 

 




