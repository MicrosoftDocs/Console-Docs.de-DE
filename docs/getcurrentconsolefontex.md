---
title: Getcurrentconsolefontex-Funktion
description: Siehe Referenzinformationen zur getcurrentconsolefontex-Funktion, die erweiterte Informationen zur aktuell verwendeten Konsolen Schriftart abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e499cdb51a5ca71948dd40ebd3d4d151f2d71a8a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038728"
---
# <a name="getcurrentconsolefontex-function"></a>Getcurrentconsolefontex-Funktion

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Ruft erweiterte Informationen über die aktuelle Konsolen Schriftart ab.

## <a name="syntax"></a>Syntax

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a>Parameter

*hconsoleoutput* \[ in\]  
Ein Handle für den Bildschirm Puffer der Konsole. Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen. Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*bmaximumwindow* \[ in\]  
Wenn dieser Parameter **true** ist, werden für die maximale Fenstergröße Schriftart Informationen abgerufen. Wenn dieser Parameter **false** ist, werden für die aktuelle Fenstergröße Schriftart Informationen abgerufen.

*lpconsolecurrentfontex* \[ vorgenommen\]  
Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md) -Struktur, die die angeforderten Schriftart Informationen empfängt.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows Vista \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2008 \[ -Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md)
