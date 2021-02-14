---
title: GetStdHandle-Funktion
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
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358750"
---
# <a name="getstdhandle-function"></a>GetStdHandle-Funktion

Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).

## <a name="syntax"></a>Syntax

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>Parameter

*nStdHandle* \[in\]  
Das Standardgerät. Dieser Parameter kann einen der folgenden Werte annehmen.

| Wert | Bedeutung |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | Das Standardeingabegerät. Anfänglich ist dies der Konsoleneingabepuffer, `CONIN$`. |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | Das Standardausgabegerät. Anfänglich ist dies der aktive Konsolenbildschirmpuffer, `CONOUT$`. |
| **STD_ERROR_HANDLE** (DWORD) -12 | Das Standardfehlergerät. Anfänglich ist dies der aktive Konsolenbildschirmpuffer, `CONOUT$`. |

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für das angegebene Gerät oder ein umgeleitetes Handle, das durch einen vorhergehenden Aufruf von [**SetStdHandle**](setstdhandle.md) festgelegt wurde. Das Handle verfügt über die Zugriffsrechte **GENERIC\_READ** und **GENERIC\_WRITE**, es sei denn, die Anwendung hat **SetStdHandle** verwendet, um ein Standardhandle mit geringeren Zugriffsrechten festzulegen.

Wenn bei der Ausführung der Funktion ein Fehler auftritt, lautet der Rückgabewert **INVALID\_HANDLE\_VALUE**. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

Wenn eine Anwendung nicht über zugeordnete Standardhandles verfügt, wie etwa ein Dienst, der auf einem interaktiven Desktop ausgeführt wird und diese nicht umgeleitet hat, ist der Rückgabewert **NULL**.

## <a name="remarks"></a>Bemerkungen

Von **GetStdHandle** zurückgegebene Handles können von Anwendungen verwendet werden, die aus der Konsole lesen oder in die Konsole schreiben müssen. Beim Erstellen einer Konsole ist das Standardeingabehandle ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe- und Standardfehlerhandles sind Handles für den aktiven Bildschirmpuffer der Konsole. Diese Handles können von den Funktionen [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) und [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) oder von jeder Konsolenfunktion verwendet werden, die auf den Konsoleneingabepuffer oder einen Bildschirmpuffer zugreift (beispielsweise die Funktionen [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) oder [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)).

Die Standardhandles eines Prozesses können durch einen Aufruf von [**SetStdHandle**](setstdhandle.md) umgeleitet werden. In diesem Fall gibt **GetStdHandle** das umgeleitete Handle zurück. Wenn die Standardhandles umgeleitet wurden, können Sie den `CONIN$`-Wert in einem Aufruf der Funktion [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) angeben, um ein Handle zum Eingabespeicher einer Konsole abzurufen. In ähnlicher Weise können Sie den `CONOUT$`-Wert angeben, um ein Handle für den aktiven Bildschirmpuffer einer Konsole abzurufen.

Die Standardhandles eines Prozesses beim Eintritt in die main-Methode werden durch die Konfiguration des [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem)-Flags vorgeschrieben, das dem Linker zum Zeitpunkt des Erstellens der Anwendung übergeben wurde. Für die Angabe von **/SUBSYSTEM:CONSOLE** ist es erforderlich, dass das Betriebssystem die Handles beim Start mit einer Konsolensitzung füllt, falls die Tabelle der Standardhandles nicht bereits mithilfe von Vererbung durch das übergeordnete Element aufgefüllt wurde. Im Gegensatz dazu impliziert **/SUBSYSTEM:WINDOWS**, dass die Anwendung keine Konsole benötigt und von den Standardhandles wahrscheinlich keinen Gebrauch machen wird. Weitere Informationen zur Handlevererbung finden Sie in der Dokumentation zu [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Einige Anwendungen werden außerhalb der Grenzen ihres deklarierten Subsystems betrieben; beispielsweise kann eine **/SUBSYSTEM:WINDOWS**-Anwendung die Standardhandles zu Protokollierungs- oder Debuggingzwecken überprüfen/verwenden, aber zugleich normal mit einer grafischen Benutzeroberfläche ausgeführt werden. Diese Anwendungen müssen den Zustand von Standardhandles beim Start sorgfältig überprüfen und [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md) sowie [**FreeConsole**](freeconsole.md) verwenden, um bei Bedarf eine Konsole hinzuzufügen bzw. zu entfernen.

Einige Anwendungen können sogar ihr Verhalten je nach dem Typ des geerbten Handles ändern. Die Unterscheidung des Typs zwischen Konsole, Pipe, Datei und anderen kann mithilfe von [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype) durchgeführt werden.

### <a name="attachdetach-behavior"></a>Verhalten beim Zuordnen/Trennen

Beim Zuordnen zu einer neuen Konsole werden Standardhandles immer durch Konsolenhandles ersetzt, es sei denn, während der Prozesserstellung wurde **STARTF\_USESTDHANDLES** angegeben.

Wenn der vorhandene Wert des Standardhandles **NULL** ist oder der vorhandene Wert des Standardhandles wie ein Konsolen-Pseudohandle aussieht, wird das Handle durch ein Konsolenhandle ersetzt.

Wenn ein übergeordnetes Element sowohl **CREATE\_NEW\_CONSOLE** als auch **STARTF\_USESTDHANDLES** verwendet, um einen Konsolenprozess zu erstellen, werden Standardhandles nicht ersetzt, es sei denn, der vorhandene Wert des Standardhandles ist **NULL**, oder es handelt sich um ein Konsolen-Pseudohandle.

> [!NOTE]
>Konsolenprozesse *müssen* mit gefüllten Standardhandles gestartet werden, sonst werden sie automatisch mit passenden Handles für eine neue Konsole gefüllt. GUI-Anwendungen (Anwendungen mit grafischer Benutzeroberfläche) können ohne die Standardhandles gestartet werden, und sie werden nicht automatisch gefüllt.

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen von Eingabepufferereignissen](reading-input-buffer-events.md).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ProcessEnv.h (via Winbase.h, include Windows.h) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[Konsolenhandles](console-handles.md)

[**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)