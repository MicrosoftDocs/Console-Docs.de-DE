---
title: Getconsolealias-Funktion
description: Ruft den Text für den angegebenen konsolenalias und den Namen der ausführbaren Datei ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 37c441c48c2bb71fc8e590d4f8a80032561f833e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039028"
---
# <a name="getconsolealias-function"></a>Getconsolealias-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft den Text für den angegebenen konsolenalias und die ausführbare Datei ab.

## <a name="syntax"></a>Syntax

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a>Parameter

*lpSource* \[ in\]  
Der konsolenalias, dessen Text abgerufen werden soll.

*lptargetbuffer* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der den dem Konsolen Alias zugeordneten Text empfängt.

*Targetbufferlength* \[ in\]  
Die Größe des Puffers, auf den von *lptargetbuffer* verwiesen wird (in Bytes).

*lpexename* \[ in\]  
Der Name der ausführbaren Datei.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

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
| Unicode- und ANSI-Name | **Getconsolealiasw** (Unicode) und **getconsolealiasa** (ANSI) |

## <a name="see-also"></a>Weitere Informationen

[Konsolenaliase](console-aliases.md)

[Konsolenfunktionen](console-functions.md)

[**AddConsoleAlias**](addconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
