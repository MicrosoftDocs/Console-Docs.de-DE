---
title: Funktion "Read Console"
description: Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 16287bec8e690e5d70483d6e6055e6badaca40ce
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059578"
---
# <a name="readconsole-function"></a>Funktion "Read Console"


Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der die aus dem Konsolen Eingabepuffer gelesenen Daten empfängt.

*nnumofcharstoread* \[ in\]  
Die Anzahl der zu lesenden Zeichen. Die Größe des Puffers, auf den der *lpBuffer* -Parameter verweist, muss mindestens `nNumberOfCharsToRead * sizeof(TCHAR)` Bytes betragen.

*lpnumofcharsread* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Zeichen empfängt.

*pinputcontrol* \[ in, optional\]  
Ein Zeiger auf eine [**Konsolen-einfügekonsolen- \_ \_ Steuer**](console-readconsole-control.md) Elementstruktur, die ein Steuerzeichen angibt, das das Ende des Lesevorgangs signalisiert. Dieser Parameter kann **null**sein.

Dieser Parameter erfordert standardmäßig Unicode-Eingaben. Legen Sie für den ANSI-Modus diesen Parameter auf **null**fest.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Die **Lese Konsole** liest Tastatureingaben aus dem Eingabepuffer einer Konsole. Sie verhält sich wie die Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) ", mit dem Unterschied, dass Sie entweder in Unicode (Wide-Character) oder ANSI-Modus gelesen werden kann. Verwenden Sie die **infoconsole** anstelle von " **Infofile**", damit Anwendungen, die einen einzelnen Satz von Quellen verwalten, mit beiden Modi kompatibel sind. Obwohl die **infoconsole** nur mit einem Konsolen Eingabepuffer Handle verwendet werden kann, kann die **Infodatei** mit anderen Handles (z. b. Dateien oder Pipes) verwendet werden. Der Wert von "read **Console** " schlägt fehl, wenn er mit einem Standard Handle verwendet wird, das zu einem anderen als einem Konsolen handle umgeleitet wurde.

Alle Eingabemodi, die das Verhalten von " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " beeinflussen, haben in der " **infoconsole**" dieselbe Wirkung. Um die Eingabemodi eines Konsolen Eingabe Puffers abzurufen und festzulegen, verwenden Sie die Funktionen [**getconsolemode**](getconsolemode.md) und [**setconsolemode**](setconsolemode.md) .

Wenn der Eingabepuffer andere Eingabeereignisse als Tastatur Ereignisse enthält (z. b. Mausereignisse oder Ereignisse zum Ändern von Fenstern), werden diese verworfen. Diese Ereignisse können nur mit der Funktion " [**leseconsoleinput**](readconsoleinput.md) " gelesen werden.

Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole. Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt. Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .

Der *pinputcontrol* -Parameter kann verwendet werden, um zwischengeschaltete Aufwecken aus dem Lesevorgang in Reaktion auf ein Steuerzeichen zu aktivieren, das in der [** \_ infoconsole- \_ Steuer**](console-readconsole-control.md) Elementstruktur der Konsole angegeben wird. Diese Funktion erfordert, dass Befehls Erweiterungen aktiviert werden, das Standardausgabe Handle als Konsolenausgabe Handle und Eingabe als Unicode.

**Windows Server 2003 und Windows XP/2000:** Das zwischen Lese Feature wird nicht unterstützt.

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
<td><p>"Read <strong>consolew</strong> (Unicode)" und "read <strong>Consolea</strong> " (ANSI)</p></td>
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

[**Steuerelement für die Konsole der Konsole \_ \_**](console-readconsole-control.md)

[**Getconsolemode**](getconsolemode.md)

[Eingabe-und Ausgabemethoden](input-and-output-methods.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**Setconsolecp**](setconsolecp.md)

[**Setconsolemode**](setconsolemode.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

[**Schreib Konsole**](writeconsole.md)

 

 




