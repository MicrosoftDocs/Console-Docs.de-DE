---
title: Getconsoletitle-Funktion
description: Ruft den Titel und die Größe des Titels für das aktuelle Konsolenfenster ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059699"
---
# <a name="getconsoletitle-function"></a>Getconsoletitle-Funktion


Ruft den Titel für das aktuelle Konsolenfenster ab.

<a name="syntax"></a>Syntax
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a>Parameter
----------

*lpconsoletitle* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem Titel empfängt. Wenn der Puffer zu klein ist, um den Titel zu speichern, speichert die Funktion so viele Zeichen des Titels, wie Sie in den Puffer passt, und endet mit einem NULL-Terminator.

*nSize* \[ in\]  
Die Größe des Puffers, auf den der *lpconsoletitle* -Parameter zeigt (in Zeichen).

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, entspricht der Rückgabewert der Länge des Konsolenfenster Titels in Zeichen.

Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.

<a name="remarks"></a>Hinweise
-------

Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion. Um die ursprüngliche Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoleoriginaltitle**](getconsoleoriginaltitle.md) -Funktion.

Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole. Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt. Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [**setconsoletitle**](setconsoletitle.md).

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
<td><p><strong>Getconsoletitlew</strong> (Unicode) und <strong>getconsoletitlea</strong> (ANSI)</p></td>
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

[**Getconsoleoriginaltitle**](getconsoleoriginaltitle.md)

[**Setconsolecp**](setconsolecp.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

[**Setconsoletitle**](setconsoletitle.md)

 

 




