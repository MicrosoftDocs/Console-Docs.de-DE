---
title: Handlerroutine-Rückruffunktion
description: Eine Anwendungs definierte Funktion, die mit der SetConsoleCtrlHandler-Funktion verwendet wird. Ein Konsolen Prozess verwendet diese Funktion zum Behandeln von Steuerungs Signalen, die vom Prozess empfangen werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/HandlerRoutine
- wincon/HandlerRoutine
- HandlerRoutine
MS-HAID:
- '\_win32\_handlerroutine'
- base.handlerroutine
- consoles.handlerroutine
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2e8732fa-7dfd-415b-b2fc-c27a400496f2
topic_type:
- apiref
api_name:
- HandlerRoutine
api_location:
- WinCon.h
api_type:
- UserDefined
ms.openlocfilehash: bd028892101b38ac7f0bfa307547ca4aa4cf5b0e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358740"
---
# <a name="handlerroutine-callback-function"></a>Handlerroutine-Rückruffunktion

Eine Anwendungs definierte Funktion, die mit der [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion verwendet wird. Ein Konsolen Prozess verwendet diese Funktion zum Behandeln von Steuerungs Signalen, die vom Prozess empfangen werden. Wenn das Signal empfangen wird, erstellt das System einen neuen Thread im Prozess zum Ausführen der Funktion.

Der Typ der **phandler- \_ Routine** definiert einen Zeiger auf diese Rückruffunktion. **Handlerroutine** ist ein Platzhalter für den Namen der Anwendungs definierten Funktion.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

## <a name="parameters"></a>Parameter

*dwctrltype* \[ in\]  
Der Typ des vom Handler empfangenen Steuersignal. Dieser Parameter kann einen der folgenden Werte annehmen.

| Wert | Bedeutung |
|-|-|
| **CTRL_C_EVENT** 0 | Ein <kbd>STRG</kbd> + <kbd>C</kbd> -Signal wurde entweder von der Tastatureingabe oder von einem von der **[generateconsolectrlevent](generateconsolectrlevent.md)** -Funktion generierten Signal empfangen. |
| **CTRL_BREAK_EVENT** 1 | Ein <kbd>STRG</kbd>- + <kbd>break</kbd> -Signal wurde empfangen, entweder von der Tastatureingabe oder von einem Signal, das von **[generateconsolectrlevent](generateconsolectrlevent.md)** generiert wurde. |
| **CTRL_CLOSE_EVENT** 2 | Ein Signal, das das System an alle an eine Konsole angefügten Prozesse sendet, wenn der Benutzer die Konsole schließt (entweder durch Klicken auf **Schließen** im Fenstermenü des Konsolenfensters oder durch Klicken auf den Schaltflächen Befehl **Task beenden** im Task-Manager). |
| **CTRL_LOGOFF_EVENT** 5 | Ein Signal, das das System an alle Konsolen Prozesse sendet, wenn sich der Benutzer abmeldet. Dieses Signal gibt nicht an, welcher Benutzer sich abmeldet, daher können keine Annahmen getroffen werden.<br /><br />Beachten Sie, dass dieses Signal nur von Diensten empfangen wird. Interaktive Anwendungen werden bei der Abmeldung beendet, sodass Sie nicht vorhanden sind, wenn das System dieses Signal sendet. |
| **CTRL_SHUTDOWN_EVENT** 6 | Ein Signal, das das System sendet, wenn das System heruntergefahren wird. Interaktive Anwendungen sind nicht in der Zeit vorhanden, in der das System dieses Signal sendet. Daher kann es in dieser Situation nur als Dienste empfangen werden. Dienste verfügen auch über einen eigenen Benachrichtigungs Mechanismus für das Herunterfahren von Ereignissen. Weitere Informationen finden Sie unter **[Handler](/windows/win32/api/winsvc/nc-winsvc-lphandler_function)**.<br /><br />Dieses Signal kann auch von einer Anwendung mit **[generateconsolectrlevent](generateconsolectrlevent.md)** generiert werden. |

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion das Steuersignal verarbeitet, sollte Sie " **true**" zurückgeben. Wenn **false** zurückgegeben wird, wird die nächste Handlerfunktion in der Liste der Handler für diesen Prozess verwendet.

## <a name="remarks"></a>Bemerkungen

Da das System einen neuen Thread im Prozess zum Ausführen der Handlerfunktion erstellt, ist es möglich, dass die Handlerfunktion von einem anderen Thread im Prozess beendet wird. Stellen Sie sicher, dass die Threads im Prozess mit dem Thread für die Handlerfunktion synchronisiert werden.

Jeder Konsolen Prozess verfügt über eine eigene Liste von **Handlerroutine** -Funktionen. Anfänglich enthält diese Liste nur eine Standardhandlerfunktion, die [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)aufruft. Bei einem Konsolen Prozess werden zusätzliche Handlerfunktionen durch Aufrufen der [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion hinzugefügt oder entfernt, die sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt. Wenn ein Konsolen Prozess eines der Steuersignale empfängt, werden seine Handlerfunktionen für eine zuletzt registrierte, erste aufrufende Basis aufgerufen, bis einer der Handler " **true**" zurückgibt. Wenn keiner der Handler **true** zurückgibt, wird der Standard Handler aufgerufen.

Das **Ereignis \_ STRG \_ Close**, das STRG-Abmelde **\_ \_ Ereignis** und das **STRG- \_ Shutdown \_** -Ereignis geben dem Prozess vor dem beenden eine Gelegenheit zum Bereinigen. Eine **Handlerroutine** kann alle notwendigen Bereinigungs Vorgänge ausführen und dann eine der folgenden Aktionen ausführen:

- Ruft die [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) -Funktion auf, um den Prozess zu beenden.
- Gibt **false** zurück. Wenn keine der registrierten Handlerfunktionen **true** zurückgibt, beendet der Standard Handler den Prozess.
- Gibt **true** zurück. In diesem Fall werden keine anderen Handlerfunktionen aufgerufen, und das System beendet den Prozess.

Ein Prozess kann die [**setprocessshutdownparameters**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setprocessshutdownparameters) -Funktion verwenden, um zu verhindern, dass das System während des Abmelde-oder herunter Fahrens ein Dialogfeld für den Benutzer anzeigt. In diesem Fall beendet das System den Prozess, wenn **Handlerroutine** den Wert " **true** " zurückgibt oder wenn die Timeout Spanne abläuft.

Wenn eine Konsolenanwendung als Dienst ausgeführt wird, erhält Sie einen geänderten standardmäßigen Konsolen Steuerungs Handler. Dieser geänderte Handler Ruft bei der Verarbeitung des Strg-Abmelde **\_ \_ Ereignisses** und des Strg- **\_ Shutdown- \_ Ereignisses** " [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) " nicht auf. Dadurch kann der Dienst weiter ausgeführt werden, nachdem sich der Benutzer abgemeldet hat. Wenn der Dienst einen eigenen Konsolen Steuerungs Handler installiert, wird dieser Handler vor dem Standard Handler aufgerufen. Wenn der installierte Handler **ExitProcess** aufruft, wenn das STRG-Abmelde **\_ \_ Ereignis** Signal verarbeitet wird, wird der Dienst beendet, wenn sich der Benutzer abmeldet.

Beachten Sie, dass eine Drittanbieter Bibliothek oder-dll einen Konsolen Steuerungs Handler für Ihre Anwendung installieren kann. Wenn dies der Fall ist, überschreibt dieser Handler den Standard Handler und kann dazu führen, dass die Anwendung beendet wird, wenn sich der Benutzer abmeldet.

## <a name="timeouts"></a>Zeitlimits

| Ereignis                  | Umstände                   | Timeout                                                     |
|------------------------|---------------------------------|-------------------------------------------------------------|
| `CTRL_CLOSE_EVENT`     | _irgendeiner_                           | Systemparameter `SPI_GETHUNGAPPTIMEOUT` , 5000 ms            |
| `CTRL_LOGOFF_EVENT`    | _schneller_[1] | Registrierungsschlüssel `CriticalAppShutdownTimeout` oder 500 ms          |
| `CTRL_LOGOFF_EVENT`    | _keine der obigen Angaben_             | Systemparameter `SPI_GETWAITTOKILLTIMEOUT` , 5000 ms         |
| `CTRL_SHUTDOWN_EVENT`  | **Dienst Prozess**             | Systemparameter `SPI_GETWAITTOKILLSERVICETIMEOUT` , 20000ms |
| `CTRL_SHUTDOWN_EVENT`  | _schneller_[1] | Registrierungsschlüssel `CriticalAppShutdownTimeout` oder 500 ms          |
| `CTRL_SHUTDOWN_EVENT`  | _keine der obigen Angaben_             | Systemparameter `SPI_GETWAITTOKILLTIMEOUT` , 5000 ms         |
| `CTRL_C`, `CTRL_BREAK` | _irgendeiner_                           | **kein Timeout**                                              |

_[1]: "schnelle" Ereignisse werden niemals verwendet, aber es gibt noch Code, um Sie zu unterstützen._

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ConsoleApi.h (über WinCon.h, Windows.h einschließen) |

## <a name="see-also"></a>Siehe auch

[Konsolen-Bearbeitungssteuerelemente](console-control-handlers.md)

[Konsolenfunktionen](console-functions.md)

[**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**Getprocessshutdownparameters**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocessshutdownparameters)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**Setprocessshutdownparameters**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setprocessshutdownparameters)