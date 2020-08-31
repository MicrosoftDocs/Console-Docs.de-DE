---
title: Getconsoleoutputcp-Funktion
description: Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: e80618ebd5c6b29f00e79594c55bfa15fab315ba
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059755"
---
# <a name="getconsoleoutputcp-function"></a>Getconsoleoutputcp-Funktion


Ruft die Ausgabe Codepage ab, die von der Konsole verwendet wird, die dem aufrufenden Prozess zugeordnet ist. Eine-Konsole verwendet Ihre Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die im Konsolenfenster angezeigten Bilder zu übersetzen.

<a name="syntax"></a>Syntax
------

```C
UINT WINAPI GetConsoleOutputCP(void);
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

Verwenden Sie die [**setconsoleoutputcp**](setconsoleoutputcp.md) -Funktion, um die Ausgabe Codepage einer Konsole festzulegen. Verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) , um die Eingabe Codepage einer Konsole festzulegen und abzufragen.

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

[**Getconsolecp**](getconsolecp.md)

[**Setconsolecp**](setconsolecp.md)

[**Setconsoleoutputcp**](setconsoleoutputcp.md)

 

 




