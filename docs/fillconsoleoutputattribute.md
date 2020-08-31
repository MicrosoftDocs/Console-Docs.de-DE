---
title: Fillconsoleoutputattribute-Funktion
description: Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059882"
---
# <a name="fillconsoleoutputattribute-function"></a>Fillconsoleoutputattribute-Funktion


Legt die Zeichen Attribute für eine angegebene Anzahl von Zeichen Zellen fest, beginnend bei den angegebenen Koordinaten in einem Bildschirm Puffer.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*wattribute* \[ in\]  
Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen. Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).

*nlength* \[ in\]  
Die Anzahl der Zeichen Zellen, die auf die angegebenen Farb Attribute festgelegt werden sollen.

*dwschreitecoord* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle angibt, deren Attribute festgelegt werden sollen.

*lpnumofattrswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der Zeichen Zellen empfängt, deren Attribute tatsächlich festgelegt wurden.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Wenn die Anzahl der Zeichen Zellen, deren Attribute festgelegt werden sollen, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden die Zellen der nächsten Zeile festgelegt. Wenn die Anzahl der Zellen, die in geschrieben werden sollen, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Zellen bis zum Ende des Konsolenbildschirm Puffers geschrieben.

Die Zeichen Werte an den Positionen, die in geschrieben werden, werden nicht geändert.

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

[**Fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md)

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**"Schreibconsoleoutputattribute"**](writeconsoleoutputattribute.md)

 

 




