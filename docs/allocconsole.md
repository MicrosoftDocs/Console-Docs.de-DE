---
title: "\"Zuweisung\"-Funktion"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Zuweisung", die eine neue Konsole für den aufrufenden Prozess zugeordnet.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 2e06cdc82c4e58dd09b99fa08bf4917ad37b552f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060243"
---
# <a name="allocconsole-function"></a>"Zuweisung"-Funktion


Weist eine neue Konsole für den aufrufenden Prozess zu.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI AllocConsole(void);
```

<a name="parameters"></a>Parameter
----------

Diese Funktion besitzt keine Parameter.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Ein Prozess kann nur mit einer Konsole verknüpft werden, sodass die Funktion " **Zuordnungs Konsole** " fehlschlägt, wenn der aufrufende Prozess bereits über eine Konsole verfügt. Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von der aktuellen Konsole zu trennen, und dann kann die Zuweisung von "- **Konsole** " zum Erstellen einer neuen Konsole oder einer [**attachconsole**](attachconsole.md) zum Anfügen an eine andere Konsole durchführen.

Wenn der aufrufenden Prozess einen untergeordneten Prozess erstellt, erbt das untergeordnete Element die neue Konsole.

" **Zugskonsole** " initialisiert Standard Eingaben, Standardausgabe und Standardfehler Handles für die neue Konsole. Das Standardeingabe Handle ist ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standardfehler Handles sind Handles für den Bildschirm Puffer der Konsole. Um diese Handles abzurufen, verwenden Sie die [**getstdhandle**](getstdhandle.md) -Funktion.

Diese Funktion wird hauptsächlich von einer grafischen Benutzeroberflächen Anwendung (GUI) zum Erstellen eines Konsolenfensters verwendet. GUI-Anwendungen werden ohne eine-Konsole initialisiert. Konsolen Anwendungen werden mit einer-Konsole initialisiert, es sei denn, Sie werden als getrennte Prozesse erstellt (durch Aufrufen der [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) -Funktion mit dem getrennten ** \_ prozessflag** ).

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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[Konsolenfunktionen](console-functions.md)

[Trö](consoles.md)

[**Attachconsole**](attachconsole.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**Freeconsole**](freeconsole.md)

[**Getstdhandle**](getstdhandle.md)

 

 




