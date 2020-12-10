---
title: SetConsoleCtrlHandler-Funktion
description: Fügt eine von der Anwendung definierte HandlerRoutine-Funktion zur Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt sie aus dieser.
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
ms.localizationpriority: high
ms.openlocfilehash: 208eebc92b718fed9856a48dfaf5cbebdaddc1e1
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420269"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler-Funktion

Fügt eine von der Anwendung definierte [**HandlerRoutine**](handlerroutine.md)-Funktion zur Liste der Handlerfunktionen für den aufrufenden Prozess hinzu oder entfernt sie aus dieser.

Wenn keine Handlerfunktion angegeben wird, legt die Funktion ein vererbbares Attribut fest, das bestimmt, ob der aufrufende Prozess <kbd>STRG</kbd>+<kbd>C</kbd>-Signale ignoriert.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>Parameter

*HandlerRoutine* \[in, optional\]  
Ein Zeiger auf die von der Anwendung definierte [**HandlerRoutine**](handlerroutine.md)-Funktion, die hinzugefügt oder entfernt werden soll. Dieser Parameter kann **NULL** sein.

*Add* \[in\]  
Wenn dieser Parameter **TRUE** ist, wird der Handler hinzugefügt. Ist er **FALSE**, wird der Handler entfernt.

Wenn der *HandlerRoutine*-Parameter **NULL** ist, bewirkt der Wert **TRUE**, dass der aufrufende Prozess die Eingabe von <kbd>STRG</kbd>+<kbd>C</kbd> ignoriert, während beim Wert **FALSE** die normale Verarbeitung der Eingabe von <kbd>STRG</kbd>+<kbd>C</kbd> wiederhergestellt wird. Dieses Attribut zum Ignorieren oder Verarbeiten von <kbd>STRG</kbd>+<kbd>C</kbd> wird von untergeordneten Prozessen geerbt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) auf.

## <a name="remarks"></a>Bemerkungen

Diese Funktion bietet eine ähnliche Benachrichtigung für Konsolenanwendungen und-Dienste, wie sie [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) für grafische Anwendungen mit einem Nachrichtensystem bereitstellt. Sie könnten diese Funktion auch aus einer grafischen Anwendung heraus verwenden, es ist aber nicht sichergestellt, dass sie vor der Benachrichtigung von **WM\_QUERYENDSESSION** eingehen würde.

Für jeden Konsolenprozess gibt es eine eigene Liste mit anwendungsdefinierten [**HandlerRoutine**](handlerroutine.md)-Funktionen, die <kbd>STRG</kbd>+<kbd>C</kbd>- und <kbd>STRG</kbd>+<kbd>UNTBR</kbd>-Signale verarbeiten. Die Handlerfunktionen verarbeiten außerdem Signale, die vom System generiert werden, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt. Anfänglich enthält die Handlerliste für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)-Funktion aufruft. Ein Konsolenprozess fügt zusätzliche Handlerfunktionen hinzu oder entfernt diese, indem er die Funktion **SetConsoleCtrlHandler** aufruft, was sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt. Wenn ein Konsolenprozess eins der Steuersignale empfängt, werden seine Handlerfunktionen der Reihe nach beginnend mit der zuletzt registrierten aufgerufen, bis einer der Handler `TRUE` zurückgibt. Wenn keiner der Handler `TRUE` zurückgibt, wird der Standardhandler aufgerufen.

Für Konsolenprozesse werden die Tastenkombinationen <kbd>STRG</kbd>+<kbd>C</kbd> und <kbd>STRG</kbd>+<kbd>UNTBR</kbd> normalerweise als Signale (**STRG\_C\_EVENT** und **STRG\_BREAK\_EVENT**) behandelt. Wenn ein Konsolenfenster mit Tastaturfokus <kbd>STRG</kbd>+<kbd>C</kbd> oder <kbd>STRG</kbd>+<kbd>UNTBR</kbd> empfängt, wird das Signal normalerweise an alle Prozesse übergeben, die die betreffende Konsole gemeinsam verwenden.

<kbd>STRG</kbd>+<kbd>UNTBR</kbd> wird immer als Signal behandelt, aber das Verhalten von <kbd>STRG</kbd>+<kbd>C</kbd> kann normalerweise auf drei Arten geändert werden, die das Aufrufen der Handlerfunktionen verhindern:

