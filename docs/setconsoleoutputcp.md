---
title: Setconsoleoutputcp-Funktion
description: Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae1f3970af6c8db1ebedc29e0644ed001258ecc5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060502"
---
# <a name="setconsoleoutputcp-function"></a>Setconsoleoutputcp-Funktion


Legt die Ausgabe Codepage fest, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. Eine-Konsole verwendet Ihre Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die im Konsolenfenster angezeigten Bilder zu übersetzen.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI SetConsoleOutputCP(
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

Wenn die aktuelle Schriftart eine Unicode-Schriftart mit fester Größe ist, ändert **setconsoleoutputcp** die Zuordnung der Zeichen Werte in den Glyphe-Satz der Schriftart, anstatt jedes Mal, wenn Sie aufgerufen wird, eine separate Schriftart zu laden. Dies wirkt sich darauf aus, wie erweiterte Zeichen (ASCII-Wert größer als 127) in einem Konsolenfenster angezeigt werden. Wenn es sich bei der aktuellen Schriftart jedoch um eine Raster Schriftart handelt, wirkt sich **setconsoleoutputcp** nicht darauf aus, wie erweiterte Zeichen angezeigt werden.

Verwenden Sie die Funktion " [enumsystemcodepages](https://go.microsoft.com/fwlink/p/?linkid=178051) ", um die Codepages zu suchen, die vom Betriebssystem installiert oder unterstützt werden. Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden auch in der Registrierung unter folgendem Schlüssel gespeichert:

**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ Control \\ nls \\ Codepage**

Es ist jedoch besser, mit [enumsystemcodepages Codepages](https://go.microsoft.com/fwlink/p/?linkid=178051) aufzuzählen, da sich die Registrierung in verschiedenen Versionen von Windows unterscheiden kann.
Verwenden Sie die [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) -Funktion, um zu bestimmen, ob eine bestimmte Codepage gültig ist. Verwenden Sie die [**getcpinfoex**](https://msdn.microsoft.com/library/windows/desktop/dd318081) -Funktion, um weitere Informationen über eine Codepage einschließlich Ihres Namens abzurufen. Eine Liste der verfügbaren Code Page Bezeichner finden Sie unter [Code Page Identifier](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Verwenden Sie die [**getconsoleoutputcp**](getconsoleoutputcp.md) -Funktion, um die aktuelle Ausgabe Codepage einer Konsole zu ermitteln. Um die Eingabe Codepage einer Konsole festzulegen und abzurufen, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) .

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

[**Setconsolecp**](setconsolecp.md)

 

 




