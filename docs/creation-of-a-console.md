---
title: Erstellung einer Konsole
description: Das System erstellt eine neue Konsole, wenn ein Konsolenprozess gestartet wird. Dabei handelt es sich um einen Prozess im Zeichenmodus, dessen Einstiegspunkt die main-Funktion ist.
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
ms.localizationpriority: high
ms.openlocfilehash: bf7993874c4f7c7031dbbcc9ce53a0610157eb75
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357920"
---
# <a name="creation-of-a-console"></a>Erstellung einer Konsole

Das System erstellt eine neue Konsole, wenn ein *Konsolenprozess* gestartet wird. Dabei handelt es sich um einen Prozess im Zeichenmodus, dessen Einstiegspunkt die **main**-Funktion ist. Beispielsweise erstellt das System eine neue Konsole, wenn es den Befehlsprozessor `cmd.exe` startet. Wenn der Befehlsprozessor einen neuen Konsolenprozess startet, kann der Benutzer angeben, ob das System eine neue Konsole für den neuen Prozess erstellt oder ob es die Konsole des Befehlsprozessors erbt.

Ein Prozess kann eine Konsole mithilfe einer der folgenden Methoden erstellen:

- Ein Prozess mit grafischer Benutzeroberfläche (GUI) oder ein Konsolenprozess kann die Funktion [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) mit **CREATE\_NEW\_CONSOLE** verwenden, um einen Konsolenprozess mit einer neuen Konsole zu erstellen. (Standardmäßig erbt ein Konsolenprozess seine übergeordnete Konsole, und es lässt sich nicht sicherstellen, dass Eingaben von dem Prozess empfangen werden, für den sie bestimmt sind.)
- Ein GUI- oder Konsolenprozess, der aktuell keiner Konsole zugeordnet ist, kann die Funktion [**AllocConsole**](allocconsole.md) verwenden, um eine neue Konsole zu erstellen. (GUI-Prozesse werden bei der Erstellung keiner Konsole zugeordnet. Konsolenprozesse werden keiner Konsole zugeordnet, wenn sie mithilfe von [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) mit **DETACHED\_PROCESS** erstellt werden.)

Normalerweise verwendet ein Prozess [**AllocConsole**](allocconsole.md), um eine Konsole zu erstellen, wenn ein Fehler auftritt, der einen Benutzereingriff erfordert. Beispielsweise kann ein GUI-Prozess eine Konsole erstellen, wenn ein Fehler auftritt, der ihn daran hindert, seine normale grafische Oberfläche zu verwenden, oder ein Konsolenprozess, der normalerweise keine Benutzerinteraktion aufweist, kann eine Konsole erstellen, um einen Fehler anzuzeigen.

Ein Prozess kann darüber hinaus eine Konsole durch Festlegen des Flags **CREATE\_NEW\_CONSOLE** in einem Aufruf von [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) erstellen. Mit dieser Methode wird eine neue Konsole erstellt, die für den untergeordneten Prozess, aber nicht für den übergeordneten Prozess zugänglich ist. Separate Konsolen ermöglichen es übergeordneten und untergeordneten Prozessen, konfliktfrei mit dem Benutzer zu interagieren. Wenn dieses Flag beim Erstellen eines Prozesses nicht angegeben wird, werden beide Prozesse der gleichen Konsole zugeordnet, und es ist nicht sichergestellt, dass der richtige Prozess die für ihn bestimmten Eingaben empfängt. Anwendungen können Verwirrung verhindern, indem sie untergeordnete Prozesse erstellen, die keine Handles vom Eingabepuffer erben, oder indem sie es jeweils nur einem untergeordneten Prozess ermöglichen, einen Eingabepufferhandle zu erben, während sie zugleich den übergeordneten Prozess am Lesen der Konsoleneingaben hindern, bis der untergeordnete Prozess beendet wurde.

Das Erstellen einer neuen Konsole führt zur Erstellung eines neuen Konsolenfensters sowie separater E/A-Bildschirmpuffer. Der Prozess, der der neuen Konsole zugeordnet ist, verwendet die [**GetStdHandle**](getstdhandle.md)-Funktion, um die Handles der Eingabe- und Bildschirmpuffer der neuen Konsole abzurufen. Diese Handles ermöglichen es dem Prozess, auf die Konsole zuzugreifen.

Wenn ein Prozess [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) verwendet, kann er eine [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa)-Struktur angeben, deren Elemente die Eigenschaften der ersten neuen Konsole steuern (sofern vorhanden), die für den untergeordneten Prozess erstellt werden. Die im Aufruf von **CreateProcess** angegebene **STARTUPINFO**-Struktur wirkt sich auf eine erstellte Konsole aus, wenn das Flag **CREATE\_NEW\_CONSOLE** angegeben wird. Sie wirkt sich ebenfalls auf eine erstellte Konsole aus, wenn der untergeordnete Prozess anschließend [**AllocConsole**](allocconsole.md) verwendet. Die folgenden Konsolenmerkmale können angegeben werden:

- Größe des neuen Konsolenfensters in Zeichenzellen
- Position des neuen Konsolenfensters in Bildschirmkoordinaten
- Größe des Bildschirmpuffers der neuen Konsole in Zeichenzellen
- Attribute für Text- und Hintergrundfarbe des Bildschirmpuffers der neuen Konsole
- Anzeigename für die Titelleiste des neuen Konsolenfensters

Das System verwendet Standardwerte, wenn keine Werte für [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa) angegeben werden. Ein untergeordneter Prozess kann die Funktion [**GetStartupInfo**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getstartupinfow) verwenden, um die Werte in seiner **STARTUPINFO**-Struktur zu bestimmen.

Ein Prozess kann die Position seines Konsolenfensters auf dem Bildschirm nicht ändern, es stehen aber die folgenden Konsolenfunktionen zur Verfügung, um die anderen in der Struktur [**STARTUPINFO**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa) angegebenen Eigenschaften festzulegen oder abzurufen.

| Funktion | BESCHREIBUNG |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Ruft die Fenstergröße, die Größe des Bildschirmpuffers und die Farbattribute ab. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | Ändert die Größe des Konsolenfensters.  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Ändert die Größe des Bildschirmpuffers der Konsole. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Legt die Farbattribute fest.  |
| [**SetConsoleTitle**](setconsoletitle.md)  | Legt den Titel des Konsolenfensters fest. |
| [**GetConsoleTitle**](getconsoletitle.md)  | Ruft den Titel des Konsolenfensters ab.  |

Ein Prozess kann die Funktion [**FreeConsole**](freeconsole.md) verwenden, um sich von einer ererbten Konsole oder von einer mithilfe von [**AllocConsole**](allocconsole.md) erstellten Konsole zu trennen.

Ein Prozess kann die Funktion [**AttachConsole**](attachconsole.md) verwenden, um sich nach der Verwendung von [**FreeConsole**](freeconsole.md) zum Zweck der Trennung von seiner eigenen Sitzung (oder wenn keine weitere zugeordnete Sitzung vorhanden ist), einer anderen vorhandenen Konsolensitzung zuzuordnen.