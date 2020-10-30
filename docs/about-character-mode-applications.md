---
title: Informationen zu Konsolen
description: -Konsolen stellen auf hoher Ebene Unterstützung für Anwendungen im einfachen Zeichenmodus bereit, die mit dem Benutzer interagieren, indem Sie Funktionen verwenden, die aus der Standardeingabe lesen und in Standardausgabe oder Standardfehler schreiben.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037528"
---
# <a name="about-character-mode-applications"></a>Informationen zu Zeichenmodusanwendungen

Zeichenmodus (oder Befehlszeilen Anwendung) Anwendungen:

1. \[Optionales \] Lesen von Daten aus der Standardeingabe (stdin)
2. "Work"
3. \[Optionales \] Schreiben von Daten in Standardausgabe (stdout) oder Standardfehler (stderr)

Zeichenmodus-Anwendungen kommunizieren mit dem Endbenutzer über eine Konsolenanwendung (oder eine Terminalanwendung). Eine-Konsole konvertiert Benutzereingaben von Tastatur, Maus, Touchscreen, Stift usw. und sendet diese an die stdin einer Anwendung im Zeichenmodus. In einer-Konsole wird möglicherweise auch die Textausgabe einer Anwendung im Zeichenmodus auf dem Bildschirm des Benutzers angezeigt.

In Windows ist die Konsole integriert und bietet eine umfangreiche API, über die Zeichenmodus-Anwendungen mit dem Benutzer interagieren können. Allerdings ermutigt das Konsolen Team in der letzten Zeit, alle Zeichenmodus-Anwendungen mit [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) über die klassischen API-Aufrufe zu entwickeln, um die Kompatibilität zwischen Windows und anderen Betriebssystemen zu überschreiten. Weitere Informationen zu diesem Übergang und den beteiligten Kompromisse finden Sie in unserer Erörterung [klassischer APIs im Vergleich zu virtuellen Terminal Sequenzen](classic-vs-vt.md).

- [Trö](consoles.md)
- [Eingabe-und Ausgabemethoden](input-and-output-methods.md)
- [Konsolen-Codepages](console-code-pages.md)
- [Konsolen-Bearbeitungssteuerelemente](console-control-handlers.md)
- [Konsolenaliase](console-aliases.md)
- [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md)
- [Probleme mit der Konsolenanwendung](console-application-issues.md)
