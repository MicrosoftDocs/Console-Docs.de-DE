---
title: SetConsoleCursorPosition-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur SetConsoleCursorPosition-Funktion, mit der die Cursorposition im angegebenen Konsolenbildschirm Puffer festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: eaa50df16248597f1054f0741113ecc9be1f3264
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060274"
---
# <a name="setconsolecursorposition-function"></a>SetConsoleCursorPosition-Funktion


Legt die Cursorposition im angegebenen Konsolenbildschirm Puffer fest.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*dwcurrsorposition* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die neue Cursorposition in Zeichen angibt. Die Koordinaten sind die Spalte und die Zeile einer Bildschirm Puffer-Zeichen Zelle. Die Koordinaten müssen sich innerhalb der Grenzen des Konsolenbildschirm Puffers befinden.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Die Cursorposition bestimmt, wo Zeichen, die von der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder " [**Write-Console**](writeconsole.md) " geschrieben wurden oder von der Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " angezeigt werden, angezeigt werden. Verwenden Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion, um die aktuelle Position des Cursors zu ermitteln.

Wenn sich die neue Cursorposition nicht innerhalb der Grenzen des Fensters des Konsolenbildschirm Puffers befindet, wird der Fenster Ursprung geändert, um den Cursor sichtbar zu machen.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Verwenden der übergeordneten Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).

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

[**Getconsolecursorinfo**](getconsolecursorinfo.md)

[**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)

[**"Read Console"**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**Setconsolecursorinfo**](setconsolecursorinfo.md)

[**Schreib Konsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




