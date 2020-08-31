---
title: Konsolenausgabe Funktionen auf niedriger Ebene
description: Die Konsolenausgabe Funktionen auf niedriger Ebene ermöglichen den direkten Zugriff auf die Zeichen Zellen eines Bildschirm Puffers.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_low\_level\_console\_output\_functions'
- base.low\_level\_console\_output\_functions
- consoles.low\_level\_console\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 94185428-e8c7-4926-93ec-867b8c97b4ca
ms.openlocfilehash: 16441e318e7c0eed2de1125a2f7613cb4a105d44
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059619"
---
# <a name="low-level-console-output-functions"></a>Konsolenausgabe Funktionen auf niedriger Ebene


Die Konsolenausgabe Funktionen auf niedriger Ebene ermöglichen den direkten Zugriff auf die Zeichen Zellen eines Bildschirm Puffers. Ein Satz von Funktionen liest oder schreibt in aufeinander folgende Zellen, beginnend an einer beliebigen Position im Konsolenbildschirm Puffer. Ein anderer Satz von Funktionen liest von oder schreibt in rechteckige Blöcke von Zellen.

Die folgenden Funktionen lesen oder schreiben in eine angegebene Anzahl von aufeinander folgenden Zeichen Zellen in einem Bildschirm Puffer, beginnend mit einer angegebenen Zelle.


| Funktion                                                           | Beschreibung                                                                                                             |
|--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| [**"Read consoleoutputcharacter"**](readconsoleoutputcharacter.md)   | Kopiert eine Zeichenfolge aus Unicode-oder ANSI-Zeichen aus einem Bildschirm Puffer.                                                     |
| [**Schreibconsoleoutputcharacter**](writeconsoleoutputcharacter.md) | Schreibt eine Zeichenfolge von Unicode-oder ANSI-Zeichen in einen Bildschirm Puffer.                                                       |
| [**"Read consoleoutputattribute"**](readconsoleoutputattribute.md)   | Kopiert eine Zeichenfolge von Text-und Hintergrund Farb Attributen aus einem Bildschirm Puffer.                                           |
| [**"Schreibconsoleoutputattribute"**](writeconsoleoutputattribute.md) | Schreibt eine Zeichenfolge von Text-und Hintergrund Farb Attributen in einen Bildschirm Puffer.                                             |
| [**Fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md)   | Schreibt ein einzelnes Unicode-oder ANSI-Zeichen in eine angegebene Anzahl von aufeinander folgenden Zellen in einem Bildschirm Puffer.                |
| [**Fillconsoleoutputattribute**](fillconsoleoutputattribute.md)   | Schreibt eine Kombination aus Text-und Hintergrund Farb Attributen in eine angegebene Anzahl von aufeinander folgenden Zellen in einem Bildschirm Puffer. |


Für alle diese Funktionen, wenn die letzte Zelle einer Zeile gefunden wird, umschließt das Lesen oder schreiben in die erste Zelle der nächsten Zeile. Wenn das Ende der letzten Zeile des Konsolenbildschirm Puffers gefunden wird, verwerfen die Schreibfunktionen alle ungeschriebenen Zeichen oder Attribute, und die Lesefunktionen melden die Anzahl der tatsächlich geschriebenen Zeichen oder Attribute.

Die folgenden Funktionen lesen oder schreiben in rechteckige Blöcke von Zeichen Zellen an einer bestimmten Position in einem Bildschirm Puffer.


| Funktion                                         | Beschreibung                                                                                                               |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| [**"Read consoleoutput"**](readconsoleoutput.md)   | Kopiert Zeichen-und Farbdaten aus einem angegebenen Block von Bildschirm Puffer Zellen in einen angegebenen Block in einem Ziel Puffer. |
| [**Schreibconsoleoutput**](writeconsoleoutput.md) | Schreibt Zeichen-und Farbdaten in einen angegebenen Block von Bildschirm Puffer Zellen aus einem angegebenen Block in einem Quell Puffer.        |



Diese Funktionen behandeln Bildschirm Puffer und Quell-oder Ziel Puffer als zweidimensionale Arrays von [**Char \_ Info**](char-info-str.md) -Strukturen (die Zeichen-und Farb Attributdaten für jede Zelle enthalten). Die-Funktionen geben die Breite und Höhe des Quell-oder Ziel Puffers in Zeichen Zellen an, und der Zeiger auf den Puffer wird als Zeiger auf die Ursprungs Zelle (0,0) des zweidimensionalen Arrays behandelt. Die-Funktionen verwenden eine [**kleine \_ Rect**](small-rect-str.md) -Struktur, um anzugeben, auf welche Rechtecks im Konsolenbildschirm Puffer zugegriffen werden soll, und die Koordinaten der oberen linken Zelle im Quell-oder Ziel Puffer bestimmen den Speicherort des entsprechenden Rechtecks in diesem Puffer.

Diese Funktionen schneiden das angegebene Bildschirm Puffer Rechteck automatisch an die Grenzen des Konsolenbildschirm Puffers an. Wenn das Rechteck z. b. untere rechte Koordinaten angibt, die (Spalte 100, Zeile 50) sind und der Konsolenbildschirm Puffer nur 80 Spalten breit ist, werden die Koordinaten abgeschnitten, sodass Sie sind (Spalte 79, Zeile 50). Entsprechend wird dieses angepasste Rechteck wieder abgeschnitten, damit es in die Grenzen des Quell-oder Ziel Puffers passt. Die Bildschirm Puffer Koordinaten des eigentlichen Rechtecks, aus dem gelesen oder geschrieben wurde, werden angegeben. Ein Beispiel, in dem diese Funktionen verwendet werden, finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).

Die Abbildung zeigt einen [**leseconsoleoutput**](readconsoleoutput.md) -Vorgang, bei dem das Clipping auftritt, wenn der Block aus dem Konsolenbildschirm Puffer gelesen wird, und wieder, wenn der Block in den Ziel Puffer kopiert wird. Die-Funktion meldet das tatsächliche Bildschirm Puffer Rechteck, aus dem Sie kopiert wurde.

![Bildschirm Puffer Fenster mit Ziel Puffer](images/cscon-03.png)








