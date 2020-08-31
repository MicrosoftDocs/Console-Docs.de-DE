---
title: Getnumofconfiguration Manager-Funktion
description: Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060443"
---
# <a name="getnumberofconsolemousebuttons-function"></a>Getnumofconfiguration Manager-Funktion


Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a>Parameter
----------

*lpnumofmoulbuttons* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der Maustasten empfängt.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Wenn eine Konsole eine Mauseingabe empfängt, wird eine [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur, die eine [** \_ \_ Daten Satzstruktur des Maus Ereignisses**](mouse-event-record-str.md) enthält, in den Eingabepuffer der Konsole eingefügt. Der **dwbuttonstate** -Member des **Maus \_ Ereignis \_ Datensatzes** weist ein Bit auf, das den Zustand der einzelnen Maustasten angibt. Das Bit ist 1, wenn die Schaltfläche nicht gedrückt ist, und 0, wenn die Schaltfläche aktiv ist. Um die Anzahl der wichtigen Bits zu ermitteln, verwenden Sie **getnumofansolemousebuttons**.

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

[Konsolen Eingabepuffer](console-input-buffer.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)

[**\_Ereignis \_ Daten Satz für Maus**](mouse-event-record-str.md)

 

 




