---
title: Getconsolealiaseslength-Funktion
description: Ruft die erforderliche Größe für den Puffer ab, der von der getconsolealiases-Funktion verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 395acba39600fe1a98a80ed06ea23646b0b9f174
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038958"
---
# <a name="getconsolealiaseslength-function"></a>Getconsolealiaseslength-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft die erforderliche Größe für den Puffer ab, der von der [**getconsolealiases**](getconsolealiases.md) -Funktion verwendet wird.

## <a name="syntax"></a>Syntax

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a>Parameter

*lpexename* \[ in\]  
Der Name der ausführbaren Datei, deren Konsolen Aliase abgerufen werden sollen.

## <a name="return-value"></a>Rückgabewert

Die Größe des Puffers, der zum Speichern aller für diese ausführbaren Datei definierten Konsolen Aliase in Bytes erforderlich ist.

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
| Unicode- und ANSI-Name | **Getconsolealiaseslengthw** (Unicode) und **getconsolealiaseslengtha** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[**AddConsoleAlias**](addconsolealias.md)

[Konsolenaliase](console-aliases.md)

[Konsolenfunktionen](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
