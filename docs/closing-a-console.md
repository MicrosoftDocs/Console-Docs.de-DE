---
title: Schließen einer Konsole
description: Ein Prozess kann die freeconsole-Funktion verwenden, um sich von seiner Konsole zu trennen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: bdd6b98f96f4ecb64aa6750396c30ef2dd6d0f74
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060178"
---
# <a name="closing-a-console"></a>Schließen einer Konsole


Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von seiner Konsole zu trennen. Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen. Nachdem **freeconsole**aufgerufen wurde, kann der Prozess mithilfe von " [**Zuweisung**](allocconsole.md) " eine neue Konsole oder eine anfügekonsole zum Anfügen an eine andere Konsole erstellen. [**AttachConsole**](attachconsole.md)

Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder [**freeconsole**](freeconsole.md)aufruft.

 

 




