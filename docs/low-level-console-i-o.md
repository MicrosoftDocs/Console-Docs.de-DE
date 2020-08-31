---
title: E/a-Konsole auf niedriger Ebene
description: Die e/a-Funktionen der Low-Level-Konsole erweitern die Kontrolle einer Anwendung über die Konsolen-e/a, indem Sie den direkten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole aktivieren.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b548a188189b597a270faac1cfbc83a2af699fab
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060403"
---
# <a name="low-level-console-io"></a>E/a-Konsole auf niedriger Ebene


Die e/a-Funktionen der Low-Level-Konsole erweitern die Kontrolle einer Anwendung über die Konsolen-e/a, indem Sie den direkten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole aktivieren. Diese Funktionen ermöglichen es einer Anwendung, folgende Aufgaben auszuführen:

- Empfangen von Eingaben über Maus-und Puffergröße-Ereignisse
- Erweiterte Informationen zu Tastatureingabe Ereignissen erhalten
- Eingabedaten Sätze in den Eingabepuffer schreiben
- Eingabedaten Sätze lesen, ohne Sie aus dem Eingabepuffer zu entfernen
- Bestimmen der Anzahl ausstehender Ereignisse im Eingabepuffer
- Leeren Sie den Eingabepuffer.
- Lesen und Schreiben von Zeichen folgen von Unicode-oder ANSI-Zeichen an einer bestimmten Position in einem Bildschirm Puffer
- Lese-und Schreibvorgänge für Zeichen folgen mit Text-und Hintergrundfarben Attributen an einem angegebenen Bildschirm Puffer Speicherort
- Rechteckige Blöcke von Zeichen-und Farbdaten an einem angegebenen Bildschirm Puffer Speicherort lesen und schreiben
- Schreiben eines einzelnen Unicode-oder ANSI-Zeichens oder einer Kombination aus Text-und Hintergrund Farb Attribut in eine angegebene Anzahl von aufeinander folgenden Zellen, beginnend an einem angegebenen Bildschirm Puffer Speicherort

Weitere Informationen finden Sie unter den folgenden Themen:

- [Konsolen Modi](console-modes.md)
- [Konsolen Modi auf niedriger Ebene](low-level-console-modes.md)
- [Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)
- [Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)

 

 




