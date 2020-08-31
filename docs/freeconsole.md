---
title: Freeconsole-Funktion
description: Siehe Referenzinformationen zur freeconsole-Funktion, die den aufrufenden Prozess von seiner Konsole trennt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059867"
---
# <a name="freeconsole-function"></a>Freeconsole-Funktion


Trennt den aufrufenden Prozess von seiner Konsole aus.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI FreeConsole(void);
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

Ein Prozess kann höchstens an eine Konsole angefügt werden. Wenn der Aufrufprozess nicht bereits an eine Konsole angefügt ist, lautet der Fehlercode **" \_ ungültiger \_ Parameter** " (87).

Ein Prozess kann die **freeconsole** -Funktion verwenden, um sich von seiner Konsole zu trennen. Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen. Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder **freeconsole**aufruft. Nachdem ein Prozess **freeconsole**aufgerufen hat, kann er die Funktion " [**Zuweisung**](allocconsole.md) " aufrufen, um eine neue Konsole [**oder eine**](attachconsole.md) anfügekonsole zum Anfügen an eine andere Konsole zu erstellen.

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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[**"Zuweisung"-Konsole**](allocconsole.md)

[**Attachconsole**](attachconsole.md)

[Konsolenfunktionen](console-functions.md)

[Trö](consoles.md)

 

 




