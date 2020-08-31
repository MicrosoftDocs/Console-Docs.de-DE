---
title: Funktion "schreiteconsoleoutputattribute"
description: Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e7c684b2f450713eaa78730676a0148e9b090c79
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060478"
---
# <a name="writeconsoleoutputattribute-function"></a>Funktion "schreiteconsoleoutputattribute"


Kopiert eine Reihe von Zeichen Attributen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpattribute* \[ in\]  
Die Attribute, die beim Schreiben in den Konsolenbildschirm Puffer verwendet werden sollen. Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#_win32_font_attributes).

*nlength* \[ in\]  
Die Anzahl der Zellen des Bildschirm Puffers, in die die Attribute kopiert werden.

*dwschreitecoord* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle im Konsolenbildschirm Puffer angibt, in die die Attribute geschrieben werden.

*lpnumofattrswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der Attribute empfängt, die tatsächlich in den Konsolenbildschirm Puffer geschrieben wurden.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Attribute in die nächste Zeile geschrieben. Wenn die Anzahl der Attribute, in die geschrieben werden soll, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Attribute bis zum Ende des Bildschirm Puffers der Konsole geschrieben.

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

[Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

[**"Read consoleoutput"**](readconsoleoutput.md)

[**"Read consoleoutputattribute"**](readconsoleoutputattribute.md)

[**"Read consoleoutputcharacter"**](readconsoleoutputcharacter.md)

[**Schreibconsoleoutput**](writeconsoleoutput.md)

[**Schreibconsoleoutputcharacter**](writeconsoleoutputcharacter.md)

 

 




