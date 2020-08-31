---
title: Closepseudoconsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur closepseudoconsole-Funktion, die eine Pseudo Console aus dem angegebenen Handle schließt.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060179"
---
# <a name="closepseudoconsole-function"></a>Closepseudoconsole-Funktion


Schließt eine pseudoconsole aus dem angegebenen Handle.

<a name="syntax"></a>Syntax
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a>Parameter
----------

*HPC* \[ in\]  
Ein Handle für eine aktive psuedoconsole, wie von " [deepseudoconsole](createpseudoconsole.md)" geöffnet.

<a name="return-value"></a>Rückgabewert
------------

*keine*

<a name="remarks"></a>Hinweise
-------

Wenn Sie eine Pseudo Konsole schließen, werden auch Client Anwendungen beendet, die an die Sitzung angefügt sind.

`hOutput`Wenn diese API aufgerufen wird, kann von der pseudoconsole ein abschließender gezeichnet werden. Es wird erwartet, dass der Aufrufer diese Informationen aus dem Kommunikationskanal Puffer abfließt und ihn entweder vornimmt oder verwerfen kann. Wenn der Puffer nicht entladen wird, kann es passieren, dass der Close-Befehl unbegrenzt wartet, bis er entladen wird oder die Kommunikationskanäle anders voneinander getrennt sind.

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

[**Resizepseudoconsole**](resizepseudoconsole.md)
