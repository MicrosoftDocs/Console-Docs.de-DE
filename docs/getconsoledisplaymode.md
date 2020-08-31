---
title: Getconsoledisplaymode-Funktion
description: Siehe Referenzinformationen zur getconsoledisplaymode-Funktion, die den Anzeigemodus der aktuellen Konsole abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059811"
---
# <a name="getconsoledisplaymode-function"></a>Getconsoledisplaymode-Funktion


Ruft den Anzeigemodus der aktuellen Konsole ab.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a>Parameter
----------

*lpmodeflags* \[ vorgenommen\]  
Der Anzeigemodus der Konsole. Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.

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
<td><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</td>
<td><p>Voll Bild Konsole. Die Konsole befindet sich in diesem Modus, sobald das Fenster maximiert ist. An diesem Punkt kann der Übergang zum Vollbildmodus weiterhin fehlschlagen.</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</td>
<td><p>Voll Bild Konsole, die direkt mit der Video Hardware kommuniziert. Dieser Modus wird festgelegt, nachdem sich die Konsole im <strong>CONSOLE_FULLSCREEN</strong> Modus befindet, um anzugeben, dass der Übergang zum Vollbildmodus abgeschlossen wurde.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie ** \_ Win32 \_ Winnt** als 0x0500 sein oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows XP [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2003 [nur Desktop-Apps]</p></td>
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

[Konsolen Modi](console-modes.md)

[**Setconsoledisplaymode**](setconsoledisplaymode.md)

 

 




