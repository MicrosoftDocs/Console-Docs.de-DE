---
title: Getconsolecp-Funktion
description: Ruft die Eingabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: ba0ebfecddf5702e8078197b834931a62658d9dc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059803"
---
# <a name="getconsolecp-function"></a>Getconsolecp-Funktion


Ruft die Eingabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen.

<a name="syntax"></a>Syntax
------

```C
UINT WINAPI GetConsoleCP(void);
```

<a name="parameters"></a>Parameter
----------

Diese Funktion besitzt keine Parameter.

<a name="return-value"></a>Rückgabewert
------------

Der Rückgabewert ist ein Code, der die Codepage bezeichnet. Eine Liste der Bezeichner finden Sie unter [Code Page Identifier](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Wenn der Rückgabewert 0 (null) ist, ist die Funktion fehlgeschlagen. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Eine Codepage ordnet 256 Zeichen Codes einzelnen Zeichen zu. Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind. Weitere Informationen zu einer Codepage, einschließlich des Namens, finden Sie in der [**getcpinfoex**](https://msdn.microsoft.com/library/windows/desktop/dd318081) -Funktion.

Um die Eingabe Codepage einer Konsole festzulegen, verwenden Sie die [**setconsolecp**](setconsolecp.md) -Funktion. Um die Ausgabe Codepage einer Konsole festzulegen und abzufragen, verwenden Sie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) .

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
<td>Consoleapi. h (über WinCon. h, Include Windows. h)</td>
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

[**Getconsoleoutputcp**](getconsoleoutputcp.md)

[**Setconsolecp**](setconsolecp.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

 

 




