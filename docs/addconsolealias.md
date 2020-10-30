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
ms.openlocfilehash: 2f2396122e693ab76ddf4e4e0bcdb2d38a2c042b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037552"
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

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert " **true** ".

Wenn die Funktion fehlschlägt, ist der Rückgabewert **false** . Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Konsolen Aliase](console-aliases.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Addconsolealiasw** (Unicode) und **addconsolealiasa** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenaliase](console-aliases.md)

[Konsolenfunktionen](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
