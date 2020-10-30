---
title: Read ConsoleInput-Funktion
description: Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38778931522dff8d1d000bb6f0ce13c2849d76db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039488"
---
# <a name="readconsoleinput-function"></a>Read ConsoleInput-Funktion

Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a>Parameter

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ vorgenommen\]  
Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die die Eingabepuffer Daten empfangen.

*nlength* \[ in\]  
Die Größe des Arrays, auf das durch den *lpBuffer* -Parameter in Array Elementen verwiesen wird.

*lpnumofeventsread* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der gelesenen Eingabedaten Sätze empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der im *nlength* -Parameter angeforderten Datensätze die Anzahl der Datensätze überschreitet, die im Puffer verfügbar sind, wird die Anzahl der verfügbaren Datensätze gelesen. Die Funktion gibt erst zurück, wenn mindestens ein Eingabedaten Satz gelesen wurde.

Ein Prozess kann ein Konsolen Eingabepuffer Handle in einer der Wait- [Funktionen](https://msdn.microsoft.com/library/windows/desktop/ms687069) angeben, um zu bestimmen, wann eine ungelesene Konsolen Eingabe vorhanden ist. Wenn der Eingabepuffer nicht leer ist, wird der Status eines Konsolen Eingabepuffer-Handles signalisiert.

Verwenden Sie die [**getnummeriofconsoleinputevents**](getnumberofconsoleinputevents.md) -Funktion, um die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer einer Konsole zu ermitteln. Um Eingabedaten Sätze aus einem Konsolen Eingabepuffer zu lesen, ohne die Anzahl der ungelesenen Datensätze zu beeinträchtigen, verwenden Sie die Funktion " [**Peer**](peekconsoleinput.md) . Verwenden Sie die [**flushconsoleinputbuffer**](flushconsoleinputbuffer.md) -Funktion, um alle ungelesenen Datensätze im Eingabepuffer einer Konsole zu verwerfen.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Consoleapi. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | "Read **consolinput w** (Unicode)" und "read **consolinput a** " (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)

[Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)
