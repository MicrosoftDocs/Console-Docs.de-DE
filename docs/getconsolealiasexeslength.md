---
title: Getconsolealiasexeslength-Funktion
description: Ruft die erforderliche Größe für den Puffer ab, der von der getconsolealiasexes-Funktion verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0f4459254e9382a0c784ceb2c214af056087ab1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059802"
---
# <a name="getconsolealiasexeslength-function"></a>Getconsolealiasexeslength-Funktion


Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiasexes**](getconsolealiasexes.md) -Funktion verwendet wird.

<a name="syntax"></a>Syntax
------

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

<a name="parameters"></a>Parameter
----------

Diese Funktion besitzt keine Parameter.

<a name="return-value"></a>Rückgabewert
------------

Die Größe des Puffers, der zum Speichern der Namen aller ausführbaren Dateien erforderlich ist, für die Konsolen Aliase definiert sind (in Bytes).

<a name="remarks"></a>Hinweise
-------

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
<td><p><strong>Getconsolealiasexeslengthw</strong> (Unicode) und <strong>getconsolealiasexeslengtha</strong> (ANSI)</p></td>
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

[**Getconsolealiases**](getconsolealiases.md)

[**Getconsolealiasexes**](getconsolealiasexes.md)

 

 




