---
title: Getnumofconsoleinputevents-Funktion
description: Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c5e3a59308239898f78796170d08f8b21ca1b667
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059698"
---
# <a name="getnumberofconsoleinputevents-function"></a>Getnumofconsoleinputevents-Funktion


Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

<a name="parameters"></a>Parameter
----------

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpcnumofevents* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole empfängt.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Die **getnumofconsoleinputevents** -Funktion meldet die Gesamtzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer, einschließlich der Tastatur-, Maus-und Fenstergröße für Eingabedaten Sätze. Prozesse, die die Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " verwenden, können nur Tastatureingaben lesen. Prozesse, die die Funktion " [**leseconsoleinput**](readconsoleinput.md) " verwenden, können alle Typen von Eingabedaten Sätzen lesen.

Ein Prozess kann ein Konsolen Eingabepuffer Handle in einer der Wait- [Funktionen](https://msdn.microsoft.com/library/windows/desktop/ms687069) angeben, um zu bestimmen, wann eine ungelesene Konsolen Eingabe vorhanden ist. Wenn der Eingabepuffer nicht leer ist, wird der Status eines Konsolen Eingabepuffer-Handles signalisiert.

Um Eingabedaten Sätze aus einem Konsolen Eingabepuffer zu lesen, ohne die Anzahl der ungelesenen Datensätze zu beeinträchtigen, verwenden Sie die Funktion " [**Peer**](peekconsoleinput.md) . Verwenden Sie die [**flushconsoleinputbuffer**](flushconsoleinputbuffer.md) -Funktion, um alle ungelesenen Datensätze im Eingabepuffer einer Konsole zu verwerfen.

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


[Konsolenfunktionen](console-functions.md)

[**Flushconsolinput Buffer**](flushconsoleinputbuffer.md)

[Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)

[**"Etekconsoleinput"**](peekconsoleinput.md)

[**"Read Console"**](readconsole.md)

[**Read ConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

 

 




