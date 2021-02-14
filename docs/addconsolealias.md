---
title: Addconsolealias-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur addconsolealias-Funktion, die einen Konsolen Alias für die angegebene ausführbare Datei definiert.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9ff901615fa2a17ee9902bd028a2f63ee6b7a4b4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357870"
---
# <a name="addconsolealias-function"></a>Addconsolealias-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Definiert einen konsolenalias für die angegebene ausführbare Datei.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a>Parameter

*Quelle* \[ in\]  
Der konsolenalias, der dem durch *target* angegebenen Text zugeordnet werden soll.

*Ziel* \[ in\]  
Der Text, der als *Quelle* ersetzt werden soll. Wenn dieser Parameter **null** ist, wird der Konsolen Alias entfernt.

*EXEName* \[ in\]  
Der Name der ausführbaren Datei, für die der konsolenalias definiert werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert " **true**".

Wenn die Funktion fehlschlägt, ist der Rückgabewert **false**. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.

## <a name="remarks"></a>Bemerkungen

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Konsolen Aliase](console-aliases.md).

## <a name="requirements"></a>Anforderungen

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 2000 Professional \[nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Windows 2000 Server \[nur Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Addconsolealiasw** (Unicode) und **addconsolealiasa** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenaliase](console-aliases.md)

[Konsolenfunktionen](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)