---
title: High-Level Konsolen-e/a
description: Die e/a-Funktionen auf hoher Ebene stellen eine einfache Möglichkeit dar, einen Datenstrom aus Konsolen Eingaben zu lesen oder einen Zeichendaten Strom in die Konsolenausgabe zu schreiben.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: d240a261ea555e0bfa506c96c1aaea9d6a933697
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358693"
---
# <a name="high-level-console-io"></a>High-Level Konsolen-e/a

Die e/a-Funktionen auf hoher Ebene stellen eine einfache Möglichkeit dar, einen Datenstrom aus Konsolen Eingaben zu lesen oder einen Zeichendaten Strom in die Konsolenausgabe zu schreiben. Ein allgemeiner Lesevorgang ruft Eingabezeichen aus dem Eingabepuffer einer Konsole ab und speichert Sie in einem angegebenen Puffer. Ein hoher Schreibvorgang erfordert Zeichen aus einem angegebenen Puffer und schreibt Sie in einen Bildschirm Puffer an der aktuellen Cursorposition, wobei der Cursor beim Schreiben jedes Zeichens vorwärts bewegt wird.

Die e/a-Vorgänge auf hoher Ebene bieten Ihnen die Wahl zwischen den Funktionen "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) " und " [**Write File**](/windows/win32/api/fileapi/nf-fileapi-writefile) " sowie den Funktionen "read [**Console**](readconsole.md) " und " [**Write Console**](writeconsole.md) ". Sie sind mit Ausnahme zweier wichtiger Unterschiede identisch. Die Konsolenfunktionen unterstützen die Verwendung von Unicode-Zeichen oder den ANSI-Zeichensatz über die Varianten A und W der einzelnen Funktionen. die Datei-e/a-Funktionen unterstützen Unicode nicht, mit Ausnahme von UTF-8-Set mit der `CP_UTF8` -Konstante in den Funktionen **[setconsolecp](setconsolecp.md)** und **[setconsoleoutputcp](setconsoleoutputcp.md)** vor der Verwendung. Außerdem können die Datei-e/a-Funktionen für den Zugriff auf Dateien, Pipes und serielle Kommunikationsgeräte verwendet werden. die Konsolenfunktionen können nur mit Konsolen Handles verwendet werden. Dieser Unterschied ist wichtig, wenn eine Anwendung auf Standard Handles basiert, die möglicherweise umgeleitet wurden.

Wenn Sie einen der Funktionen auf hoher Ebene verwenden, kann eine Anwendung die Text-und Hintergrundfarben steuern, die zum Anzeigen von Zeichen verwendet werden, die anschließend in einen Bildschirm Puffer mit dem bevorzugten Mechanismus über **[virtuelle Terminal Sequenzen](console-virtual-terminal-sequences.md)** geschrieben werden. Eine Anwendung kann auch die Konsolen Modi verwenden, die sich auf die e/a-Konsole auf hoher Ebene auswirken, um die folgenden Eigenschaften zu aktivieren oder zu deaktivieren:

- Wiedergabe von Tastatureingaben in den aktiven Bildschirm Puffer
- Zeilen Eingabe, in der ein Lesevorgang erst zurückgegeben wird, wenn die EINGABETASTE gedrückt wird
- Automatische Verarbeitung von Tastatureingaben zur Handhabung von Wagen Rücklauf-, STRG + C-und anderen Eingabe Details
- Automatische Verarbeitung der Ausgabe zur Behandlung von Zeilenumbruch, Wagen Rücklauf, backspaces und anderen Ausgabe Details

Weitere Informationen finden Sie in den folgenden Themen:

- [Konsolenmodi](console-modes.md)
- [Allgemeine Konsolen Modi](high-level-console-modes.md)
- [Eingabe-und Ausgabefunktionen auf hoher Ebene](high-level-console-input-and-output-functions.md)
- [Klassische APIs im Vergleich zu virtuellen Terminal Sequenzen](classic-vs-vt.md)