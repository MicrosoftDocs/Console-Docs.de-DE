---
title: Konsolen – Windows-Desktop
description: Eine-Konsole ist eine Anwendung, die e/a-Vorgänge für Befehlszeilen Anwendungen bereitstellt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039118"
---
# <a name="consoles"></a>Trö

Eine- *Konsole* ist eine Anwendung, die e/a-Dienste für Anwendungen im Zeichenmodus bereitstellt.

Eine-Konsole besteht aus einem Eingabepuffer und mindestens einem Bildschirm Puffer. Der *Eingabepuffer* enthält eine Warteschlange von Eingabedaten Sätzen, die jeweils Informationen über ein Eingabe Ereignis enthalten. Die Eingabe Warteschlange enthält immer Key-Press-und Key-Release-Ereignisse. Es kann auch Mausereignisse (Zeiger Bewegungen und Schaltflächen-Pressen und Releases) und Ereignisse enthalten, in denen sich Benutzeraktionen auf die Größe des aktiven Bildschirm Puffers auswirken. Ein *Bildschirm Puffer* ist ein zweidimensionales Array von Zeichen-und Farbdaten für die Ausgabe in einem Konsolenfenster. Eine beliebige Anzahl von Prozessen kann eine-Konsole gemeinsam verwenden.

> [!TIP]
>Eine breitere Idee von Konsolen und deren Beziehung zu Terminals und Befehlszeilen-Client Anwendungen finden Sie in der Roadmap für das **[Ökosystem](ecosystem-roadmap.md)** .

- [Erstellung einer Konsole](creation-of-a-console.md)
- [Anfügen an eine Konsole](attaching-to-a-console.md)
- [Schließen einer Konsole](closing-a-console.md)
- [Konsolenhandles](console-handles.md)
- [Konsoleneingabepuffer](console-input-buffer.md)
- [Konsolenbildschirmpuffer](console-screen-buffers.md)
- [Fenster-und Bildschirm Puffergröße](window-and-screen-buffer-size.md)
- [Konsolenauswahl](console-selection.md)
- [Scrollen des Bildschirm Puffers](scrolling-the-screen-buffer.md)
