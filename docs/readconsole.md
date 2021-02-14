---
title: Funktion "Read Console"
description: Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 757d770bc7fea543d15678af5f80f15c17dd0e82
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358280"
---
# <a name="readconsole-function"></a>Funktion "Read Console"

Liest Zeichen Eingaben aus dem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a>Parameter

*hconsoleinput* \[ in\]  
Ein Handle für den Konsolen Eingabepuffer. Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der die aus dem Konsolen Eingabepuffer gelesenen Daten empfängt.

*nnumofcharstoread* \[ in\]  
Die Anzahl der zu lesenden Zeichen. Die Größe des Puffers, auf den der *lpBuffer* -Parameter verweist, muss mindestens `nNumberOfCharsToRead * sizeof(TCHAR)` Bytes betragen.

*lpnumofcharsread* \[ vorgenommen\]  
Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Zeichen empfängt.

*pinputcontrol* \[ in, optional\]  
Ein Zeiger auf eine [**Konsolen-einfügekonsolen- \_ \_ Steuer**](console-readconsole-control.md) Elementstruktur, die ein Steuerzeichen angibt, das das Ende des Lesevorgangs signalisiert. Dieser Parameter kann **NULL** sein.

Dieser Parameter erfordert standardmäßig Unicode-Eingaben. Legen Sie für den ANSI-Modus diesen Parameter auf **null** fest.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

Die **Lese Konsole** liest Tastatureingaben aus dem Eingabepuffer einer Konsole. Sie verhält sich wie die Funktion "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) ", mit dem Unterschied, dass Sie entweder in Unicode (Wide-Character) oder ANSI-Modus gelesen werden kann. Verwenden Sie die **infoconsole** anstelle von " **Infofile**", damit Anwendungen, die einen einzelnen Satz von Quellen verwalten, mit beiden Modi kompatibel sind. Obwohl die **infoconsole** nur mit einem Konsolen Eingabepuffer Handle verwendet werden kann, kann die **Infodatei** mit anderen Handles (z. b. Dateien oder Pipes) verwendet werden. Der Wert von "read **Console** " schlägt fehl, wenn er mit einem Standard Handle verwendet wird, das zu einem anderen als einem Konsolen handle umgeleitet wurde.

Alle Eingabemodi, die das Verhalten von " [**Infofile**](/windows/win32/api/fileapi/nf-fileapi-readfile) " beeinflussen, haben in der " **infoconsole**" dieselbe Wirkung. Um die Eingabemodi eines Konsolen Eingabe Puffers abzurufen und festzulegen, verwenden Sie die Funktionen [**getconsolemode**](getconsolemode.md) und [**setconsolemode**](setconsolemode.md) .

Wenn der Eingabepuffer andere Eingabeereignisse als Tastatur Ereignisse enthält (z. b. Mausereignisse oder Ereignisse zum Ändern von Fenstern), werden diese verworfen. Diese Ereignisse können nur mit der Funktion " [**leseconsoleinput**](readconsoleinput.md) " gelesen werden.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

Der *pinputcontrol* -Parameter kann verwendet werden, um zwischengeschaltete Aufwecken aus dem Lesevorgang in Reaktion auf ein Steuerzeichen zu aktivieren, das in der [**\_ infoconsole- \_ Steuer**](console-readconsole-control.md) Elementstruktur der Konsole angegeben wird. Diese Funktion erfordert, dass Befehls Erweiterungen aktiviert werden, das Standardausgabe Handle als Konsolenausgabe Handle und Eingabe als Unicode.

**Windows Server 2003 und Windows XP/2000:** Das zwischen Lese Feature wird nicht unterstützt.

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ConsoleApi.h (über WinCon.h, Windows.h einschließen) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | "Read **consolew** (Unicode)" und "read **Consolea** " (ANSI) |

## <a name="see-also"></a>Siehe auch

[Konsolenfunktionen](console-functions.md)

[**Steuerelement für die Konsole der Konsole \_ \_**](console-readconsole-control.md)

[**GetConsoleMode**](getconsolemode.md)

[Ein- und Ausgabemethoden](input-and-output-methods.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsole**](writeconsole.md)