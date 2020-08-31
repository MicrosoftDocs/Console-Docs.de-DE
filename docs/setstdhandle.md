---
title: Setstdhandle-Funktion
description: Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 6ab17a2162d31c956ec64dbb33696c20ae085298
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060531"
---
# <a name="setstdhandle-function"></a>Setstdhandle-Funktion


Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.

<a name="syntax"></a>Syntax
------

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

<a name="parameters"></a>Parameter
----------

*nstdhandle* \[ in\]  
Das Standardgerät, für das das Handle festgelegt werden soll. Dieser Parameter kann einen der folgenden Werte aufweisen.

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
<td><p>Das Standardeingabe Gerät.</p></td>
</tr>
<tr class="even">
<td><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</td>
<td><p>Das Standardausgabe Gerät.</p></td>
</tr>
<tr class="odd">
<td><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</td>
<td><p>Das Standardfehler Gerät.</p></td>
</tr>
</tbody>
</table>

 

*hHandle* \[ in\]  
Das Handle für das Standardgerät.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Die Standard Handles eines Prozesses wurden möglicherweise durch einen Aufrufen von **setstdhandle**umgeleitet. in diesem Fall gibt [**getstdhandle**](getstdhandle.md) das umgeleitete Handle zurück. Wenn die Standard Handles umgeleitet wurden, können Sie den Wert von "$" in einem Aufrufen der Funktion "angleichen [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " angeben, um ein Handle für den Eingabepuffer einer Konsole abzurufen. Entsprechend können Sie den Wert für "$ $" angeben, um ein Handle für den aktiven Bildschirm Puffer der Konsole zu erhalten.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Erstellen eines untergeordneten Prozesses mit umgeleiteter Eingabe und Ausgabe](https://msdn.microsoft.com/library/windows/desktop/ms682499).

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

[**Getstdhandle**](getstdhandle.md)

 

 




