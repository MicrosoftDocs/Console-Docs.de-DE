---
title: SetConsoleCtrlHandler-Funktion
description: Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt Sie.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: cd7b491c1a395483d4aef052d4147d3edf2514e5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060291"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler-Funktion


Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der [**Handlerfunktionen**](handlerroutine.md) für den aufrufenden Prozess hinzu oder entfernt Sie.

Wenn keine Handlerfunktion angegeben wird, legt die Funktion ein Vererb bares Attribut fest, das bestimmt, ob der aufrufende Prozess STRG + C-Signale ignoriert.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

<a name="parameters"></a>Parameter
----------

*Handlerroutine* \[ in, optional\]  
Ein Zeiger auf die Anwendungs definierte [**Handlerroutine**](handlerroutine.md) -Funktion, die hinzugefügt oder entfernt werden soll. Dieser Parameter kann **null**sein.

*Hinzufügen* \[ in\]  
Wenn dieser Parameter **true**ist, wird der Handler hinzugefügt. Wenn der Wert **false**ist, wird der Handler entfernt.

Wenn der *Handlerroutine* -Parameter **null**ist, bewirkt ein **true** -Wert, dass der Aufrufprozess die Strg + c-Eingabe ignoriert, und ein **false** -Wert stellt die normale Verarbeitung der Strg + c-Eingabe wieder her. Dieses Attribut zum ignorieren oder Verarbeiten von STRG + C wird von untergeordneten Prozessen geerbt.

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Hinweise
-------

