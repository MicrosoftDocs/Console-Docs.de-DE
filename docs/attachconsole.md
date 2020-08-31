---
title: Attachconsole-Funktion
description: Siehe Referenzinformationen über die attachconsole-Funktion, die den aufrufenden Prozess an die Konsole des angegebenen Prozesses anfügt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060234"
---
# <a name="attachconsole-function"></a>Attachconsole-Funktion


Fügt den aufrufenden Prozess an die Konsole des angegebenen Prozesses an.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a>Parameter
----------

*dwProcessId* \[ in\]  
Der Bezeichner des Prozesses, dessen-Konsole verwendet werden soll. Dieser Parameter kann einen der folgenden Werte aufweisen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><em>pid</em></td>
<td><p>Verwenden Sie die Konsole des angegebenen Prozesses.</p></td>
</tr>
<tr class="even">
<td><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</td>
<td><p>Verwenden Sie die Konsole des übergeordneten Elements des aktuellen Prozesses.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Ein Prozess kann höchstens an eine Konsole angefügt werden. Wenn der Aufrufprozess bereits an eine Konsole angefügt ist, lautet der zurückgegebene Fehlercode **Error \_ Access \_ denied** (5). Wenn der angegebene Prozess über keine Konsole verfügt, wird der zurückgegebene Fehlercode ** \_ mit einem ungültigen \_ handle** (6) zurückgegeben. Wenn der angegebene Prozess nicht vorhanden ist, lautet der zurückgegebene Fehlercode " ** \_ ungültiger \_ Parameter** " (87).

Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von seiner Konsole zu trennen. Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen. Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder **freeconsole**aufruft. Nachdem ein Prozess **freeconsole**aufgerufen hat, kann er die Funktion " [**Zuweisung**](allocconsole.md) " aufrufen, um eine neue Konsole **oder eine** anfügekonsole zum Anfügen an eine andere Konsole zu erstellen.

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
<td><p>Windows XP [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2003 [nur Desktop-Apps]</p></td>
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


[Konsolenfunktionen](console-functions.md)

[Trö](consoles.md)

[**"Zuweisung"-Konsole**](allocconsole.md)

[**Freeconsole**](freeconsole.md)

[**Getconsoleprocesslist**](getconsoleprocesslist.md)

 

 




