---
title: Ein- und Ausgabemethoden
description: Es gibt zwei unterschiedliche Ansätze für Konsolen-e/a. die Wahl hängt von der Flexibilität und Steuerung der Anwendungsanforderungen ab.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: e1802d3fd503d377cac9b404353f94c717b44f20
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358290"
---
# <a name="input-and-output-methods"></a>Ein- und Ausgabemethoden

Es gibt zwei unterschiedliche Ansätze für Konsolen-e/a. die Wahl hängt von der Flexibilität und Steuerung der Anwendungsanforderungen ab. Der allgemeine Ansatz ermöglicht eine einfache Zeichen Strom-e/a, schränkt aber den Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole ein. Die Low-Level-Vorgehensweise erfordert, dass Entwickler mehr Code schreiben und eine größere Anzahl von Funktionen auswählen, aber auch eine höhere Flexibilität der Anwendung bietet.

> [!NOTE]
> Die Low-Level-Vorgehensweise wird für die Entwicklung neuer und fortlaufender Anwendungen nicht empfohlen. Anwendungen, die Funktionalität von den e/a-Funktionen der Low-Level-Konsole benötigen, werden empfohlen, **[virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md)** zu verwenden und unsere Dokumentation sowohl für klassische Funktionen als auch für das **[virtuelle Terminal](classic-vs-vt.md)** und **[die Ökosystem-Roadmap](ecosystem-roadmap.md)** zu erkunden

Eine Anwendung kann die Datei-e/a-Funktionen, "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) " und " [**Write File**](/windows/win32/api/fileapi/nf-fileapi-writefile)" und die Konsolenfunktionen " [**infoconsole**](readconsole.md) " und " [**Write-Console**](writeconsole.md)" für e/a-Vorgänge auf hoher Ebene verwenden, die indirekten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole bereitstellen. Die Eingabefunktionen auf hoher Ebene filtern und verarbeiten die Daten im Eingabepuffer einer Konsole, um die Eingabe als Zeichendaten Strom zurückzugeben, wobei die Eingabe von Maus-und Puffergröße verworfen wird. Entsprechend schreiben die Ausgabefunktionen auf hoher Ebene einen Datenstrom von Zeichen, die an der aktuellen Cursorposition in einem Bildschirm Puffer angezeigt werden. Eine Anwendung steuert die Funktionsweise dieser Funktionen, indem die e/a-Modi einer Konsole festgelegt werden.

Die e/a-Funktionen auf niedriger Ebene bieten direkten Zugriff auf die Eingabe-und Bildschirm Puffer einer Konsole, sodass eine Anwendung auf die Maus-und Puffergröße für Eingabeereignisse und erweiterte Informationen für Tastatur Ereignisse zugreifen kann. Mithilfe von Ausgabefunktionen auf niedriger Ebene kann eine Anwendung eine angegebene Anzahl von aufeinander folgenden Zeichen Zellen in einem Bildschirm Puffer lesen oder in rechteckige Blöcke von Zeichen Zellen an einer bestimmten Position in einem Bildschirm Puffer schreiben. Die Eingabemodi einer Konsole beeinflussen Eingaben auf niedriger Ebene, indem der Anwendung ermöglicht wird, zu bestimmen, ob Maus-und Puffer-resialisierungsereignisse im Eingabepuffer platziert werden. Die Ausgabe Modi einer Konsole haben keine Auswirkungen auf die Ausgabe auf niedriger Ebene.

Die e/a-Methoden auf hoher und niedriger Ebene schließen sich nicht gegenseitig aus, und eine Anwendung kann eine beliebige Kombination dieser Funktionen verwenden. In der Regel verwendet eine Anwendung jedoch nur einen Ansatz oder den anderen, und es wird empfohlen, sich auf ein bestimmtes Paradigma zu konzentrieren, um optimale Ergebnisse zu erzielen.

> [!TIP]
> Die ideale vorwärts gerichtete Anwendung konzentriert sich auf die Methoden auf hoher Ebene und erweitert die weiteren Anforderungen mit **[virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md)** über die e/a-Methoden auf hoher Ebene, wenn dies notwendig ist, um die Verwendung von e/a-Funktionen auf niedriger Ebene zu vermeiden.

In den folgenden Themen werden die Konsolen Modi und die e/a-Funktionen auf hoher und niedriger Ebene beschrieben.

- [Konsolenmodi](console-modes.md)
- [E/a-Konsole auf hoher Ebene](high-level-console-i-o.md)
- [Allgemeine Konsolen Modi](high-level-console-modes.md)
- [Eingabe-und Ausgabefunktionen auf hoher Ebene](high-level-console-input-and-output-functions.md)
- [Virtuelle Konsolenterminalsequenzen](console-virtual-terminal-sequences.md)
- [Klassische Funktionen im Vergleich zu virtuellen Terminal Sequenzen](classic-vs-vt.md)
- [Roadmap für das Ökosystem](ecosystem-roadmap.md)
- [E/a-Konsole auf niedriger Ebene](low-level-console-i-o.md)
- [Konsolen Modi auf niedriger Ebene](low-level-console-modes.md)
- [Konsolen Eingabefunktionen auf niedriger Ebene](low-level-console-input-functions.md)
- [Konsolenausgabe Funktionen auf niedriger Ebene](low-level-console-output-functions.md)