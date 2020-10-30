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
# <a name="scrolling-a-screen-buffers-window"></a><span data-ttu-id="f54e9-104">Scrollen im Fenster eines Bildschirmpuffers</span><span class="sxs-lookup"><span data-stu-id="f54e9-104">Scrolling a Screen Buffer's Window</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f54e9-105">Die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion kann verwendet werden, um einen Bildlauf für den Inhalt eines Bildschirm Puffers im Konsolenfenster durchführen.</span><span class="sxs-lookup"><span data-stu-id="f54e9-105">The [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function can be used to scroll the contents of a screen buffer in the console window.</span></span> <span data-ttu-id="f54e9-106">Diese Funktion kann auch die Fenstergröße ändern.</span><span class="sxs-lookup"><span data-stu-id="f54e9-106">This function can also change the window size.</span></span> <span data-ttu-id="f54e9-107">Die-Funktion kann entweder die neuen oberen linken und unteren rechten Ecke des Fensters des Konsolenbildschirm Puffers als absolute Bildschirm Puffer Koordinaten angeben oder die Änderungen der aktuellen Fenster Koordinaten angeben.</span><span class="sxs-lookup"><span data-stu-id="f54e9-107">The function can either specify the new upper left and lower right corners of the console screen buffer's window as absolute screen buffer coordinates or specify the changes from the current window coordinates.</span></span> <span data-ttu-id="f54e9-108">Die Funktion schlägt fehl, wenn sich die angegebenen Fenster Koordinaten außerhalb der Grenzen des Konsolenbildschirm Puffers befinden.</span><span class="sxs-lookup"><span data-stu-id="f54e9-108">The function fails if the specified window coordinates are outside the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="f54e9-109">Im folgenden Beispiel wird die Ansicht des Konsolenbildschirm Puffers durch Ändern der Fenster Koordinaten, die von der [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion zurückgegeben werden, durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="f54e9-109">The following example scrolls the view of the console screen buffer up by modifying the window coordinates returned by the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="f54e9-110">Die- `ScrollByAbsoluteCoord` Funktion veranschaulicht, wie absolute Koordinaten angegeben werden, während die- `ScrollByRelativeCoord` Funktion veranschaulicht, wie relative Koordinaten angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f54e9-110">The `ScrollByAbsoluteCoord` function demonstrates how to specify absolute coordinates, while the `ScrollByRelativeCoord` function demonstrates how to specify relative coordinates.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="f54e9-111">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f54e9-111">Related topics</span></span>

[<span data-ttu-id="f54e9-112">Scrollen im Inhalt eines Bildschirmpuffers</span><span class="sxs-lookup"><span data-stu-id="f54e9-112">Scrolling a Screen Buffer's Contents</span></span>](scrolling-a-screen-buffer-s-contents.md)

[<span data-ttu-id="f54e9-113">Scrollen des Bildschirm Puffers</span><span class="sxs-lookup"><span data-stu-id="f54e9-113">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
