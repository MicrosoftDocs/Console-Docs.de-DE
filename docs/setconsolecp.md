---
title: Setconsolecp-Funktion
description: Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: cf7048f9042b6c516c6d8e7a6e0544fdc2ac7533
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060298"
---
# <a name="setconsolecp-function"></a>Setconsolecp-Funktion


Legt die Eingabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a>Parameter
----------

*wcodepageid* \[ in\]  
Der Bezeichner der festzulegenden Codepage. Weitere Informationen finden Sie in den Hinweisen.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu. Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.

Verwenden Sie die Funktion " [**enumsystemcodepages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) ", um die Codepages zu suchen, die vom Betriebssystem installiert oder unterstützt werden. Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden auch in der Registrierung unter folgendem Schlüssel gespeichert:

**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ Control \\ nls \\ Codepage**

Es ist jedoch besser, mit [**enumsystemcodepages Codepages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) aufzuzählen, da sich die Registrierung in verschiedenen Versionen von Windows unterscheiden kann.

Verwenden Sie die [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) -Funktion, um zu bestimmen, ob eine bestimmte Codepage gültig ist. Verwenden Sie die [**getcpinfoex**](https://msdn.microsoft.com/library/windows/desktop/dd318081) -Funktion, um weitere Informationen über eine Codepage einschließlich Ihres Namens abzurufen. Eine Liste der verfügbaren Code Page Bezeichner finden Sie unter [Code Page Identifier](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Verwenden Sie die [**getconsolecp**](getconsolecp.md) -Funktion, um die aktuelle Eingabe Codepage einer Konsole zu ermitteln. Zum Festlegen und Abrufen der Ausgabe Codepage einer Konsole verwenden Sie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) .

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


[Konsolen Codepages](console-code-pages.md)

[Konsolenfunktionen](console-functions.md)

[**Getconsolecp**](getconsolecp.md)

[**Getconsoleoutputcp**](getconsoleoutputcp.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

 

 




