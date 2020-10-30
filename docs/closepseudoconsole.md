---
title: Closepseudoconsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur closepseudoconsole-Funktion, die eine Pseudo Console aus dem angegebenen Handle schließt.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037288"
---
# <a name="closepseudoconsole-function"></a>Closepseudoconsole-Funktion

Schließt eine pseudoconsole aus dem angegebenen Handle.

## <a name="syntax"></a>Syntax

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a>Parameter

*HPC* \[ in\]  
Ein Handle für eine aktive pseudoconsole, wie von " [kreatepseudoconsole](createpseudoconsole.md)" geöffnet.

## <a name="return-value"></a>Rückgabewert

*keine*

## <a name="remarks"></a>Bemerkungen

Wenn Sie eine Pseudo Konsole schließen, werden auch Client Anwendungen beendet, die an die Sitzung angefügt sind.

Wenn diese API aufgerufen wird, wird möglicherweise ein abschließender Rahmen auf dem `hOutput` Handle angezeigt, das ursprünglich für " [kreatepsuedoconsole](createpseudoconsole.md) " bereitgestellt wurde. Es wird erwartet, dass der Aufrufer diese Informationen aus dem Kommunikationskanal Puffer abfließt und ihn entweder vornimmt oder verwerfen kann. Wenn der Puffer nicht entladen wird, kann es passieren, dass der Close-Befehl unbegrenzt wartet, bis er entladen wird oder die Kommunikationskanäle anders voneinander getrennt sind.

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

[**ResizePseudoConsole**](resizepseudoconsole.md)
