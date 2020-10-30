---
title: Scrollen im Fenster eines Bildschirmpuffers
description: Die setconsolewindowinfo-Funktion kann verwendet werden, um einen Bildlauf für den Inhalt eines Bildschirm Puffers im Konsolenfenster durchführen.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_window'
- base.scrolling\_a\_screen\_buffer\_s\_window
- consoles.scrolling\_a\_screen\_buffer\_s\_window
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bc300349-9bfa-4417-92ad-57a05a658ce5
ms.openlocfilehash: 332edf04a2f6f4ebaa9b482d2dc3f15381190855
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039428"
---
# <a name="scrolling-a-screen-buffers-window"></a>Scrollen im Fenster eines Bildschirmpuffers

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion kann verwendet werden, um einen Bildlauf für den Inhalt eines Bildschirm Puffers im Konsolenfenster durchführen. Diese Funktion kann auch die Fenstergröße ändern. Die-Funktion kann entweder die neuen oberen linken und unteren rechten Ecke des Fensters des Konsolenbildschirm Puffers als absolute Bildschirm Puffer Koordinaten angeben oder die Änderungen der aktuellen Fenster Koordinaten angeben. Die Funktion schlägt fehl, wenn sich die angegebenen Fenster Koordinaten außerhalb der Grenzen des Konsolenbildschirm Puffers befinden.

Im folgenden Beispiel wird die Ansicht des Konsolenbildschirm Puffers durch Ändern der Fenster Koordinaten, die von der [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion zurückgegeben werden, durchgeführt. Die- `ScrollByAbsoluteCoord` Funktion veranschaulicht, wie absolute Koordinaten angegeben werden, während die- `ScrollByRelativeCoord` Funktion veranschaulicht, wie relative Koordinaten angegeben werden.

```C
#include <windows.h>
#include <stdio.h>
#include <conio.h>

HANDLE hStdout;

int ScrollByAbsoluteCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo;
    SMALL_RECT srctWindow;

    // Get the current screen buffer size and window position.

    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError());
        return 0;
    }

    // Set srctWindow to the current window size and location.

    srctWindow = csbiInfo.srWindow;

    // Check whether the window is too close to the screen buffer top

    if ( srctWindow.Top >= iRows )
    {
        srctWindow.Top -= (SHORT)iRows;     // move top up
        srctWindow.Bottom -= (SHORT)iRows;  // move bottom up

        if (! SetConsoleWindowInfo(
                   hStdout,          // screen buffer handle
                   TRUE,             // absolute coordinates
                   &srctWindow))     // specifies new location
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError());
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int ScrollByRelativeCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo;
    SMALL_RECT srctWindow;

    // Get the current screen buffer window position.

    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError());
        return 0;
    }

    // Check whether the window is too close to the screen buffer top

    if (csbiInfo.srWindow.Top >= iRows)
    {
        srctWindow.Top =- (SHORT)iRows;     // move top up
        srctWindow.Bottom =- (SHORT)iRows;  // move bottom up
        srctWindow.Left = 0;         // no change
        srctWindow.Right = 0;        // no change

        if (! SetConsoleWindowInfo(
                   hStdout,          // screen buffer handle
                   FALSE,            // relative coordinates
                   &srctWindow))     // specifies new location
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError());
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int main( void )
{
    int i;

    printf("\nPrinting twenty lines, then scrolling up five lines.\n");
    printf("Press any key to scroll up ten lines; ");
    printf("then press another key to stop the demo.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    if(ScrollByAbsoluteCoord(5))
        _getch();
    else return 0;

    if(ScrollByRelativeCoord(10))
        _getch();
    else return 0;
}
```

## <a name="related-topics"></a>Verwandte Themen

[Scrollen im Inhalt eines Bildschirmpuffers](scrolling-a-screen-buffer-s-contents.md)

[Scrollen des Bildschirm Puffers](scrolling-the-screen-buffer.md)
