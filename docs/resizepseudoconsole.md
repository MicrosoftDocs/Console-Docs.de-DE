---
title: Resizepseudoconsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur resizepseudoconsole-Funktion, die die Größe der internen Puffer für eine Pseudo Konsole auf die angegebene Größe anpasst.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037538"
---
# <a name="resizepseudoconsole-function"></a>Resizepseudoconsole-Funktion

Ändert die Größe der internen Puffer für eine pseudoconsole auf die angegebene Größe.

## <a name="syntax"></a>Syntax

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a>Parameter

*HPC* \[ in\]  
Ein Handle für eine aktive pseudoconsole, wie von " [kreatepseudoconsole](createpseudoconsole.md)" geöffnet.

*Größe* \[ in\]  
Die Abmessungen des Fensters/Puffers in der Anzahl von Zeichen, die für den internen Puffer dieser pseudoconsole verwendet werden.

## <a name="return-value"></a>Rückgabewert

Typ: **HRESULT**

Wenn diese Methode erfolgreich ausgeführt wird, wird **S_OK** zurückgegeben. Andernfalls wird ein **HRESULT** -Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Diese Funktion kann die Größe der internen Puffer in der pseudoconsole-Sitzung ändern, sodass Sie der Fenster-/Puffergröße entspricht, die für die Anzeige am Terminal Ende verwendet wird. Dadurch wird sichergestellt, dass für die Kommunikation angefügte Command-Line Interface (CUI)-Anwendungen, die die [Konsolenfunktionen](console-functions.md) verwenden, die richtigen Dimensionen in ihren Aufrufen zurückgegeben werden.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Windows 10-Update vom Oktober 2018 (Version 1809) \[ nur Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2019 \[ -Desktop-Apps\] |
| Header | Consoleapi. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Pseudo Konsolen](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
