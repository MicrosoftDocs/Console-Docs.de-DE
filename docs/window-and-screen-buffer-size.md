---
title: Fenster-und Bildschirm Puffergröße
description: Die Größe eines Bildschirm Puffers wird in Form eines Koordinaten Rasters auf der Grundlage von Zeichen Zellen ausgedrückt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_window\_and\_screen\_buffer\_size'
- base.window\_and\_screen\_buffer\_size
- consoles.window\_and\_screen\_buffer\_size
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55246039-31eb-41ca-ad8e-d314cb508644
ms.openlocfilehash: 86a8967eeff35a7a5416273e639ba8bbe5a31ef1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060514"
---
# <a name="window-and-screen-buffer-size"></a>Fenster-und Bildschirm Puffergröße


Die Größe eines Bildschirm Puffers wird in Form eines Koordinaten Rasters auf der Grundlage von Zeichen Zellen ausgedrückt. Die Breite ist die Anzahl der Zeichen Zellen in jeder Zeile, und die Höhe ist die Anzahl der Zeilen. Jedem Bildschirm Puffer ist ein Fenster zugeordnet, das die Größe und Position des rechteckigen Teils des Konsolenbildschirm Puffers bestimmt, der im Konsolenfenster angezeigt wird. Das Fenster des Bildschirm Puffers wird definiert, indem die Zeichen Zell Koordinaten der oberen linken und unteren rechten Zelle des Rechteck des Fensters angegeben werden.

Ein Bildschirm Puffer kann eine beliebige Größe aufweisen, die nur durch den verfügbaren Arbeitsspeicher beschränkt ist. Die Abmessungen des Fensters eines Bildschirm Puffers dürfen nicht die entsprechenden Abmessungen des Konsolenbildschirm Puffers oder des maximalen Fensters überschreiten, das auf dem Bildschirm auf der Grundlage der aktuellen Schriftart Größe (ausschließlich vom Benutzer gesteuert) angepasst werden kann.

Die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion gibt die folgenden Informationen zu einem Bildschirm Puffer und dessen Fenster zurück:

- Die aktuelle Größe des Konsolenbildschirm Puffers.
- Die aktuelle Position des Fensters.
- Die maximale Größe des Fensters bei Angabe der aktuellen Bildschirm Puffergröße, der aktuellen Schriftgröße und der Bildschirmgröße.

Die [**getlargestconsolewindowsize**](getlargestconsolewindowsize.md) -Funktion gibt die maximale Größe eines Konsolenfensters basierend auf der aktuellen Schriftart und Bildschirmgröße zurück. Diese Größe unterscheidet sich von der maximalen Fenstergröße, die von [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) zurückgegeben wird, da die Puffergröße des Konsolen Bildschirms ignoriert wird.

Verwenden Sie die Funktion [**setconsoleskreenbuffersize**](setconsolescreenbuffersize.md) , um die Größe des Bildschirm Puffers zu ändern. Diese Funktion schlägt fehl, wenn eine der beiden Dimensionen der angegebenen Größe kleiner als die entsprechende Dimension des Konsolenfensters ist.

Verwenden Sie die Funktion [**setconsolewindowinfo**](setconsolewindowinfo.md) , um die Größe oder Position des Fensters eines Bildschirm Puffers zu ändern. Diese Funktion schlägt fehl, wenn die angegebenen Fenster Eckkoordinaten die Begrenzungen des Konsolenbildschirm Puffers oder des Bildschirms überschreiten. Wenn Sie die Fenstergröße des aktiven Bildschirm Puffers ändern, ändert sich die Größe des Konsolenfensters, das auf dem Bildschirm angezeigt wird.

Ein Prozess kann den Eingabemodus der Konsole ändern, um Fenster Eingaben zu aktivieren, damit der Prozess Eingaben empfangen kann, wenn der Benutzer die Bildschirmgröße des Konsolen Bildschirms ändert. Wenn eine Anwendung eine Fenster Eingabe ermöglicht, kann Sie [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) zum Abrufen der Fenster-und Bildschirm Puffergröße beim Start verwenden. Diese Informationen können dann verwendet werden, um zu bestimmen, wie Daten im-Fenster angezeigt werden. Wenn der Benutzer die Größe des Bildschirm Puffers der Konsole ändert, kann die Anwendung reagieren, indem die Art und Weise der Anzeige von Daten geändert wird. Beispielsweise kann eine Anwendung die Art und Weise anpassen, in der Text am Ende der Zeile umbrochen wird, wenn sich die Anzahl der Zeichen pro Zeile ändert. Wenn eine Anwendung keine Fenster Eingabe aktiviert, muss Sie entweder die geerbten Fenster-und Bildschirm Puffergrößen verwenden oder Sie auf die gewünschte Größe während des Starts festlegen und die geerbten Größen beim Beenden wiederherstellen. Weitere Informationen zum Fenster Eingabemodus finden Sie unter [Konsolen Modi auf niedriger Ebene](low-level-console-modes.md).

 

 




