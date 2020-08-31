---
title: E/a-Konsole auf hoher Ebene
description: Die e/a-Funktionen auf hoher Ebene stellen eine einfache Möglichkeit dar, einen Datenstrom aus Konsolen Eingaben zu lesen oder einen Zeichendaten Strom in die Konsolenausgabe zu schreiben.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: 2209259f604bb8653bca6ab38ca763b63f65713f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059611"
---
# <a name="high-level-console-io"></a>E/a-Konsole auf hoher Ebene


Die e/a-Funktionen auf hoher Ebene stellen eine einfache Möglichkeit dar, einen Datenstrom aus Konsolen Eingaben zu lesen oder einen Zeichendaten Strom in die Konsolenausgabe zu schreiben. Ein allgemeiner Lesevorgang ruft Eingabezeichen aus dem Eingabepuffer einer Konsole ab und speichert Sie in einem angegebenen Puffer. Ein hoher Schreibvorgang erfordert Zeichen aus einem angegebenen Puffer und schreibt Sie in einen Bildschirm Puffer an der aktuellen Cursorposition, wobei der Cursor beim Schreiben jedes Zeichens vorwärts bewegt wird.

Die e/a-Vorgänge auf hoher Ebene bieten Ihnen die Wahl zwischen den Funktionen "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " sowie den Funktionen "read [**Console**](readconsole.md) " und " [**Write Console**](writeconsole.md) ". Sie sind mit Ausnahme zweier wichtiger Unterschiede identisch. Die Konsolenfunktionen unterstützen die Verwendung von Unicode-Zeichen oder den ANSI-Zeichensatz. Unicode wird von den Datei-e/a-Funktionen nicht unterstützt. Außerdem können die Datei-e/a-Funktionen für den Zugriff auf Dateien, Pipes und serielle Kommunikationsgeräte verwendet werden. die Konsolenfunktionen können nur mit Konsolen Handles verwendet werden. Dieser Unterschied ist wichtig, wenn eine Anwendung auf Standard Handles basiert, die möglicherweise umgeleitet wurden.

Wenn Sie einen der Funktionen auf hoher Ebene verwenden, kann eine Anwendung die Text-und Hintergrundfarben steuern, die zum Anzeigen von Zeichen verwendet werden, die anschließend in einen Bildschirm Puffer geschrieben werden. Eine Anwendung kann auch die Konsolen Modi verwenden, die sich auf die e/a-Konsole auf hoher Ebene auswirken, um die folgenden Eigenschaften zu aktivieren oder zu deaktivieren:

- Wiedergabe von Tastatureingaben in den aktiven Bildschirm Puffer
- Zeilen Eingabe, in der ein Lesevorgang erst zurückgegeben wird, wenn die EINGABETASTE gedrückt wird
- Automatische Verarbeitung von Tastatureingaben zur Handhabung von Wagen Rücklauf-, STRG + C-und anderen Eingabe Details
- Automatische Verarbeitung der Ausgabe zur Behandlung von Zeilenumbruch, Wagen Rücklauf, backspaces und anderen Ausgabe Details

Weitere Informationen finden Sie unter den folgenden Themen:

- [Konsolen Modi](console-modes.md)
- [Allgemeine Konsolen Modi](high-level-console-modes.md)
- [Eingabe-und Ausgabefunktionen auf hoher Ebene](high-level-console-input-and-output-functions.md)

 

 




