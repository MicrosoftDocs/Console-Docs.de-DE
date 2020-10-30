---
title: Zeichenmodus-Anwendungen
description: Konsolen verwalten Eingabe und Ausgabe (e/a) für Anwendungen im Zeichenmodus (Anwendungen, die keine eigene grafische Benutzeroberfläche bereitstellen).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037348"
---
# <a name="character-mode-applications"></a>Zeichenmodus-Anwendungen

Konsolen verwalten Eingabe und Ausgabe (e/a) für Anwendungen im Zeichenmodus (Anwendungen, die keine eigene grafische Benutzeroberfläche bereitstellen).

Die Konsolenfunktionen ermöglichen unterschiedliche Zugriffsebenen auf eine Konsole. Die e/a-Funktionen auf hoher Ebene ermöglichen es einer Anwendung, aus der Standardeingabe zu lesen, um Tastatureingaben abzurufen, die im Eingabepuffer einer Konsole gespeichert sind. Mit den Funktionen kann eine Anwendung auch in eine Standardausgabe oder einen Standardfehler schreiben, um Text im Bildschirm Puffer der Konsole anzuzeigen. Die Funktionen auf hoher Ebene unterstützen auch die Umleitung von Standard Handles und die Steuerung der Konsolen Modi für verschiedene e/a-Funktionen. Die e/a-Funktionen auf niedriger Ebene ermöglichen es Anwendungen, ausführliche Eingaben zu Tastatur-und Mausereignissen zu empfangen, sowie Ereignisse, die Benutzerinteraktionen mit dem Konsolenfenster betreffen. Die Funktionen auf niedriger Ebene ermöglichen auch eine bessere Kontrolle der Ausgabe auf dem Bildschirm.

In dieser Übersicht wird die Unterstützung für Anwendungen im Zeichenmodus beschrieben.

- [Informationen zu Konsolen](about-character-mode-applications.md)
- [Verwenden der Konsole](using-the-console.md)
- [Konsolen Referenz](console-reference.md)
