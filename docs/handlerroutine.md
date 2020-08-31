---
title: Handlerroutine-Rückruffunktion
description: Eine Anwendungs definierte Funktion, die mit der SetConsoleCtrlHandler-Funktion verwendet wird. Ein Konsolen Prozess verwendet diese Funktion zum Behandeln von Steuerungs Signalen, die vom Prozess empfangen werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
- Wincon.h
api_type:
- UserDefined
ms.openlocfilehash: 14205baaddd98c8c22881c5f448119412e1f4a1c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060123"
---
# <a name="handlerroutine-callback-function"></a>Handlerroutine-Rückruffunktion


Eine Anwendungs definierte Funktion, die mit der [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion verwendet wird. Ein Konsolen Prozess verwendet diese Funktion zum Behandeln von Steuerungs Signalen, die vom Prozess empfangen werden. Wenn das Signal empfangen wird, erstellt das System einen neuen Thread im Prozess zum Ausführen der Funktion.

Der Typ der **phandler- \_ Routine** definiert einen Zeiger auf diese Rückruffunktion. **Handlerroutine** ist ein Platzhalter für den Namen der Anwendungs definierten Funktion.

<a name="syntax"></a>Syntax
------

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

<a name="parameters"></a>Parameter
----------

*dwctrltype* \[ in\]  
Der Typ des vom Handler empfangenen Steuersignal. Dieser Parameter kann einen der folgenden Werte aufweisen.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Bedeutung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</td>
<td><p>Ein STRG + C-Signal wurde empfangen, entweder von der Tastatureingabe oder von einem Signal, das von der <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>generateconsolectrlevent</strong></a> -Funktion generiert wurde.</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</td>
<td><p>Ein STRG + UNTBR-Signal wurde entweder von der Tastatureingabe oder von einem von <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>generateconsolectrlevent</strong></a>generierten Signal empfangen.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_CLOSE_EVENT"></span><span id="ctrl_close_event"></span>
<strong>CTRL_CLOSE_EVENT</strong> 2</td>
<td><p>Ein Signal, das das System an alle Prozesse sendet, die an eine Konsole angefügt werden, wenn der Benutzer die Konsole schließt (durch Klicken auf <strong>Schließen</strong> im Konsolenfenster&#39;Fenstermenü des s oder durch Klicken auf den Schaltflächen Befehl " <strong>Task beenden</strong> " im Task-Manager).</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_LOGOFF_EVENT"></span><span id="ctrl_logoff_event"></span>
<strong>CTRL_LOGOFF_EVENT</strong> 5</td>
<td><p>Ein Signal, das das System an alle Konsolen Prozesse sendet, wenn sich der Benutzer abmeldet. Dieses Signal gibt nicht an, welcher Benutzer sich abmeldet, daher können keine Annahmen getroffen werden.</p>
<p>Beachten Sie, dass dieses Signal nur von Diensten empfangen wird. Interaktive Anwendungen werden bei der Abmeldung beendet, sodass Sie nicht vorhanden sind, wenn das System dieses Signal sendet.</p></td>
</tr>
<tr class="odd">
<td><span id="CTRL_SHUTDOWN_EVENT"></span><span id="ctrl_shutdown_event"></span>
<strong>CTRL_SHUTDOWN_EVENT</strong> 6</td>
<td><p>Ein Signal, das das System sendet, wenn das System heruntergefahren wird. Interaktive Anwendungen sind nicht in der Zeit vorhanden, in der das System dieses Signal sendet. Daher kann es in dieser Situation nur als Dienste empfangen werden. Dienste verfügen auch über einen eigenen Benachrichtigungs Mechanismus für das Herunterfahren von Ereignissen. Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/ms683240" data-raw-source="[&lt;strong&gt;Handler&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/ms683240)"><strong>Handler</strong></a>.</p>
<p>Dieses Signal kann auch von einer Anwendung mit <a href="generateconsolectrlevent.md" data-raw-source="[&lt;strong&gt;GenerateConsoleCtrlEvent&lt;/strong&gt;](generateconsolectrlevent.md)"><strong>generateconsolectrlevent</strong></a>generiert werden.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Rückgabewert
------------

Wenn die Funktion das Steuersignal verarbeitet, sollte Sie " **true**" zurückgeben. Wenn **false**zurückgegeben wird, wird die nächste Handlerfunktion in der Liste der Handler für diesen Prozess verwendet.

<a name="remarks"></a>Hinweise
-------

Da das System einen neuen Thread im Prozess zum Ausführen der Handlerfunktion erstellt, ist es möglich, dass die Handlerfunktion von einem anderen Thread im Prozess beendet wird. Stellen Sie sicher, dass die Threads im Prozess mit dem Thread für die Handlerfunktion synchronisiert werden.

Jeder Konsolen Prozess verfügt über eine eigene Liste von **Handlerroutine** -Funktionen. Anfänglich enthält diese Liste nur eine Standardhandlerfunktion, die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)aufruft. Bei einem Konsolen Prozess werden zusätzliche Handlerfunktionen durch Aufrufen der [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion hinzugefügt oder entfernt, die sich nicht auf die Liste der Handlerfunktionen für andere Prozesse auswirkt. Wenn ein Konsolen Prozess eines der Steuersignale empfängt, werden seine Handlerfunktionen für eine zuletzt registrierte, erste aufrufende Basis aufgerufen, bis einer der Handler " **true**" zurückgibt. Wenn keiner der Handler **true**zurückgibt, wird der Standard Handler aufgerufen.

Das **Ereignis \_ STRG \_ Close**, das STRG-Abmelde ** \_ \_ Ereignis**und das **STRG- \_ Shutdown \_ ** -Ereignis geben dem Prozess vor dem beenden eine Gelegenheit zum Bereinigen. Eine **Handlerroutine** kann alle notwendigen Bereinigungs Vorgänge ausführen und dann eine der folgenden Aktionen ausführen:

- Ruft die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion auf, um den Prozess zu beenden.
- Gibt **false**zurück. Wenn keine der registrierten Handlerfunktionen **true**zurückgibt, beendet der Standard Handler den Prozess.
- Gibt **true**zurück. In diesem Fall werden keine anderen Handlerfunktionen aufgerufen, und das System beendet den Prozess.

Ein Prozess kann die [**setprocessshutdownparameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227) -Funktion verwenden, um zu verhindern, dass das System während des Abmelde-oder herunter Fahrens ein Dialogfeld für den Benutzer anzeigt. In diesem Fall beendet das System den Prozess, wenn **Handlerroutine** den Wert " **true** " zurückgibt oder wenn die Timeout Spanne abläuft.

Wenn eine Konsolenanwendung als Dienst ausgeführt wird, erhält Sie einen geänderten standardmäßigen Konsolen Steuerungs Handler. Dieser geänderte Handler Ruft bei der Verarbeitung des Strg-Abmelde ** \_ \_ Ereignisses** und des Strg- ** \_ Shutdown- \_ Ereignisses** " [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) " nicht auf. Dadurch kann der Dienst weiter ausgeführt werden, nachdem sich der Benutzer abgemeldet hat. Wenn der Dienst einen eigenen Konsolen Steuerungs Handler installiert, wird dieser Handler vor dem Standard Handler aufgerufen. Wenn der installierte Handler **ExitProcess** aufruft, wenn das STRG-Abmelde ** \_ \_ Ereignis** Signal verarbeitet wird, wird der Dienst beendet, wenn sich der Benutzer abmeldet.

Beachten Sie, dass eine Drittanbieter Bibliothek oder-dll einen Konsolen Steuerungs Handler für Ihre Anwendung installieren kann. Wenn dies der Fall ist, überschreibt dieser Handler den Standard Handler und kann dazu führen, dass die Anwendung beendet wird, wenn sich der Benutzer abmeldet.

## <a name="timeouts"></a>Timeouts

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
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Siehe auch


[Konsolen Steuerungs Handler](console-control-handlers.md)

[Konsolenfunktionen](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**Generateconsolectrlevent**](generateconsolectrlevent.md)

[**Getprocessshutdownparameters**](https://msdn.microsoft.com/library/windows/desktop/ms683221)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**Setprocessshutdownparameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227)

 

 




