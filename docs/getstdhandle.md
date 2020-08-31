---
title: Getstdhandle-Funktion
description: Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059626"
---
# <a name="getstdhandle-function"></a>Getstdhandle-Funktion


Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).

<a name="syntax"></a>Syntax
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a>Parameter
----------

*nstdhandle* \[ in\]  
Das Standardgerät. Dieser Parameter kann einen der folgenden Werte aufweisen.

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
<td><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</td>
<td><p>Das Standardeingabe Gerät. Anfänglich ist dies der Konsolen Eingabepuffer ("$").</p></td>
</tr>
<tr class="even">
<td><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</td>
<td><p>Das Standardausgabe Gerät. Anfänglich handelt es sich hierbei um den aktiven Konsolenbildschirm Puffer.</p></td>
</tr>
<tr class="odd">
<td><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</td>
<td><p>Das Standardfehler Gerät. Anfänglich handelt es sich hierbei um den aktiven Konsolenbildschirm Puffer.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für das angegebene Gerät oder ein umgeleitetes handle, das durch einen vorherigen-Befehl von [**setstdhandle**](setstdhandle.md)festgelegt wurde. Das Handle verfügt über **allgemeine \_ Lese** -und **allgemeine \_ Schreib** Zugriffsrechte, es sei denn, die Anwendung hat **setstdhandle** verwendet, um ein Standard Handle mit geringerem Zugriff festzulegen.

Wenn die Funktion fehlschlägt, ist der Rückgabewert ein **ungültiger \_ handle- \_ Wert**. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Wenn einer Anwendung keine Standard Handles zugeordnet sind, z. b. ein Dienst, der auf einem interaktiven Desktop ausgeführt wird, und Sie nicht umgeleitet hat, ist der Rückgabewert **null**.

<a name="remarks"></a>Hinweise
-------

Von **getstdhandle** zurückgegebene Handles können von Anwendungen verwendet werden, die aus der Konsole lesen oder in diese schreiben müssen. Wenn eine-Konsole erstellt wird, ist das Standardeingabe Handle ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standard-Fehler Handles sind Handles des aktiven Bildschirm Puffers der Konsole. Diese Handles können von den Funktionen " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**schreitefile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder von einer der Konsolenfunktionen verwendet werden, die auf den Konsolen Eingabepuffer oder einen Bildschirm Puffer zugreifen (z. b. die Funktionen " [**infoconsoleinput**](readconsoleinput.md)", " [**Write Console**](writeconsole.md)" oder " [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) ").

Die Standard Handles eines Prozesses können durch einen aufzurufenden [**setstdhandle**](setstdhandle.md)umgeleitet werden. in diesem Fall gibt **getstdhandle** das umgeleitete Handle zurück. Wenn die Standard Handles umgeleitet wurden, können Sie den Wert von "$" in einem Aufrufen der Funktion "angleichen [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " angeben, um ein Handle für den Eingabepuffer einer Konsole abzurufen. Entsprechend können Sie den Wert für "$ $" angeben, um ein Handle für den aktiven Bildschirm Puffer einer Konsole zu erhalten.

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Verhalten beim Anfügen/trennen

Beim Anfügen an eine neue Konsole werden Standard Handles immer durch Konsolen Handles ersetzt, es sei denn, während der Prozesserstellung wurde **Startf \_ usestdhandles** angegeben.

Wenn der vorhandene Wert des Standard Handles **null**ist, oder wenn der vorhandene Wert des Standard Handles wie ein Konsolen Pseudo handle aussieht, wird das Handle durch ein Konsolen handle ersetzt.

Wenn ein übergeordnetes Element sowohl **Create \_ New \_ Console** als auch **Startf \_ usestdhandles** verwendet, um einen Konsolen Prozess zu erstellen, werden Standard Handles nicht ersetzt, es sei denn, der vorhandene Wert des Standard Handles ist NULL oder ein Konsolen Pseudo handle.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

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
<td>Processenv. h (über Winbase. h, Include Windows. h)</td>
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

[Konsolen Handles](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**Setstdhandle**](setstdhandle.md)

[**Schreib Konsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




