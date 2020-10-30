---
title: Konsolen Modi
description: Jedem Konsolen Eingabepuffer ist ein Satz von Eingabemodi zugeordnet, der sich auf Eingabe Vorgänge auswirkt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: 0bd048101546d20735745656677702f9f07115fd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039198"
---
# <a name="console-modes"></a>Konsolen Modi

Jedem Konsolen Eingabepuffer ist ein Satz von Eingabemodi zugeordnet, der sich auf Eingabe Vorgänge auswirkt. Ebenso hat jeder Konsolenbildschirm Puffer eine Reihe von Ausgabe Modi, die sich auf Ausgabe Vorgänge auswirken. Die Eingabemodi können in zwei Gruppen unterteilt werden: solche, die sich auf die Eingabefunktionen auf hoher Ebene auswirken, und diejenigen, die sich auf die Eingabefunktionen auf niedriger Ebene auswirken. Die Ausgabe Modi wirken sich nur auf Anwendungen aus, die die Ausgabefunktionen auf hoher Ebene verwenden.

Die [**getconsolemode**](getconsolemode.md) -Funktion meldet den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Bildschirm Puffers. Die [**setconsolemode**](setconsolemode.md) -Funktion legt den aktuellen Modus eines Konsolen Eingabe Puffers oder eines Bildschirm Puffers fest. Wenn in einer Konsole mehrere Bildschirm Puffer angezeigt werden, können die Ausgabe Modi der einzelnen angezeigt werden. Eine Anwendung kann e/a-Modi jederzeit ändern. Weitere Informationen zu den Konsolen Modi, die e/a-Vorgänge auf hoher Ebene und niedriger Ebene betreffen, finden Sie unter allgemeine [Konsolen](high-level-console-modes.md) Modi und [Low-Level-Konsolen Modi](low-level-console-modes.md).

Eine Befehlszeilen Anwendung sollte erwarten, dass andere Befehlszeilen Anwendungen den Konsolenmodus jederzeit ändern können und Sie möglicherweise nicht in der ursprünglichen Form wiederherstellt, bevor die Steuerung zurückgegeben wird. Außerdem wird empfohlen, dass alle Befehlszeilen Anwendungen den anfänglichen Konsolenmodus beim Start erfassen und versuchen, ihn beim Beenden wiederherzustellen, um eine minimale Auswirkung auf andere Befehlszeilen Anwendungen sicherzustellen, die an dieselbe Konsole angefügt sind.

Die [**getconsoledisplaymode**](getconsoledisplaymode.md) -Funktion meldet, ob sich die aktuelle Konsole im Vollbildmodus befindet.
