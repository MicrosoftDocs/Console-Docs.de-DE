---
title: Funktion "Beschreib teconsoleinput"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Beschreib teconsoleinput", die Daten direkt in den Konsolen Eingabepuffer schreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 784bed6c1a7b7f7ed9ed204b8483d30371e510a3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060563"
---
# <a name="writeconsoleinput-function"></a>Funktion "Beschreib teconsoleinput"


Schreibt Daten direkt in den Konsolen Eingabepuffer.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ in\]  
Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die Daten enthalten, die in den Eingabepuffer geschrieben werden sollen.

*nlength* \[ in\]  
Die Anzahl der Eingabedaten Sätze, die geschrieben werden sollen.

*lpnumofeventswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Eingabedaten Sätze empfängt.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

" **Write-ConsoleInput** " fügt Eingabedaten Sätze in den Eingabepuffer hinter allen ausstehenden Ereignissen im Puffer ein. Der Eingabepuffer wächst bei Bedarf dynamisch, um so viele Ereignisse zu speichern, wie Sie geschrieben werden.

Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole. Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt. Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .

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
<td><p>Schreiben von " <strong>Write-consolinput w</strong> (Unicode)" und " <strong>Write-consolinput a</strong> " (ANSI)</p></td>
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

[**Eingabe \_ Daten Satz**](input-record-str.md)

[Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)

[**Mapvirtualkey**](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[**"Etekconsoleinput"**](peekconsoleinput.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**Setconsolecp**](setconsolecp.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

[**Vkkeyscan**](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 




