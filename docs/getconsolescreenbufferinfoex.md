---
title: Getconsoleskreenbufferinfoex-Funktion
description: Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 69cb3c59af1a93cf6af664bbecaf05ef00b64ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059747"
---
# <a name="getconsolescreenbufferinfoex-function"></a>Getconsoleskreenbufferinfoex-Funktion


Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpconsoleskreenbufferinfoex* \[ vorgenommen\]  
Eine [** \_ \_ \_ INFOEX-Struktur des Konsolenbildschirm Puffers**](console-screen-buffer-infoex.md) , die die angeforderten Konsolenbildschirm Puffer Informationen empfängt.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Das Rechteck, das im **srwindow** -Member der [** \_ \_ \_ INFOEX-Struktur der Konsolenbildschirm Puffer**](console-screen-buffer-infoex.md) zurückgegeben wurde, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf im Fenster des Konsolenbildschirm Puffers durchführen, um die Größe des Fensters oder beides zu ändern.

Alle in der INFOEX-Struktur des [**Konsolen \_ Bildschirm \_ Puffers \_ **](console-screen-buffer-infoex.md) zurückgegebenen Koordinaten befinden sich in Zeichen Zellen Koordinaten, wobei sich der Ursprung (0, 0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.

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
<td><p>Windows Vista [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2008 [nur Desktop-Apps]</p></td>
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

[**Konsolen \_ Bildschirm- \_ Puffer \_ INFOEX**](console-screen-buffer-infoex.md)

[**Setconsoleskreenbufferinfoex**](setconsolescreenbufferinfoex.md)

 

 




