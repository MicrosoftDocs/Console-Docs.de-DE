---
title: Lesen und Schreiben von Zeichen-und Attribut Blöcken
description: Die Funktion "Read consoleoutput" kopiert einen rechteckigen Block von Zeichen-und Farb Attributdaten aus einem Konsolenbildschirm Puffer in einen Ziel Puffer.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_reading\_and\_writing\_blocks\_of\_characters\_and\_attributes'
- base.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
- consoles.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: eaa57723-f003-4e90-8156-be8c3b42b912
ms.openlocfilehash: 17c50e3cc0d519e087cdb8bb40e04db43cfea36f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039468"
---
# <a name="reading-and-writing-blocks-of-characters-and-attributes"></a><span data-ttu-id="c7803-104">Lesen und Schreiben von Zeichen-und Attribut Blöcken</span><span class="sxs-lookup"><span data-stu-id="c7803-104">Reading and Writing Blocks of Characters and Attributes</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c7803-105">Die Funktion "read [**consoleoutput**](readconsoleoutput.md) " kopiert einen rechteckigen Block von Zeichen-und Farb Attributdaten aus einem Konsolenbildschirm Puffer in einen Ziel Puffer.</span><span class="sxs-lookup"><span data-stu-id="c7803-105">The [**ReadConsoleOutput**](readconsoleoutput.md) function copies a rectangular block of character and color attribute data from a console screen buffer into a destination buffer.</span></span> <span data-ttu-id="c7803-106">Die-Funktion behandelt den Ziel Puffer als zweidimensionales Array von [**Char \_ Info**](char-info-str.md) -Strukturen.</span><span class="sxs-lookup"><span data-stu-id="c7803-106">The function treats the destination buffer as a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures.</span></span> <span data-ttu-id="c7803-107">Entsprechend kopiert die Funktion " [**Write-consoleoutput**](writeconsoleoutput.md) " einen rechteckigen Block von Zeichen-und Farb Attributdaten aus einem Quell Puffer in einen Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="c7803-107">Similarly, the [**WriteConsoleOutput**](writeconsoleoutput.md) function copies a rectangular block of character and color attribute data from a source buffer to a console screen buffer.</span></span> <span data-ttu-id="c7803-108">Weitere Informationen zum Lesen aus und Schreiben in rechteckige Blöcke von Bildschirm Puffer Zellen finden Sie unter [Eingabe-und Ausgabemethoden](input-and-output-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c7803-108">For more information about reading from or writing to rectangular blocks of screen buffer cells, see [Input and Output Methods](input-and-output-methods.md).</span></span>

<span data-ttu-id="c7803-109">Im folgenden Beispiel wird die Funktion " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " zum Erstellen eines neuen Bildschirm Puffers verwendet.</span><span class="sxs-lookup"><span data-stu-id="c7803-109">The following example uses the [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function to create a new screen buffer.</span></span> <span data-ttu-id="c7803-110">Nachdem die Funktion " [**setconsoleactiveskreenbuffer**](setconsoleactivescreenbuffer.md) " den aktiven Bildschirm Puffer erstellt hat, wird ein Block von Zeichen und Farb Attributen aus den beiden oberen Zeilen des stdout-Bildschirm Puffers in einen temporären Puffer kopiert.</span><span class="sxs-lookup"><span data-stu-id="c7803-110">After the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function makes this the active screen buffer, a block of characters and color attributes is copied from the top two rows of the STDOUT screen buffer into a temporary buffer.</span></span> <span data-ttu-id="c7803-111">Die Daten werden dann aus dem temporären Puffer in den neuen aktiven Bildschirm Puffer kopiert.</span><span class="sxs-lookup"><span data-stu-id="c7803-111">The data is then copied from the temporary buffer into the new active screen buffer.</span></span> <span data-ttu-id="c7803-112">Wenn die Anwendung die Verwendung des neuen Bildschirm Puffers abgeschlossen hat, ruft Sie **setconsoleactiveskreenbuffer** auf, um den ursprünglichen stdout-Bildschirm Puffer wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="c7803-112">When the application is finished using the new screen buffer, it calls **SetConsoleActiveScreenBuffer** to restore the original STDOUT screen buffer.</span></span>

```C
#include <windows.h>
#include <stdio.h>

int main(void)
{
    HANDLE hStdout, hNewScreenBuffer;
    SMALL_RECT srctReadRect;
    SMALL_RECT srctWriteRect;
    CHAR_INFO chiBuffer[160]; // [2][80];
    COORD coordBufSize;
    COORD coordBufCoord;
    BOOL fSuccess;

    // Get a handle to the STDOUT screen buffer to copy from and
    // create a new screen buffer to copy to.

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);
    hNewScreenBuffer = CreateConsoleScreenBuffer(
       GENERIC_READ |           // read/write access
       GENERIC_WRITE,
       FILE_SHARE_READ |
       FILE_SHARE_WRITE,        // shared
       NULL,                    // default security attributes
       CONSOLE_TEXTMODE_BUFFER, // must be TEXTMODE
       NULL);                   // reserved; must be NULL
    if (hStdout == INVALID_HANDLE_VALUE ||
            hNewScreenBuffer == INVALID_HANDLE_VALUE)
    {
        printf("CreateConsoleScreenBuffer failed - (%d)\n", GetLastError());
        return 1;
    }

    // Make the new screen buffer the active screen buffer.

    if (! SetConsoleActiveScreenBuffer(hNewScreenBuffer) )
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError());
        return 1;
    }

    // Set the source rectangle.

    srctReadRect.Top = 0;    // top left: row 0, col 0
    srctReadRect.Left = 0;
    srctReadRect.Bottom = 1; // bot. right: row 1, col 79
    srctReadRect.Right = 79;

    // The temporary buffer size is 2 rows x 80 columns.

    coordBufSize.Y = 2;
    coordBufSize.X = 80;

    // The top left destination cell of the temporary buffer is
    // row 0, col 0.

    coordBufCoord.X = 0;
    coordBufCoord.Y = 0;

    // Copy the block from the screen buffer to the temp. buffer.

    fSuccess = ReadConsoleOutput(
       hStdout,        // screen buffer to read from
       chiBuffer,      // buffer to copy into
       coordBufSize,   // col-row size of chiBuffer
       coordBufCoord,  // top left dest. cell in chiBuffer
       &srctReadRect); // screen buffer source rectangle
    if (! fSuccess)
    {
        printf("ReadConsoleOutput failed - (%d)\n", GetLastError());
        return 1;
    }

    // Set the destination rectangle.

    srctWriteRect.Top = 10;    // top lt: row 10, col 0
    srctWriteRect.Left = 0;
    srctWriteRect.Bottom = 11; // bot. rt: row 11, col 79
    srctWriteRect.Right = 79;

    // Copy from the temporary buffer to the new screen buffer.

    fSuccess = WriteConsoleOutput(
        hNewScreenBuffer, // screen buffer to write to
        chiBuffer,        // buffer to copy from
        coordBufSize,     // col-row size of chiBuffer
        coordBufCoord,    // top left src cell in chiBuffer
        &srctWriteRect);  // dest. screen buffer rectangle
    if (! fSuccess)
    {
        printf("WriteConsoleOutput failed - (%d)\n", GetLastError());
        return 1;
    }
    Sleep(5000);

    // Restore the original active screen buffer.

    if (! SetConsoleActiveScreenBuffer(hStdout))
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError());
        return 1;
    }

    return 0;
}
```
