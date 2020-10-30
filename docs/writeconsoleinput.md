---
title: Funktion "Beschreib teconsoleinput"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Beschreib teconsoleinput", die Daten direkt in den Konsolen Eingabepuffer schreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc2c7930ab76587edc9ae1991d4493c858b0ec30
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039288"
---
# <a name="writeconsoleinput-function"></a>Funktion "Beschreib teconsoleinput"

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Schreibt Daten direkt in den Konsolen Eingabepuffer.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a>Parameter

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ in\]  
Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die Daten enthalten, die in den Eingabepuffer geschrieben werden sollen.

*nlength* \[ in\]  
Die Anzahl der Eingabedaten Sätze, die geschrieben werden sollen.

*lpnumofeventswritten* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Eingabedaten Sätze empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

" **Write-ConsoleInput** " fügt Eingabedaten Sätze in den Eingabepuffer hinter allen ausstehenden Ereignissen im Puffer ein. Der Eingabepuffer wächst bei Bedarf dynamisch, um so viele Ereignisse zu speichern, wie Sie geschrieben werden.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** . Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus. Dieser Vorgang wird als **[falsch-Wege-Verb](console-buffer-security-and-access-rights.md#wrong-way-verbs)** für diesen Puffer betrachtet. Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | Schreiben von " **Write-consolinput w** (Unicode)" und " **Write-consolinput a** " (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Eingabe \_ Daten Satz**](input-record-str.md)

[Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)

[**Mapvirtualkey**](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**Vkkeyscan**](https://msdn.microsoft.com/library/windows/desktop/ms646329)
