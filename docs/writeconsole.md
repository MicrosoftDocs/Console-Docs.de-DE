---
title: WriteConsole-Funktion
description: Schreibt eine Zeichenfolge in einen Konsolenbildschirm-Puffer, beginnend an der aktuellen Cursorposition.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357610"
---
# <a name="writeconsole-function"></a>WriteConsole-Funktion

Schreibt eine Zeichenfolge in einen Konsolenbildschirm-Puffer, beginnend an der aktuellen Cursorposition.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a>Parameter

*hConsoleOutput* \[in\]  
Ein Handle für den Konsolenbildschirm-Puffer. Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
Ein Zeiger auf einen Puffer, der Zeichen enthält, die in den Konsolenbildschirm-Puffer geschrieben werden sollen. Es wird erwartet, dass es sich um ein Array von `char` für `WriteConsoleA` oder von `wchar_t` für `WriteConsoleW` handelt.

*nNumberOfCharsToWrite* \[in\]  
Die Anzahl der zu schreibenden Zeichen. Wenn die Gesamtgröße der angegebenen Anzahl von Zeichen den verfügbaren Heap überschreitet, schlägt die Funktion mit **ERROR\_NOT\_ENOUGH\_MEMORY** fehl.

*lpNumberOfCharsWritten* \[out, optional\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.

*lpReserved* reserviert; muss **NULL** sein.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

Die **WriteConsole**-Funktion schreibt Zeichen an der aktuellen Cursorposition in den Konsolenbildschirm-Puffer. Die Cursorposition wird mit dem Schreiben von Zeichen vorgerückt. Die [**SetConsoleCursorPosition**](setconsolecursorposition.md)-Funktion legt die aktuelle Cursorposition fest.

Zeichen werden unter Verwendung der Vordergrund- und Hintergrundfarbenattribute geschrieben, die dem Konsolenbildschirm-Puffer zugeordnet sind. Die [**SetConsoleTextAttribute**](setconsoletextattribute.md)-Funktion ändert diese Farben. Um die aktuellen Farbattribute und die aktuelle Cursorposition zu bestimmen, verwenden Sie [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Alle Eingabemodi, die sich auf das Verhalten der [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)-Funktion auswirken, haben denselben Effekt auf **WriteConsole**. Zum Abrufen und Festlegen der Ausgabemodi eines Konsolenbildschirm-Puffers verwenden Sie die Funktionen [**GetConsoleMode**](getconsolemode.md) und [**SetConsoleMode**](setconsolemode.md).

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

**WriteConsole** schlägt fehl, wenn sie mit einem Standardhandle verwendet wird, das an eine Datei umgeleitet wird. Wenn eine Anwendung mehrsprachige Ausgaben verarbeitet, die umgeleitet werden können, stellen Sie fest, ob das Ausgabehandle ein Konsolenhandle ist (eine Methode besteht darin, die [**GetConsoleMode**](getconsolemode.md)-Funktion aufzurufen und zu überprüfen, ob sie erfolgreich ist). Wenn das Handle ein Konsolenhandle ist, rufen Sie **WriteConsole** auf. Wenn das Handle kein Konsolenhandle ist, wird die Ausgabe umgeleitet, und Sie sollten [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) aufrufen, um die E/A auszuführen. Stellen Sie sicher, dass Sie eine Unicode-Nur-Text-Datei mit einer Bytereihenfolge-Marke versehen. Weitere Informationen finden Sie unter [Verwenden von Bytereihenfolge-Marken](/windows/win32/intl/using-byte-order-marks).

Obwohl eine Anwendung **WriteConsole** im ANSI-Modus verwenden kann, um ANSI-Zeichen zu schreiben, unterstützen Konsolen keine „ANSI-Escapezeichen“ oder „virtuellen Terminal“sequenzen, sofern diese nicht aktiviert sind. Weitere Informationen, auch zur Anwendbarkeit von Betriebssystemversionen, finden Sie unter [**Virtuelle Konsolenterminalsequenzen**](console-virtual-terminal-sequences.md).

Wenn virtuelle Terminal-Escapesequenzen nicht aktiviert sind, können Konsolenfunktionen entsprechende Funktionalitäten bereitstellen. Weitere Informationen finden Sie unter [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md)und [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ConsoleApi.h (über WinCon.h, Windows.h einschließen) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **WriteConsoleW** (Unicode) und **WriteConsoleA** (ANSI) |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleMode**](getconsolemode.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Ein- und Ausgabemethoden](input-and-output-methods.md)

[**ReadConsole**](readconsole.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)