---
title: SetConsoleCtrlHandler-Funktion
description: Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt Sie.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 1c5c67bc5900a36bb50c0da90516fab0cec2e366
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039418"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler-Funktion

Fügt eine Anwendungs definierte Handlerroutine-Funktion aus der Liste der [**Handlerfunktionen**](handlerroutine.md) für den aufrufenden Prozess hinzu oder entfernt Sie.

Wenn keine Handlerfunktion angegeben wird, legt die Funktion ein Vererb bares Attribut fest, das bestimmt, ob der aufrufende Prozess <kbd>STRG</kbd>- + <kbd>C</kbd> -Signale ignoriert.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>Parameter

*Handlerroutine* \[ in, optional\]  
Ein Zeiger auf die Anwendungs definierte [**Handlerroutine**](handlerroutine.md) -Funktion, die hinzugefügt oder entfernt werden soll. Dieser Parameter kann **null** sein.

*Hinzufügen* \[ in\]  
Wenn dieser Parameter **true** ist, wird der Handler hinzugefügt. Wenn der Wert **false** ist, wird der Handler entfernt.

Wenn der *Handlerroutine* -Parameter **null** ist, bewirkt ein **true** -Wert, dass der aufrufenden Prozess <kbd>STRG</kbd> + <kbd>c</kbd> -Eingaben ignoriert, und ein **false** -Wert stellt die normale Verarbeitung von <kbd>STRG</kbd> + <kbd>c</kbd> -Eingaben wieder her. Dieses Attribut zum ignorieren oder Verarbeiten von <kbd>STRG</kbd> + <kbd>C</kbd> wird von untergeordneten Prozessen geerbt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Diese Funktion bietet eine ähnliche Benachrichtigung für Konsolen Anwendungen und-Dienste, die [**WM \_ queryendsession**](https://msdn.microsoft.com/library/windows/desktop/aa376890) für grafische Anwendungen mit einem nachrichtenpump bereitstellt. Sie können diese Funktion auch aus einer grafischen Anwendung verwenden, aber es gibt keine Garantie, dass Sie vor der Benachrichtigung von **WM \_ queryendsession** eintreffen würde.

Jeder Konsolen Prozess verfügt über eine eigene Liste von Anwendungs definierten [**Handlerroutine**](handlerroutine.md) -Funktionen, die die Tastenkombination <kbd>STRG</kbd> + <kbd>C</kbd> und <kbd>STRG</kbd>drücken + <kbd>BREAK</kbd> . Die Handlerfunktionen behandeln auch Signale, die vom System generiert werden, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt. Anfänglich enthält die Handlerliste für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion aufruft. Bei einem Konsolen Prozess werden zusätzliche Handlerfunktionen durch Aufrufen der **SetConsoleCtrlHandler** -Funktion hinzugefügt oder entfernt, die sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt. Wenn ein Konsolen Prozess eines der Steuersignale empfängt, werden seine Handlerfunktionen für eine zuletzt registrierte, erste Methode aufgerufen, bis einer der Handler zurückgibt `TRUE` . Wenn keiner der Handler zurückgibt `TRUE` , wird der Standard Handler aufgerufen.

Bei Konsolen Prozessen werden die <kbd>CTRL</kbd> + Tastenkombinationen STRG <kbd>c</kbd> und <kbd>STRG</kbd>- + <kbd>BREAK</kbd> Taste normalerweise als Signale behandelt ( **Strg c- \_ \_ Ereignis** und **STRG-Break- \_ \_ Ereignis** ). Wenn ein Konsolenfenster mit dem Tastaturfokus <kbd>STRG</kbd> + <kbd>C</kbd> oder <kbd>STRG</kbd>-Taste erhält + <kbd>BREAK</kbd>, wird das Signal in der Regel an alle Prozesse weitergegeben, die die Konsole freigeben.

<kbd>STRG</kbd> + " <kbd>Break</kbd> " wird immer als Signal behandelt, aber das typische <kbd>STRG</kbd>- + <kbd>C</kbd> -Verhalten kann auf drei Arten geändert werden, die verhindern, dass die Handlerfunktionen aufgerufen werden:

- Die [**setconsolemode**](setconsolemode.md) -Funktion kann den aktivierte **\_ \_ Eingabe** Modus für den Eingabepuffer einer Konsole deaktivieren, sodass <kbd>STRG</kbd> + <kbd>C</kbd> als Tastatureingabe und nicht als Signal gemeldet wird.
- Der Aufruf von **SetConsoleCtrlHandler** mit den Argumenten **null** und **true** bewirkt, dass der aufrufende Prozess <kbd>STRG</kbd> + <kbd>C</kbd> -Signale ignoriert. Dieses Attribut wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.
- Wenn ein Konsolen Prozess gedebuggt wird und <kbd>STRG</kbd> + <kbd>C</kbd> -Signale nicht deaktiviert wurden, generiert das System eine **dbg-Steuerungs- \_ \_ c** -Ausnahme. Diese Ausnahme wird nur für den Vorteil des Debuggers ausgelöst, und eine Anwendung sollte niemals einen Ausnahmehandler verwenden, um Sie zu behandeln. Wenn der Debugger die Ausnahme behandelt, wird die <kbd>STRG</kbd>-Taste für eine Anwendung nicht bemerkt + <kbd>C</kbd>, mit einer Ausnahme: mindestwarnzeit-warte Vorgänge werden beendet. Wenn der Debugger die Ausnahme bei nicht behandelter übergibt, wird <kbd>STRG</kbd> + <kbd>C</kbd> an den Konsolen Prozess weitergeleitet und als Signal behandelt, wie bereits erläutert.

Ein Konsolen Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um ein <kbd>STRG</kbd> + <kbd>C</kbd> -oder <kbd>STRG</kbd>-halte + <kbd>BREAK</kbd> Signal an eine Konsolen Prozessgruppe zu senden.

Das System generiert das STRG-Schließ **\_ \_ Ereignis** , das STRG-Abmelde **\_ \_ Ereignis** und das **STRG-Shutdown- \_ \_ Ereignis** Signal, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt, sodass der Prozess vor dem beenden eine Bereinigung durchführt. Konsolenfunktionen oder alle C-Lauf Zeitfunktionen, die Konsolenfunktionen aufzurufen, funktionieren möglicherweise nicht zuverlässig während der Verarbeitung der drei Signale, die zuvor erwähnt wurden. Der Grund hierfür ist, dass möglicherweise einige oder alle der internen Konsolen Bereinigungs Routinen aufgerufen wurden, bevor der Prozess Signalhandler ausgeführt wurde.

**Windows 7, Windows 8, Windows 8.1 und Windows 10:**

Wenn eine Konsolenanwendung die gdi32.dll oder user32.dll Bibliothek lädt, wird die [**Handlerroutine**](handlerroutine.md) -Funktion, die Sie beim Aufrufen von **SetConsoleCtrlHandler** angeben, nicht für das STRG-Abmelde **\_ \_ Ereignis** und **STRG-Shutdown- \_ \_ Ereignis** Ereignisse aufgerufen. Das Betriebssystem erkennt Prozesse, die gdi32.dll oder user32.dll als Windows-Anwendungen und nicht als Konsolen Anwendungen laden. Dieses Verhalten tritt auch bei Konsolen Anwendungen auf, die keine Funktionen in gdi32.dll oder user32.dll direkt aufzurufen, aber Funktionen wie [Shellfunktionen](https://msdn.microsoft.com/library/windows/desktop/bb776426) aufzurufen, die wiederum Funktionen in gdi32.dll oder user32.dll aufzurufen.

Um Ereignisse zu empfangen, wenn ein Benutzer sich abmeldet oder das Gerät unter diesen Umständen heruntergefahren wird, erstellen Sie ein ausgeblendetes Fenster in der Konsolenanwendung, und behandeln Sie dann die Nachrichten des WM-Fensters [**\_ queryendsession**](https://msdn.microsoft.com/library/windows/desktop/aa376890) und [**WM \_ EndSession**](https://msdn.microsoft.com/library/windows/desktop/aa376889) , die das verborgene Fenster empfängt. Sie können ein verborgenes Fenster erstellen, indem Sie die [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) -Methode aufrufen, wobei der *dwExStyle* -Parameter auf 0 festgelegt ist.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Registrieren einer Steuerelement Handler-Funktion](registering-a-control-handler-function.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Consoleapi. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | |

## <a name="see-also"></a>Weitere Informationen

[Konsolen-Bearbeitungssteuerelemente](console-control-handlers.md)

[Konsolenfunktionen](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)
