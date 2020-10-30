---
title: Getconsolealiasexeslength-Funktion
description: Ruft die erforderliche Größe für den Puffer ab, der von der getconsolealiasexes-Funktion verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d204fd3effe5169b6be3e60a9e3c0d39fa418d20
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038908"
---
# <a name="getconsolealiasexeslength-function"></a>Getconsolealiasexeslength-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiasexes**](getconsolealiasexes.md) -Funktion verwendet wird.

## <a name="syntax"></a>Syntax

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

## <a name="parameters"></a>Parameter

Diese Funktion besitzt keine Parameter.

## <a name="return-value"></a>Rückgabewert

Die Größe des Puffers, der zum Speichern der Namen aller ausführbaren Dateien erforderlich ist, für die Konsolen Aliase definiert sind (in Bytes).

## <a name="remarks"></a>Bemerkungen

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |
| Unicode- und ANSI-Name | **Getconsolealiasexeslengthw** (Unicode) und **getconsolealiasexeslengtha** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[**AddConsoleAlias**](addconsolealias.md)

[Konsolenaliase](console-aliases.md)

[Konsolenfunktionen](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
