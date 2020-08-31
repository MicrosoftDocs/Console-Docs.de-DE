---
title: STRG + schließen-Signal
description: Das System generiert ein STRG + schließen-Signal, wenn der Benutzer eine Konsole schließt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: a44f54e5c73c77155d4aa1d8307375c176463a49
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059890"
---
# <a name="ctrlclose-signal"></a>STRG + schließen-Signal


Das System generiert ein STRG + schließen-Signal, wenn der Benutzer eine Konsole schließt. Alle Prozesse, die an die Konsole angefügt sind, erhalten das Signal, sodass jeder Prozess vor dem beenden eine Bereinigungs Möglichkeit erhält. Wenn ein Prozess dieses Signal empfängt, kann die Handlerfunktion nach dem Ausführen von Bereinigungs Vorgängen eine der folgenden Aktionen ausführen:

- Wenden Sie [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) an, um den Prozess zu beenden.
- Gibt **false**zurück. Wenn keine der registrierten Handlerfunktionen **true**zurückgibt, beendet der Standard Handler den Prozess.
- Gibt **true**zurück. In diesem Fall werden keine anderen Handlerfunktionen aufgerufen, und der Prozess wird beendet.

 

 




