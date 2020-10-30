---
title: Erstellung einer Konsole
description: Das System erstellt eine neue Konsole, wenn ein Konsolen Prozess gestartet wird. dabei handelt es sich um einen Zeichenmodus, dessen Einstiegspunkt die Hauptfunktion ist.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.openlocfilehash: 78a77044452fe2287a7cea0bfe5a6542eceef337
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038238"
---
# <a name="creation-of-a-console"></a>Erstellung einer Konsole

Das System erstellt eine neue Konsole, wenn ein *Konsolen Prozess* gestartet wird. dabei handelt es sich um einen Zeichenmodus, dessen Einstiegspunkt die **Haupt** Funktion ist. Das System erstellt beispielsweise eine neue Konsole, wenn der Befehlsprozessor gestartet wird `cmd.exe` . Wenn der Befehlsprozessor einen neuen Konsolen Prozess startet, kann der Benutzer angeben, ob das System eine neue Konsole für den neuen Prozess erstellt oder ob er die Konsole des Befehls Prozessors erbt.

Ein Prozess kann eine-Konsole mithilfe einer der folgenden Methoden erstellen:

- Eine grafische Benutzeroberfläche (GUI) oder ein Konsolen Prozess kann mithilfe [**der Funktion**](https://msdn.microsoft.com/library/windows/desktop/ms682425) "Funktion erstellen" und " **\_ neue \_ Konsole erstellen** " einen Konsolen Prozess mit einer neuen Konsole erstellen. (Standardmäßig erbt ein Konsolen Prozess seine übergeordnete Konsole, und es gibt keine Garantie dafür, dass der Prozess, für den er vorgesehen war, Eingaben empfängt.)
- Ein GUI-oder Konsolen Prozess, der zurzeit nicht an eine Konsole angefügt ist, kann die Funktion " [**Zuweisung**](allocconsole.md) " verwenden, um eine neue Konsole zu erstellen. (GUI-Prozesse werden nicht an eine Konsole angefügt, wenn Sie erstellt werden. Konsolen Prozesse werden nicht an eine Konsole angefügt, wenn [**Sie mithilfe von**](https://msdn.microsoft.com/library/windows/desktop/ms682425) "erstellter Prozess" mit einem getrennten **\_ Prozess** erstellt werden.)

In der Regel wird von einem Prozess mithilfe von " [**zuordcconsole**](allocconsole.md) " eine-Konsole erstellt, wenn ein Fehler bei der Interaktion mit dem Benutzer auftritt Beispielsweise kann ein GUI-Prozess eine-Konsole erstellen, wenn ein Fehler auftritt, der verhindert, dass die normale grafische Oberfläche verwendet wird, oder ein Konsolen Prozess, der normalerweise nicht mit dem Benutzer interagiert, kann eine-Konsole erstellen, um einen Fehler anzuzeigen.

Ein Prozess kann auch eine-Konsole erstellen, indem Sie das Flag **Create \_ New \_ Console** in einem Aufrufen von "Create- [**Process**](https://msdn.microsoft.com/library/windows/desktop/ms682425)" angeben. Diese Methode erstellt eine neue Konsole, die für den untergeordneten Prozess, jedoch nicht für den übergeordneten Prozess zugänglich ist. Getrennte Konsolen ermöglichen es, dass sowohl übergeordnete als auch untergeordnete Prozesse ohne Konflikt mit dem Benutzer interagieren können. Wenn dieses Flag nicht angegeben wird, wenn ein Konsolen Prozess erstellt wird, werden beide Prozesse an dieselbe Konsole angefügt, und es gibt keine Garantie dafür, dass der richtige Prozess die gewünschte Eingabe empfängt. Anwendungen können Verwirrung vermeiden, indem Sie untergeordnete Prozesse erstellen, die keine Handles des Eingabe Puffers erben, oder indem Sie jeweils nur einen untergeordneten Prozess zum Erben eines Eingabepuffer Handles aktivieren und gleichzeitig verhindern, dass der übergeordnete Prozess Konsolen Eingaben liest, bis das untergeordnete Element beendet ist.

Das Erstellen einer neuen Konsole führt zu einem neuen Konsolenfenster sowie zu separaten e/a-Bildschirm Puffern. Der Prozess, der der neuen Konsole zugeordnet ist, verwendet die [**getstdhandle**](getstdhandle.md) -Funktion, um die Handles der Eingabe-und Bildschirm Puffer der neuen Konsole zu erhalten. Diese Handles ermöglichen dem Prozess den Zugriff auf die Konsole.

Wenn ein Prozess " [**kreateprocess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)" verwendet, kann er eine [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) -Struktur angeben, deren Member die Merkmale der ersten neuen Konsole (sofern vorhanden) steuern, die für den untergeordneten Prozess erstellt wurde. Die im aufgerufene aufgerufene **STARTUPINFO** -Struktur **hat Auswirkungen auf** eine Konsole, die erstellt wird, wenn das Flag **Create \_ New \_ Console** angegeben wird. Er wirkt sich auch auf eine [**-Konsole aus**](allocconsole.md), die erstellt wird, wenn der untergeordnete Prozess anschließend "" " Die folgenden Konsolen Eigenschaften können angegeben werden:

- Größe des neuen Konsolenfensters in Zeichen Zellen
- Speicherort des neuen Konsolenfensters in Bildschirm Koordinaten
- Größe des Bildschirm Puffers der neuen Konsole in Zeichen Zellen
- Attribute für Text-und Hintergrundfarben des Bildschirm Puffers der neuen Konsole
- Anzeige Name für die Titelleiste des Fensters der neuen Konsole

Das System verwendet Standardwerte, wenn die [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) -Werte nicht angegeben werden. Ein untergeordneter Prozess kann die [**getstartupinfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) -Funktion verwenden, um die Werte in seiner **STARTUPINFO** -Struktur zu bestimmen.

Ein Prozess kann den Speicherort seines Konsolenfensters auf dem Bildschirm nicht ändern, aber die folgenden Konsolenfunktionen sind verfügbar, um die anderen Eigenschaften, die in der [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) -Struktur angegeben sind, festzulegen oder abzurufen.

| Funktion | BESCHREIBUNG |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Ruft die Fenstergröße, die Bildschirm Puffergröße und die Farb Attribute ab. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | Ändert die Größe des Konsolenfensters.  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Ändert die Größe des Bildschirm Puffers der Konsole. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Legt die Farb Attribute fest.  |
| [**SetConsoleTitle**](setconsoletitle.md)  | Legt den Titel des Konsolenfensters fest. |
| [**GetConsoleTitle**](getconsoletitle.md)  | Ruft den Titel des Konsolenfensters ab.  |

Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich selbst von einer geerbten Konsole oder von einer von " [**Zuweisung-Konsole**](allocconsole.md)" erstellten Konsole zu trennen.

Ein Prozess kann die [**attachconsole**](attachconsole.md) -Funktion verwenden, um sich an eine andere vorhandene Konsolen Sitzung anzufügen, nachdem [**freeconsole**](freeconsole.md) zum Trennen von der eigenen Sitzung verwendet wurde (oder wenn andernfalls keine angefügte Sitzung vorhanden ist).
