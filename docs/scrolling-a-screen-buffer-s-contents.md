---
title: Bildlauf für den Inhalt eines Bildschirm Puffers
description: Die scrollconsoleskreenbuffer-Funktion verschiebt einen Zeichen Zellblock von einem Teil eines Bildschirm Puffers in einen anderen Teil desselben Bildschirm Puffers.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_contents'
- base.scrolling\_a\_screen\_buffer\_s\_contents
- consoles.scrolling\_a\_screen\_buffer\_s\_contents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 288c6a0f-fbaa-4eee-895e-a25884b7b70a
ms.openlocfilehash: a25e9ad7a27977e6dbfcf58de2cf7a250ffd6c4d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060354"
---
# <a name="scrolling-a-screen-buffers-contents"></a>Bildlauf für den Inhalt eines Bildschirm Puffers


Die [**scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md) -Funktion verschiebt einen Zeichen Zellblock von einem Teil eines Bildschirm Puffers in einen anderen Teil desselben Bildschirm Puffers. Die-Funktion gibt die oberen linken und unteren rechten Zellen des Quell Rechtecks an, das verschoben werden soll, und die Zielkoordinaten der neuen Position für die obere linke Zelle. Die Zeichen-und Farbdaten in den Quell Zellen werden an die neue Position verschoben, und alle Zellen, die durch den Verschiebe Vorgang leer gelassen werden, werden mit einem angegebenen Zeichen und einer angegebenen Farbe gefüllt. Wenn ein Clippingrechteck angegeben wird, bleiben die Zellen außerhalb des Felds unverändert.

[**Scrollconsoleskreenbuffer**](scrollconsolescreenbuffer.md) kann verwendet werden, um eine Zeile zu löschen, indem Koordinaten der ersten Zelle in der Zeile als Zielkoordinaten angegeben werden und ein scrollrechteck angegeben wird, das alle Zeilen unterhalb der Zeile enthält.

Das folgende Beispiel zeigt die Verwendung eines clippingrechtecks, in dem nur die untersten 15 Zeilen des Konsolenbildschirm Puffers durchlaufen werden. Bei den Zeilen im angegebenen Rechteck wird eine Zeile nach oben gescrollt, und die obere Zeile des Blocks wird verworfen. Der Inhalt des Konsolenbildschirm Puffers außerhalb des clippingrechtecks bleibt unverändert.

```C
#include <windows.h>
#include <stdio.h>

int main( void )
{
    HANDLE hStdout; 
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctScrollRect, srctClipRect; 
    CHAR_INFO chiFill; 
    COORD coordDest; 
    int i;

    printf("\nPrinting 20 lines for reference. ");
    printf("Notice that line 6 is discarded during scrolling.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);
 
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 

    if (hStdout == INVALID_HANDLE_VALUE) 
    {
        printf("GetStdHandle failed with %d\n", GetLastError()); 
        return 1;
    }
 
    // Get the screen buffer size. 
 
    if (!GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo failed %d\n", GetLastError()); 
        return 1;
    }
 
    // The scrolling rectangle is the bottom 15 rows of the 
    // screen buffer. 
 
    srctScrollRect.Top = csbiInfo.dwSize.Y - 16; 
    srctScrollRect.Bottom = csbiInfo.dwSize.Y - 1; 
    srctScrollRect.Left = 0; 
    srctScrollRect.Right = csbiInfo.dwSize.X - 1; 
 
    // The destination for the scroll rectangle is one row up. 
 
    coordDest.X = 0; 
    coordDest.Y = csbiInfo.dwSize.Y - 17; 
 
    // The clipping rectangle is the same as the scrolling rectangle. 
    // The destination row is left unchanged. 
 
    srctClipRect = srctScrollRect; 
 
    // Fill the bottom row with green blanks. 
 
    chiFill.Attributes = BACKGROUND_GREEN | FOREGROUND_RED; 
    chiFill.Char.AsciiChar = (char)' '; 
 
    // Scroll up one line. 
 
    if(!ScrollConsoleScreenBuffer(  
        hStdout,         // screen buffer handle 
        &srctScrollRect, // scrolling rectangle 
        &srctClipRect,   // clipping rectangle 
        coordDest,       // top left destination cell 
        &chiFill))       // fill character and color
    {
        printf("ScrollConsoleScreenBuffer failed %d\n", GetLastError()); 
        return 1;
    }
return 0;
}
```

## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Scrollen des Fensters eines Bildschirm Puffers](scrolling-a-screen-buffer-s-window.md)

[Scrollen des Bildschirm Puffers](scrolling-the-screen-buffer.md)

 

 




