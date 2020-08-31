---
title: Getconsoleskreenbufferinfo-Funktion
description: Siehe Referenzinformationen zur getconsoleskreenbufferinfo-Funktion, die Informationen zum angegebenen Konsolenbildschirm Puffer abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059715"
---
# <a name="getconsolescreenbufferinfo-function"></a>Getconsoleskreenbufferinfo-Funktion


Ruft Informationen zum angegebenen Konsolenbildschirm Puffer ab.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpconsoleskreenbufferinfo* \[ vorgenommen\]  
Ein Zeiger auf eine [**Konsolen \_ Bildschirm- \_ Puffer \_ Info**](console-screen-buffer-info-str.md) Struktur, die die Bildschirm Puffer Informationen der Konsole empfängt.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Das Rechteck, das im **srwindow** -Member der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben wird, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf des Konsolenbildschirm Puffers im-Fenster durchführen, um die Größe des Fensters zu ändern oder beides.

Alle Koordinaten, die in der [**Konsolen \_ Bildschirm \_ Puffer \_ Info**](console-screen-buffer-info-str.md) -Struktur zurückgegeben werden, sind in Zeichen Zell Koordinaten, wobei sich der Ursprung (0,0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Scrollen des Fensters eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md).

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

[**Konsolen \_ Bildschirm- \_ Puffer \_ Informationen**](console-screen-buffer-info-str.md)

[**Getlargestconsolewindowsize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**Setconsoleskreenbuffersize**](setconsolescreenbuffersize.md)

[**Setconsolewindowinfo**](setconsolewindowinfo.md)

[Fenster-und Bildschirm Puffergröße](window-and-screen-buffer-size.md)

 

 




