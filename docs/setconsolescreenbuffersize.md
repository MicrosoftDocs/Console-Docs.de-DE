---
title: Setconsoleskreenbuffersize-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "setconsoleskreenbuffersize", die die Größe des angegebenen Konsolenbildschirm Puffers ändert.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0e2f3a3ea11f291e88837885c6fc3e555fd39e09
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060509"
---
# <a name="setconsolescreenbuffersize-function"></a>Setconsoleskreenbuffersize-Funktion


Ändert die Größe des angegebenen Konsolenbildschirm Puffers.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*dwSize* \[ in\]  
Eine [**Koord**](coord-str.md) -Struktur, die die neue Größe des Konsolenbildschirm Puffers in Zeichen Zeilen und-Spalten angibt. Die angegebene Breite und Höhe darf nicht kleiner sein als die Breite und Höhe des Fensters des Konsolenbildschirm Puffers. Die angegebenen Dimensionen dürfen auch nicht kleiner als die vom System zulässige Mindestgröße sein. Dieses Minimum hängt von der aktuellen Schriftgröße für die Konsole (vom Benutzer ausgewählt) und den von der [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) -Funktion zurückgegebenen **SM- \_ cxMin** -und **SM- \_ Cymin** -Werten ab.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

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

[Konsolen Eingabepuffer](console-input-buffer.md)

[**Koord**](coord-str.md)

[**Getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md)

[**Setconsolewindowinfo**](setconsolewindowinfo.md)

 

 




