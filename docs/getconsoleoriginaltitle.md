---
title: Getconsoleoriginaltitle-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur getconsoleoriginaltitle-Funktion, die den ursprünglichen Titel für das aktuelle Konsolenfenster abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059738"
---
# <a name="getconsoleoriginaltitle-function"></a>Getconsoleoriginaltitle-Funktion


Ruft den ursprünglichen Titel für das aktuelle Konsolenfenster ab.

<a name="syntax"></a>Syntax
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a>Parameter
----------

*lpconsoletitle* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem ursprünglichen Titel empfängt.

*nSize* \[ in\]  
Die Größe des *lpconsoletitle* -Puffers in Zeichen.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert die Länge der Zeichenfolge, die in den Puffer kopiert wird (in Zeichen).

Wenn der Puffer nicht groß genug ist, um den Titel zu speichern, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt eine ** \_ erfolgreiche Fehlermeldung**zurück.

Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.

<a name="remarks"></a>Hinweise
-------

Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion. Um die aktuelle Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoletitle**](getconsoletitle.md) -Funktion.

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie ** \_ Win32 \_ Winnt** als 0x0600 sein oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows Vista [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2008 [nur Desktop-Apps]</p></td>
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
<td><p><strong>Getconsoleoriginaltitlew</strong> (Unicode) und <strong>getconsoleoriginaltitlea</strong> (ANSI)</p></td>
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

[**Getconsoletitle**](getconsoletitle.md)

[**Setconsoletitle**](setconsoletitle.md)

 

 




