---
title: Getconsolealiases-Funktion
description: Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9e8e28323d5b696390d574a86561d7414f419bcc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059818"
---
# <a name="getconsolealiases-function"></a>Getconsolealiases-Funktion


Ruft alle definierten Konsolen Aliase für die angegebene ausführbare Datei ab.

<a name="syntax"></a>Syntax
------

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a>Parameter
----------

*lpaliasbuffer* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der die Aliase empfängt.

Das Format der Daten lautet wie folgt: *Quelle1* = *Target1* \\ 0*source2* = *TARGET2* \\ 0... *Sourcen* = *Targetn* \\ 0, wobei *N* die Anzahl der definierten Konsolen Aliase ist.

*Aliasbufferlength* \[ in\]  
Die Größe des Puffers, auf den *lpaliasbuffer*zeigt (in Bytes).

*lpexename* \[ in\]  
Die ausführbare Datei, deren Aliase abgerufen werden sollen.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Verwenden Sie die [**getconsolealiaseslength**](getconsolealiaseslength.md) -Funktion, um die erforderliche Größe für den *lpexename* -Puffer zu ermitteln.

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie ** \_ Win32 \_ Winnt** als 0x0501 oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td>ConsoleApi3. h (über WinCon. h, Include Windows. h)</td>
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
<td><p><strong>Getconsolealiasesw</strong> (Unicode) und <strong>getconsolealiasesa</strong> (ANSI)</p></td>
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


[**Addconsolealias**](addconsolealias.md)

[Konsolen Aliase](console-aliases.md)

[Konsolenfunktionen](console-functions.md)

[**Getconsolealias**](getconsolealias.md)

[**Getconsolealiaseslength**](getconsolealiaseslength.md)

[**Getconsolealiasexes**](getconsolealiasexes.md)

 

 




