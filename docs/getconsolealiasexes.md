---
title: Getconsolealiasexes-Funktion
description: Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1a97df0c22f084389e9bd6df1c4a2e8863090b45
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357493"
---
# <a name="getconsolealiasexes-function"></a>Getconsolealiasexes-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.

## <a name="syntax"></a>Syntax

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a>Parameter

*lpexenamebuffer* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der die Namen der ausführbaren Dateien empfängt.

*Exenamebufferlength* \[ in\]  
Die Größe des Puffers, auf den *lpexenamebuffer* zeigt (in Bytes).

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die [**getconsolealiasexeslength**](getconsolealiasexeslength.md) -Funktion, um die erforderliche Größe für den *lpexenamebuffer* -Puffer zu ermitteln.

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Getconsolealiasexesw** (Unicode) und **getconsolealiasexesa** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[**AddConsoleAlias**](addconsolealias.md)

[Konsolenaliase](console-aliases.md)

[Konsolenfunktionen](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasExesLength**](getconsolealiasexeslength.md)

[**GetConsoleAliases**](getconsolealiases.md)