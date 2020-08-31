---
title: Konsolen – Windows-Desktop
description: Eine-Konsole ist eine Anwendung, die e/a-Vorgänge für Befehlszeilen Anwendungen bereitstellt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059946"
---
# <a name="consoles"></a>Trö

Eine- *Konsole* (oder ein *Terminal*) ist eine Anwendung, die e/a-Vorgänge für Anwendungen im Zeichenmodus bereitstellt. Dieser prozessorunabhängige Mechanismus vereinfacht das Portieren vorhandener Zeichenmodusanwendungen oder das Erstellen neuer Zeichenmodus-Tools und-Anwendungen.

Eine-Konsole besteht aus einem Eingabepuffer und mindestens einem Bildschirm Puffer. Der *Eingabepuffer* enthält eine Warteschlange von Eingabedaten Sätzen, die jeweils Informationen über ein Eingabe Ereignis enthalten. Die Eingabe Warteschlange enthält immer Key-Press-und Key-Release-Ereignisse. Es kann auch Mausereignisse (Zeiger Bewegungen und Schaltflächen-Pressen und Releases) und Ereignisse enthalten, in denen sich Benutzeraktionen auf die Größe des aktiven Bildschirm Puffers auswirken. Ein *Bildschirm Puffer* ist ein zweidimensionales Array von Zeichen-und Farbdaten für die Ausgabe in einem Konsolenfenster. Eine beliebige Anzahl von Prozessen kann eine-Konsole gemeinsam verwenden.

- [Erstellung einer Konsole](creation-of-a-console.md)
- [Anfügen an eine Konsole](attaching-to-a-console.md)
- [Schließen einer Konsole](closing-a-console.md)
- [Konsolen Handles](console-handles.md)
- [Konsolen Eingabepuffer](console-input-buffer.md)
- [Konsolenbildschirm Puffer](console-screen-buffers.md)
- [Fenster-und Bildschirm Puffergröße](window-and-screen-buffer-size.md)
- [Konsolen Auswahl](console-selection.md)
- [Scrollen des Bildschirm Puffers](scrolling-the-screen-buffer.md)
