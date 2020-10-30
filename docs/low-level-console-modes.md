---
title: Konsolen Modi Low-Level
description: Die Typen von Eingabe Ereignissen, die im Eingabepuffer einer Konsole gemeldet werden, hängen von den Maus-und Fenster Eingabemodi der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: acd68e9679f209349f3e0db6989ca905815525a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039538"
---
# <a name="low-level-console-modes"></a>Konsolen Modi Low-Level

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Die Typen von Eingabe Ereignissen, die im Eingabepuffer einer Konsole gemeldet werden, hängen von den Maus-und Fenster Eingabemodi der Konsole ab. Der verarbeitete Eingabemodus der Konsole bestimmt, wie das System die Tastenkombination STRG + C behandelt. Um den Zustand der Eingabemodi einer Konsole festzulegen oder abzurufen, kann eine Anwendung ein Konsolen Eingabepuffer Handle in einem Aufrufen der Funktion [**setconsolemode**](setconsolemode.md) oder [**getconsolemode**](getconsolemode.md) angeben. Die folgenden Modi werden mit Konsolen Eingabe Handles verwendet.

| Mode | BESCHREIBUNG |
|-|-|
| **\_Maus \_ Eingaben aktivieren**     | Steuert, ob Mausereignisse im Eingabepuffer gemeldet werden. Die Mauseingabe ist standardmäßig aktiviert, und die Fenster Eingabe ist deaktiviert. Wenn Sie einen dieser Modi ändern, wirkt sich dies nur auf Eingaben aus, die nach dem Festlegen des Modus auftreten. ausstehende Maus-oder Fenster Ereignisse im Eingabepuffer werden nicht geleert. Der Mauszeiger wird unabhängig vom Maus Modus angezeigt.                                                |
| **\_Fenster \_ Eingabe aktivieren**    | Steuert, ob Puffer-resisierungsereignisse im Eingabepuffer gemeldet werden. Die Mauseingabe ist standardmäßig aktiviert, und die Fenster Eingabe ist deaktiviert. Wenn Sie einen dieser Modi ändern, wirkt sich dies nur auf Eingaben aus, die nach dem Festlegen des Modus auftreten. ausstehende Maus-oder Fenster Ereignisse im Eingabepuffer werden nicht geleert. Der Mauszeiger wird unabhängig vom Maus Modus angezeigt.                                      |
| **\_verarbeitete \_ Eingaben aktivieren** | Steuert die Verarbeitung von Eingaben für Anwendungen, die die e/a-Funktionen auf hoher Ebene verwenden. Wenn der verarbeitete Eingabemodus jedoch aktiviert ist, wird die Tastenkombination STRG + C nicht im Eingabepuffer der Konsole angezeigt. Stattdessen wird Sie an die entsprechende Handlerfunktion des Steuer Elements weitergegeben. Weitere Informationen zu Steuerelement Handlern finden Sie unter [Konsolen Steuerungs Handler](console-control-handlers.md). |

Die Ausgabe Modi eines Bildschirm Puffers wirken sich nicht auf das Verhalten der Ausgabefunktionen auf niedriger Ebene aus.
