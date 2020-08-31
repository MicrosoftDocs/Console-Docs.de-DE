---
title: Setconsoleactiveskreenbuffer-Funktion
description: Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f3fa9d79705c95fc0737597886b5562ce1045c45
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060299"
---
# <a name="setconsoleactivescreenbuffer-function"></a>Setconsoleactiveskreenbuffer-Funktion


Legt den angegebenen Bildschirm Puffer auf den aktuell angezeigten Konsolenbildschirm Puffer fest.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Eine Konsole kann über mehrere Bildschirm Puffer verfügen. **Setconsoleactiveskreenbuffer** bestimmt, welche angezeigt wird. Sie können in einen inaktiven Bildschirm Puffer schreiben und dann **setconsoleactiveskreenbuffer** verwenden, um den Inhalt des Puffers anzuzeigen.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).

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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[Konsolenfunktionen](console-functions.md)

[Konsolenbildschirm Puffer](console-screen-buffers.md)

[**"Kreateconsoleskreenbuffer"**](createconsolescreenbuffer.md)

 

 