Diese Funktion bietet eine ähnliche Benachrichtigung für Konsolen Anwendungen und-Dienste, die [**WM \_ queryendsession**](https://msdn.microsoft.com/library/windows/desktop/aa376890) für grafische Anwendungen mit einem nachrichtenpump bereitstellt. Sie können diese Funktion auch aus einer grafischen Anwendung verwenden, aber es gibt keine Garantie, dass Sie vor der Benachrichtigung von **WM \_ queryendsession**eintreffen würde.

Jeder Konsolen Prozess verfügt über eine eigene Liste von Anwendungs definierten [**Handlerroutine**](handlerroutine.md) -Funktionen, die die Signale STRG + C und STRG + UN-Taste verarbeiten. Die Handlerfunktionen behandeln auch Signale, die vom System generiert werden, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt. Anfänglich enthält die Handlerliste für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion aufruft. Bei einem Konsolen Prozess werden zusätzliche Handlerfunktionen durch Aufrufen der **SetConsoleCtrlHandler** -Funktion hinzugefügt oder entfernt, die sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt. Wenn ein Konsolen Prozess eines der Steuersignale empfängt, werden seine Handlerfunktionen für eine zuletzt registrierte, erste aufrufende Basis aufgerufen, bis einer der Handler "true" zurückgibt. Wenn keiner der Handler true zurückgibt, wird der Standard Handler aufgerufen.

Bei Konsolen Prozessen werden die Tastenkombinationen STRG + C und STRG + Unterbrechung normalerweise als Signale behandelt (**STRG \_ C- \_ Ereignis** und **STRG-Break- \_ \_ Ereignis**). Wenn ein Konsolenfenster mit dem Tastaturfokus STRG + C oder STRG + UNTBR erhält, wird das Signal in der Regel an alle Prozesse weitergegeben, die die Konsole freigeben.

STRG + UNTBR wird immer als Signal behandelt, aber das typische STRG + C-Verhalten kann auf drei Arten geändert werden, die verhindern, dass die Handlerfunktionen aufgerufen werden:

- Die [**setconsolemode**](setconsolemode.md) -Funktion kann den aktivierte ** \_ \_ Eingabe** Modus für den Eingabepuffer einer Konsole deaktivieren, sodass STRG + C als Tastatureingabe und nicht als Signal gemeldet wird.
- Der Aufruf von **SetConsoleCtrlHandler** mit den Argumenten **null** und **true** bewirkt, dass der aufrufende Prozess STRG + C-Signale ignoriert. Dieses Attribut wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.
- Wenn ein Konsolen Prozess gedebuggt wird und STRG + C-Signale nicht deaktiviert wurden, generiert das System eine **dbg- \_ Steuerungs- \_ C** -Ausnahme. Diese Ausnahme wird nur für den Vorteil des Debuggers ausgelöst, und eine Anwendung sollte niemals einen Ausnahmehandler verwenden, um Sie zu behandeln. Wenn der Debugger die Ausnahme behandelt, wird die Tastenkombination STRG + C von der Anwendung nicht bemerkt, mit einer Ausnahme: mindestwarnzeit-warte Vorgänge werden beendet. Wenn der Debugger die Ausnahme bei nicht behandelten übergibt, wird STRG + C an den Konsolen Prozess weitergeleitet und als Signal behandelt, wie bereits erläutert.

Ein Konsolen Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um das Signal STRG + C oder STRG + UNTBR an eine Konsolen Prozessgruppe zu senden.

Das System generiert das STRG-Schließ ** \_ \_ Ereignis**, das STRG-Abmelde ** \_ \_ Ereignis**und das **STRG-Shutdown- \_ \_ Ereignis** Signal, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt, sodass der Prozess vor dem beenden eine Bereinigung durchführt. Konsolenfunktionen oder alle C-Lauf Zeitfunktionen, die Konsolenfunktionen aufzurufen, funktionieren möglicherweise nicht zuverlässig während der Verarbeitung der drei Signale, die zuvor erwähnt wurden. Der Grund hierfür ist, dass möglicherweise einige oder alle der internen Konsolen Bereinigungs Routinen aufgerufen wurden, bevor der Prozess Signalhandler ausgeführt wurde.

**Windows 7, Windows 8, Windows 8.1 und Windows 10:**

Wenn eine Konsolenanwendung die gdi32.dll oder user32.dll Bibliothek lädt, wird die [**Handlerroutine**](handlerroutine.md) -Funktion, die Sie beim Aufrufen von **SetConsoleCtrlHandler** angeben, nicht für das STRG-Abmelde ** \_ \_ Ereignis** und **STRG-Shutdown- \_ \_ Ereignis** Ereignisse aufgerufen. Das Betriebssystem erkennt Prozesse, die gdi32.dll oder user32.dll als Windows-Anwendungen und nicht als Konsolen Anwendungen laden. Dieses Verhalten tritt auch bei Konsolen Anwendungen auf, die keine Funktionen in gdi32.dll oder user32.dll direkt aufzurufen, aber Funktionen wie [Shellfunktionen](https://msdn.microsoft.com/library/windows/desktop/bb776426) aufzurufen, die wiederum Funktionen in gdi32.dll oder user32.dll aufzurufen.

Um Ereignisse zu empfangen, wenn ein Benutzer sich abmeldet oder das Gerät unter diesen Umständen heruntergefahren wird, erstellen Sie ein ausgeblendetes Fenster in der Konsolenanwendung, und behandeln Sie dann die Nachrichten des WM-Fensters [** \_ queryendsession**](https://msdn.microsoft.com/library/windows/desktop/aa376890) und [**WM \_ EndSession**](https://msdn.microsoft.com/library/windows/desktop/aa376889) , die das verborgene Fenster empfängt. Sie können ein verborgenes Fenster erstellen, indem Sie die [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) -Methode aufrufen, wobei der *dwExStyle* -Parameter auf 0 festgelegt ist.

<a name="examples"></a>Beispiele
--------

Ein Beispiel finden Sie unter [Registrieren einer Steuerelement Handler-Funktion](registering-a-control-handler-function.md).

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


[Konsolen Steuerungs Handler](console-control-handlers.md)

[Konsolenfunktionen](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**Generateconsolectrlevent**](generateconsolectrlevent.md)

[**Getconsolemode**](getconsolemode.md)

[**Handlerroutine**](handlerroutine.md)

[**Setconsolemode**](setconsolemode.md)

 

 




