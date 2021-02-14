---
title: STRG + schließen-Signal
description: Das System generiert ein STRG + schließen-Signal, wenn der Benutzer eine Konsole schließt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: be237eac7649ad76615aea341a555a8a7af6445c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357890"
---
# <a name="ctrlclose-signal"></a>STRG + schließen-Signal

Das System generiert ein STRG + schließen-Signal, wenn der Benutzer eine Konsole schließt. Alle Prozesse, die an die Konsole angefügt sind, erhalten das Signal, sodass jeder Prozess vor dem beenden eine Bereinigungs Möglichkeit erhält. Wenn ein Prozess dieses Signal empfängt, kann die Handlerfunktion nach dem Ausführen von Bereinigungs Vorgängen eine der folgenden Aktionen ausführen:

- Wenden Sie [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) an, um den Prozess zu beenden.
- Gibt **false** zurück. Wenn keine der registrierten Handlerfunktionen **true** zurückgibt, beendet der Standard Handler den Prozess.
- Gibt **true** zurück. In diesem Fall werden keine anderen Handlerfunktionen aufgerufen, und der Prozess wird beendet.