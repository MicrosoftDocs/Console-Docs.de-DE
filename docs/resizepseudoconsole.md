---
title: Resizepseudoconsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur resizepseudoconsole-Funktion, die die Größe der internen Puffer für eine Pseudo Konsole auf die angegebene Größe anpasst.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060347"
---
# <a name="resizepseudoconsole-function"></a>Resizepseudoconsole-Funktion


Ändert die Größe der internen Puffer für eine pseudoconsole auf die angegebene Größe.

<a name="syntax"></a>Syntax
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a>Parameter
----------

*HPC* \[ in\]  
Ein Handle für eine aktive psuedoconsole, wie von " [deepseudoconsole](createpseudoconsole.md)" geöffnet.

*Größe* \[ in\]  
Die Abmessungen des Fensters/Puffers in der Anzahl von Zeichen, die für den internen Puffer dieser pseudoconsole verwendet werden. 

<a name="return-value"></a>Rückgabewert
------------

Typ: **HRESULT**

Wenn diese Methode erfolgreich ausgeführt wird, wird **S_OK**zurückgegeben. Andernfalls wird ein **HRESULT** -Fehlercode zurückgegeben.

<a name="remarks"></a>Hinweise
-------

Diese Funktion kann die Größe der internen Puffer in der pseudoconsole-Sitzung ändern, sodass Sie der Fenster-/Puffergröße entspricht, die für die Anzeige am Terminal Ende verwendet wird. Dadurch wird sichergestellt, dass bei der Kommunikation mit den [Konsolenfunktionen](console-functions.md) angefügte Befehlszeilenschnittstelle (CUI) Anwendungen die richtigen Dimensionen in ihren Aufrufen zurückgegeben werden.

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
<td><p>Windows 10 1809 [nur Desktop-Apps]</p></td>
</tr>
<tr class="even">
<td><p>Unterstützte Mindestversion (Server)</p></td>
<td><p>Windows Server 2019 [nur Desktop-Apps]</p></td>
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

[Pseudo Konsolen](pseudoconsoles.md)

[**"Kreatepseudoconsole"**](createpseudoconsole.md)

[**Closepseudoconsole**](closepseudoconsole.md)
