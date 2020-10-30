---
title: Schließen einer Konsole
description: Ein Prozess kann die freeconsole-Funktion verwenden, um sich von seiner Konsole zu trennen.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: db424e6d9fc91a7a3b6cff3b5fc5028833d208f9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037318"
---
# <a name="closing-a-console"></a>Schließen einer Konsole

Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von seiner Konsole zu trennen. Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen. Nachdem **freeconsole** aufgerufen wurde, kann der Prozess mithilfe von " [**Zuweisung**](allocconsole.md) " eine neue Konsole oder eine anfügekonsole zum Anfügen an eine andere Konsole erstellen. [**AttachConsole**](attachconsole.md)

Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder [**freeconsole**](freeconsole.md)aufruft.