- Die Funktion [**SetConsoleMode**](setconsolemode.md) kann den Modus **ENABLE\_PROCESSED\_INPUT** für den Eingabepuffer einer Konsole deaktivieren, sodass <kbd>STRG</kbd>+<kbd>C</kbd> als Tastatureingabe statt als Signal gemeldet wird.
- Das Aufrufen von **SetConsoleCtrlHandler** mit den Argumenten **NULL** und **TRUE** bewirkt, dass der aufrufende Prozess <kbd>STRG</kbd>+<kbd>C</kbd>-Signale ignoriert. Dieses Attribut wird von untergeordneten Prozessen geerbt, kann jedoch von jedem Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse davon betroffen sind.
- Wenn ein Konsolenprozess debuggt wird und <kbd>STRG</kbd>+<kbd>C</kbd>-Signale nicht deaktiviert wurden, generiert das System eine **DBG\_CONTROL\_C**-Ausnahme. Diese Ausnahme wird nur zum Nutzen des Debuggers ausgelöst, und eine Anwendung sollte niemals einen Ausnahmehandler verwenden, um sie zu verarbeiten. Wenn der Debugger die Ausnahme behandelt, wird das <kbd>STRG</kbd>+<kbd>C</kbd>-Signal von einer Anwendung nicht bemerkt, mit einer Ausnahme: Warnungsfähige Wartebedingungen werden beendet. Wenn der Debugger die Ausnahme unverarbeitet übergibt, wird <kbd>STRG</kbd>+<kbd>C</kbd> an den Konsolenprozess übergeben und als Signal behandelt, wie zuvor erörtert.

Ein Konsolenprozess kann die Funktion [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) verwenden, um ein <kbd>STRG</kbd>+<kbd>C</kbd>- oder <kbd>STRG</kbd>+<kbd>BREAK</kbd>-Signal an eine Konsolenprozessgruppe zu senden.

Das System generiert **CTRL\_CLOSE\_EVENT**-, **CTRL\_LOGOFF\_EVENT**- und **CTRL\_SHUTDOWN\_EVENT**-Signale, wenn der Benutzer die Konsole schließt, sich abmeldet oder das System herunterfährt, sodass der Prozess Gelegenheit hat, vor der Beendigung aufzuräumen. Konsolenfunktionen oder beliebige C-Laufzeitfunktionen, die Konsolenfunktionen aufrufen, funktionieren möglicherweise nicht zuverlässig, während eins dieser zuvor erwähnten Signale verarbeitet wird. Dies hat den Grund, dass möglicherweise einige oder alle ihrer internen Routinen zur Konsolenbereinigung aufgerufen wurden, bevor der Prozesssignalhandler ausgeführt wird.

**Windows 7, Windows 8, Windows 8.1 und Windows 10:**

Wenn eine Konsolenanwendung die gdi32.dll- oder user32.dll-Bibliothek lädt, wird die [**HandlerRoutine**](handlerroutine.md)-Funktion, die Sie beim Aufrufen von **SetConsoleCtrlHandler** angeben, für die Ereignisse **CTRL\_LOGOFF\_EVENT** und **CTRL\_SHUTDOWN\_EVENT** nicht aufgerufen. Das Betriebssystem erkennt Prozesse, die gdi32.dll oder user32.dll laden, als Windows-Anwendungen und nicht als Konsolenanwendungen. Dieses Verhalten tritt auch bei Konsolenanwendungen auf, die keine Funktionen in gdi32.dll oder user32.dll direkt aufrufen, sondern Funktionen wie etwa [Shellfunktionen](https://msdn.microsoft.com/library/windows/desktop/bb776426) aufrufen, die ihrerseits Funktionen in gdi32.dll oder user32.dll aufrufen.

Zum Empfangen von Ereignissen, wenn sich ein Benutzer abmeldet oder das Gerät unter diesen Umständen heruntergefahren wird, erstellen Sie ein verborgenes Fenster in Ihrer Konsolenanwendung, und verarbeiten Sie dann die Fensternachrichten [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) und [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889), die vom verborgenen Fenster empfangen werden. Sie können ein ausgeblendetes Fenster erstellen, indem Sie die Methode [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) mit auf 0 festgelegtem Parameter *dwExStyle* aufrufen.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Registrieren einer Steuerelementhandler-Funktion](registering-a-control-handler-function.md).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ConsoleApi.h (über WinCon.h, Windows.h einschließen) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | |

## <a name="see-also"></a>Siehe auch

[Konsolen-Bearbeitungssteuerelemente](console-control-handlers.md)

[Konsolenfunktionen](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)
