---
title: Funktion "Beschreib teconsole"
description: Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060479"
---
# <a name="writeconsole-function"></a>Funktion "Beschreib teconsole"


Schreibt eine Zeichenfolge in einen Konsolenbildschirm Puffer, beginnend an der aktuellen Cursorposition.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ in\]  
Ein Zeiger auf einen Puffer, der Zeichen enthält, die in den Konsolenbildschirm Puffer geschrieben werden sollen.

*nnumofcharstowrite* \[ in\]  
Die Anzahl der zu schreibenden Zeichen. Wenn die Gesamtgröße der angegebenen Anzahl von Zeichen den verfügbaren Heap überschreitet, tritt bei der Funktion ein Fehler auf, und es ist ** \_ nicht \_ genügend Arbeits \_ Speicher**vorhanden.

*lpnumofcharswritten* \[ Out, optional\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.

*lpReserved*   
Bleiben muss **null**sein.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Die Funktion " **Write Console** " schreibt Zeichen an der aktuellen Cursorposition in den Konsolenbildschirm Puffer. Die Cursorposition wird beim Schreiben von Zeichen fortgesetzt. Die [**SetConsoleCursorPosition**](setconsolecursorposition.md) -Funktion legt die aktuelle Cursorposition fest.

Zeichen werden mithilfe der Vordergrund-und Hintergrundfarben Attribute geschrieben, die dem Konsolenbildschirm Puffer zugeordnet sind. Die [**SetConsoleTextAttribute**](setconsoletextattribute.md) -Funktion ändert diese Farben. Zum Ermitteln der aktuellen Farb Attribute und der aktuellen Cursorposition verwenden Sie [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md).

Alle Eingabemodi, die das Verhalten der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " beeinflussen, haben dieselbe Auswirkung auf " **Write Console**". Zum Abrufen und Festlegen der Ausgabe Modi eines Konsolenbildschirm Puffers verwenden Sie die Funktionen [**getconsolemode**](getconsolemode.md) und [**setconsolemode**](setconsolemode.md) .

Die Funktion " **Beschreib teconsole** " verwendet entweder Unicode-Zeichen oder ANSI-Zeichen aus der aktuellen Codepage der Konsole. Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt. Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .

Die **Schreib Konsole** schlägt fehl, wenn Sie mit einem Standard Handle verwendet wird, das zu einer Datei umgeleitet wird. Wenn eine Anwendung mehrsprachige Ausgaben verarbeitet, die umgeleitet werden können, bestimmen Sie, ob das Ausgabe Handle ein Konsolen Handle ist (eine Methode besteht darin, die [**getconsolemode**](getconsolemode.md) -Funktion aufzurufen und zu überprüfen, ob Sie erfolgreich ist). Wenn das Handle ein Konsolen Handle ist, müssen Sie " **Write-Console**" anrufen. Wenn das Handle kein Konsolen Handle ist, wird die Ausgabe umgeleitet, und Sie sollten " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " zum Ausführen des e/a-Vorgangs aufruft. Stellen Sie sicher, dass eine Unicode-nur-Text-Datei mit einer Byte Reihenfolge Markierung versehen wird. Weitere Informationen finden Sie unter [Verwenden von Byte Reihenfolge Markierungen](https://msdn.microsoft.com/library/windows/desktop/dd374101).

Obwohl eine Anwendung über die Schreib **Konsole** im ANSI-Modus zum Schreiben von ANSI-Zeichen verwendet werden kann, unterstützen-Konsolen keine ANSI-Escapesequenzen. Einige Funktionen bieten jedoch äquivalente Funktionalität. Weitere Informationen finden Sie unter [**setcurrsorpos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)und [**getconsolecursorinfo**](getconsolecursorinfo.md).

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
<td>Consoleapi. h (über WinCon. h, Include Windows. h)</td>
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
<td><p>" <strong>Schreibconsolew</strong> (Unicode)" und " <strong>Beschreib teconsolea</strong> " (ANSI)</p></td>
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

[**Getconsolecursorinfo**](getconsolecursorinfo.md)

[**Getconsolemode**](getconsolemode.md)

[**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)

[Eingabe-und Ausgabemethoden](input-and-output-methods.md)

[**"Read Console"**](readconsole.md)

[**Setconsolecp**](setconsolecp.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**Setconsolemode**](setconsolemode.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**Setcurrsorpos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




