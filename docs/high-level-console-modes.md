---
title: Konsolen Modi High-Level
description: Das Verhalten der hauptkonsolen Funktionen ist von den Konsolen Eingabe-und Ausgabe Modi betroffen.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: 418983a788957578e97fee70624fd80c1b09bc04
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038642"
---
# <a name="high-level-console-modes"></a>Konsolen Modi High-Level

Das Verhalten der hauptkonsolen Funktionen ist von den Konsolen Eingabe-und Ausgabe Modi betroffen. Alle folgenden Konsolen Eingabemodi werden bei der Erstellung einer-Konsole für den Eingabepuffer einer Konsole aktiviert:

- Zeilen Eingabemodus
- Verarbeiteter Eingabemodus
- Echo Eingabemodus

Beide der folgenden Konsolenausgabe Modi sind bei der Erstellung für einen Konsolenbildschirm Puffer aktiviert:

- Verarbeiteter Ausgabemodus
- Umwickeln im EOL-Ausgabemodus

Alle drei Eingabemodi, zusammen mit dem verarbeiteten Ausgabemodus, sind so konzipiert, dass Sie zusammenarbeiten. Es empfiehlt sich, alle diese Modi als Gruppe zu aktivieren oder zu deaktivieren. Wenn alle aktiviert sind, wird die Anwendung als "gekochter" Modus bezeichnet, was bedeutet, dass der meiste Teil der Verarbeitung für die Anwendung verarbeitet wird. Wenn alle deaktiviert sind, befindet sich die Anwendung im RAW-Modus, was bedeutet, dass die Eingabe ungefiltert und jede Verarbeitung an die Anwendung übertragen wird.

Eine Anwendung kann die [**getconsolemode**](getconsolemode.md) -Funktion verwenden, um den aktuellen Modus des Eingabe Puffers oder Bildschirm Puffers einer Konsole zu ermitteln. Sie können jeden dieser Modi aktivieren oder deaktivieren, indem Sie die folgenden Werte in der [**setconsolemode**](setconsolemode.md) -Funktion verwenden. Beachten Sie, dass sich das Festlegen des Ausgabemodus eines Bildschirm Puffers nicht auf den Ausgabemodus anderer Bildschirm Puffer auswirkt.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
