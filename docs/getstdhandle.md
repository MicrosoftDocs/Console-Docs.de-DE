---
title: Getstdhandle-Funktion
description: Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420209"
---
# <a name="getstdhandle-function"></a>Getstdhandle-Funktion

Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).

## <a name="syntax"></a>Syntax

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>Parameter

*nstdhandle* \[ in\]  
Das Standardgerät. Dieser Parameter kann einen der folgenden Werte aufweisen.

| Wert | Bedeutung |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | Das Standardeingabe Gerät. Anfänglich ist dies der Konsolen Eingabepuffer `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | Das Standardausgabe Gerät. Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | Das Standardfehler Gerät. Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` . |

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für das angegebene Gerät oder ein umgeleitetes handle, das durch einen vorherigen-Befehl von [**setstdhandle**](setstdhandle.md)festgelegt wurde. Das Handle verfügt über **allgemeine \_ Lese** -und **allgemeine \_ Schreib** Zugriffsrechte, es sei denn, die Anwendung hat **setstdhandle** verwendet, um ein Standard Handle mit geringerem Zugriff festzulegen.

Wenn die Funktion fehlschlägt, ist der Rückgabewert ein **ungültiger \_ handle- \_ Wert**. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Wenn einer Anwendung keine Standard Handles zugeordnet sind, z. b. ein Dienst, der auf einem interaktiven Desktop ausgeführt wird, und Sie nicht umgeleitet hat, ist der Rückgabewert **null**.

## <a name="remarks"></a>Hinweise

Von **getstdhandle** zurückgegebene Handles können von Anwendungen verwendet werden, die aus der Konsole lesen oder in diese schreiben müssen. Wenn eine-Konsole erstellt wird, ist das Standardeingabe Handle ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standard-Fehler Handles sind Handles des aktiven Bildschirm Puffers der Konsole. Diese Handles können von den Funktionen " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**schreitefile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder von einer der Konsolenfunktionen verwendet werden, die auf den Konsolen Eingabepuffer oder einen Bildschirm Puffer zugreifen (z. b. die Funktionen " [**infoconsoleinput**](readconsoleinput.md)", " [**Write Console**](writeconsole.md)" oder " [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) ").

Die Standard Handles eines Prozesses können durch einen aufzurufenden [**setstdhandle**](setstdhandle.md)umgeleitet werden. in diesem Fall gibt **getstdhandle** das umgeleitete Handle zurück. Wenn die Standard Handles umgeleitet wurden, können Sie den `CONIN$` Wert in einem Aufrufen der Funktion "- [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) Funktion" angeben, um ein Handle für den Eingabepuffer einer Konsole zu erhalten. Entsprechend können Sie den Wert angeben, `CONOUT$` um ein Handle für den aktiven Bildschirm Puffer einer Konsole zu erhalten.

Die Standard Handles eines Prozesses für den Eintrag der Main-Methode werden durch die Konfiguration des [**/Subsystem**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) -Flags vorgegeben, das beim Erstellen der Anwendung an den Linker weitergegeben wurde. Durch Angeben von **/Subsystem: Console** wird angefordert, dass das Betriebssystem die Handles beim Start mit einer Konsolen Sitzung aufgefüllt, wenn das übergeordnete Element die Standard handle-Tabelle nicht bereits nach Vererbung ausgefüllt hat. Im Gegensatz dazu bedeutet **/Subsystem: Windows** , dass die Anwendung keine Konsole benötigt und wahrscheinlich nicht die Standard Handles verwendet. Weitere Informationen zur Behandlung von Vererbungen finden Sie in der Dokumentation zu [**Startf \_ usestdhandles**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Einige Anwendungen arbeiten außerhalb der Grenzen Ihres deklarierten Subsystems. Beispielsweise kann eine **/Subsystem: Windows** -Anwendung Standard Handles für Protokollierungs-oder Debugzwecke überprüfen/verwenden, aber normal mit einer grafischen Benutzeroberfläche arbeiten. Diese Anwendungen müssen den Status der Standard Handles beim Start sorgfältig überprüfen und mithilfe von [**attachconsole**](attachconsole.md), [**Zuordnungen Console**](allocconsole.md)und [**freeconsole**](freeconsole.md) eine Konsole hinzufügen bzw. entfernen, wenn gewünscht.

Einige Anwendungen können auch das Verhalten für den Typ des geerbten Handles verändern. Die Unterscheidung zwischen Konsolen, Pipe, Datei und anderen Typen kann mit " [**getfiletype**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype)" durchgeführt werden.

### <a name="attachdetach-behavior"></a>Verhalten beim Anfügen/trennen

Beim Anfügen an eine neue Konsole werden Standard Handles immer durch Konsolen Handles ersetzt, es sei denn, während der Prozesserstellung wurde **Startf \_ usestdhandles** angegeben.

Wenn der vorhandene Wert des Standard Handles **null** ist, oder wenn der vorhandene Wert des Standard Handles wie ein Konsolen Pseudo handle aussieht, wird das Handle durch ein Konsolen handle ersetzt.

Wenn ein übergeordnetes Element sowohl **Create \_ New \_ Console** als auch **Startf \_ usestdhandles** verwendet, um einen Konsolen Prozess zu erstellen, werden Standard Handles nicht ersetzt, es sei denn, der vorhandene Wert des Standard Handles ist **null** oder ein Konsolen Pseudo handle.

> [!NOTE]
>Konsolen Prozesse *müssen* mit den ausgefüllten Standard Handles beginnen oder automatisch mit den entsprechenden Handles für eine neue Konsole aufgefüllt werden. Grafische Benutzeroberflächen Anwendungen (GUI) können ohne die Standard Handles gestartet werden und werden nicht automatisch ausgefüllt.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Processenv. h (über Winbase. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[Konsolenhandles](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
