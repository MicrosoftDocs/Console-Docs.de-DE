---
title: Leserconsoleoutputattribute-Funktion
description: Kopiert eine angegebene Anzahl von Zeichen Attributen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4cf3ac9b85c3eab73c3530c1fd9991a7fbbf5a5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060394"
---
# <a name="readconsoleoutputattribute-function"></a>Leserconsoleoutputattribute-Funktion


Kopiert eine angegebene Anzahl von Zeichen Attributen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpattribute* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der die Attribute empfängt, die vom Konsolenbildschirm Puffer verwendet werden.

Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).

*nlength* \[ in\]  
Die Anzahl der zu lesenden Zeichen Zellen des Bildschirm Puffers. Die Größe des Puffers, auf den der *lpattribute* -Parameter verweist, sollte lauten `nLength * sizeof(WORD)` .

*dwumkoord* \[ in\]  
Die Koordinaten der ersten Zelle im Konsolenbildschirm Puffer, von der in Zeichen gelesen werden soll. Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.

*lpnumofattrsread* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Attribute empfängt.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Wenn sich die Anzahl der zu lesenden Attribute über das Ende der angegebenen Bildschirm Puffer Zeile hinaus erstreckt, werden Attribute aus der nächsten Zeile gelesen. Wenn die Anzahl der zu lesenden Attribute über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Attribute bis zum Ende des Konsolenbildschirm Puffers gelesen.

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

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**"Read consoleoutput"**](readconsoleoutput.md)

[**"Read consoleoutputcharacter"**](readconsoleoutputcharacter.md)

[**Schreibconsoleoutput**](writeconsoleoutput.md)

[**"Schreibconsoleoutputattribute"**](writeconsoleoutputattribute.md)

[**Schreibconsoleoutputcharacter**](writeconsoleoutputcharacter.md)

 

 




