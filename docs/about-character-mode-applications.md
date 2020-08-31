---
title: Informationen zu-Konsolen
description: -Konsolen stellen auf hoher Ebene Unterstützung für Anwendungen im einfachen Zeichenmodus bereit, die mit dem Benutzer interagieren, indem Sie Funktionen verwenden, die aus der Standardeingabe lesen und in Standardausgabe oder Standardfehler schreiben.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060250"
---
# <a name="about-character-mode-applications"></a>Informationen zu Zeichenmodus-Anwendungen

Zeichenmodus (oder Befehlszeilen Anwendung) Anwendungen:

1. Optional Lesen von Daten aus der Standardeingabe (stdin)
2. "Work"
3. Optional Schreiben von Daten in Standardausgabe (stdout) oder Standardfehler (stderr)

Zeichenmodus-Anwendungen kommunizieren mit dem Endbenutzer über eine Konsolenanwendung (oder eine Terminalanwendung). Eine-Konsole konvertiert Benutzereingaben von Tastatur, Maus, Touchscreen, Stift usw. und sendet diese an die stdin einer Anwendung im Zeichenmodus. In einer-Konsole wird möglicherweise auch die Textausgabe einer Anwendung im Zeichenmodus auf dem Bildschirm des Benutzers angezeigt.

In Windows ist die Konsole integriert und bietet eine umfangreiche API, über die Zeichenmodus-Anwendungen mit dem Benutzer interagieren können.

- [Trö](consoles.md)
- [Eingabe-und Ausgabemethoden](input-and-output-methods.md)
- [Konsolen Codepages](console-code-pages.md)
- [Konsolen Steuerungs Handler](console-control-handlers.md)
- [Konsolen Aliase](console-aliases.md)
- [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md)
- [Konsolen Anwendungsprobleme](console-application-issues.md)

 

 




