---
title: Getlargestconsolewindowsize-Funktion
description: Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059690"
---
# <a name="getlargestconsolewindowsize-function"></a>Getlargestconsolewindowsize-Funktion


Ruft die Größe des größtmöglichen Konsolenfensters basierend auf der aktuellen Schriftart und der Größe der Anzeige ab.

<a name="syntax"></a>Syntax
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert eine [**coord**](coord-str.md) -Struktur, die die Anzahl der Zeichen Zellen Spalten (**X** -Member) und der Zeilen (**Y** -Member) im größtmöglichen Konsolenfenster angibt. Andernfalls sind die Elemente der-Struktur 0 (null).

Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Die-Funktion berücksichtigt nicht die Größe des Bildschirm Puffers der Konsole. Dies bedeutet, dass die zurückgegebene Fenstergröße möglicherweise größer als die Größe des Konsolenbildschirm Puffers ist. Mithilfe der [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion kann die maximale Größe des Konsolenfensters anhand der aktuellen Bildschirm Puffergröße, der aktuellen Schriftart und der Anzeige Größe bestimmt werden.

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

[**Koord**](coord-str.md)

[**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)

[**Setconsolewindowinfo**](setconsolewindowinfo.md)

[Fenster-und Bildschirm Puffergröße](window-and-screen-buffer-size.md)

 

 




