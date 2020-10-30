---
title: Lesen von Eingabepufferereignissen
description: Die Funktion "Read ConsoleInput" kann verwendet werden, um direkt auf den Eingabepuffer einer Konsole zuzugreifen.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_reading\_input\_buffer\_events'
- base.reading\_input\_buffer\_events
- consoles.reading\_input\_buffer\_events
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 57570f3b-4a37-4789-bf6c-474fae60171d
ms.openlocfilehash: 3fc600251e7530e914a4c6e352d6ed098ca1195d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037628"
---
# <a name="reading-input-buffer-events"></a>Lesen von Eingabepufferereignissen

Die Funktion "read [**ConsoleInput**](readconsoleinput.md) " kann verwendet werden, um direkt auf den Eingabepuffer einer Konsole zuzugreifen. Wenn eine-Konsole erstellt wird, wird die Mauseingabe aktiviert, und die Fenster Eingabe ist deaktiviert. Um sicherzustellen, dass der Prozess alle Ereignis Typen empfängt, wird in diesem Beispiel die Funktion " [**setconsolemode**](setconsolemode.md) " verwendet, um Fenster-und Maus Eingaben zu aktivieren. Dann wechselt Sie in eine Schleife, die 100 Konsolen Eingabeereignisse liest und verarbeitet. Beispielsweise wird die Meldung "Tastaturereignis" angezeigt, wenn der Benutzer eine Taste drückt, und die Meldung "Maus Ereignis" wird angezeigt, wenn der Benutzer mit der Maus interagiert.

```C
#include <windows.h>
#include <stdio.h>

HANDLE hStdin;
DWORD fdwSaveOldMode;

VOID ErrorExit(LPSTR);
VOID KeyEventProc(KEY_EVENT_RECORD);
VOID MouseEventProc(MOUSE_EVENT_RECORD);
VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD);

int main(VOID)
{
    DWORD cNumRead, fdwMode, i;
    INPUT_RECORD irInBuf[128];
    int counter=0;

    // Get the standard input handle.

    hStdin = GetStdHandle(STD_INPUT_HANDLE);
    if (hStdin == INVALID_HANDLE_VALUE)
        ErrorExit("GetStdHandle");

    // Save the current input mode, to be restored on exit.

    if (! GetConsoleMode(hStdin, &fdwSaveOldMode) )
        ErrorExit("GetConsoleMode");

    // Enable the window and mouse input events.

    fdwMode = ENABLE_WINDOW_INPUT | ENABLE_MOUSE_INPUT;
    if (! SetConsoleMode(hStdin, fdwMode) )
        ErrorExit("SetConsoleMode");

    // Loop to read and handle the next 100 input events.

    while (counter++ <= 100)
    {
        // Wait for the events.

        if (! ReadConsoleInput(
                hStdin,      // input buffer handle
                irInBuf,     // buffer to read into
                128,         // size of read buffer
                &cNumRead) ) // number of records read
            ErrorExit("ReadConsoleInput");

        // Dispatch the events to the appropriate handler.

        for (i = 0; i < cNumRead; i++)
        {
            switch(irInBuf[i].EventType)
            {
                case KEY_EVENT: // keyboard input
                    KeyEventProc(irInBuf[i].Event.KeyEvent);
                    break;

                case MOUSE_EVENT: // mouse input
                    MouseEventProc(irInBuf[i].Event.MouseEvent);
                    break;

                case WINDOW_BUFFER_SIZE_EVENT: // scrn buf. resizing
                    ResizeEventProc( irInBuf[i].Event.WindowBufferSizeEvent );
                    break;

                case FOCUS_EVENT:  // disregard focus events

                case MENU_EVENT:   // disregard menu events
                    break;

                default:
                    ErrorExit("Unknown event type");
                    break;
            }
        }
    }

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);

    return 0;
}

VOID ErrorExit (LPSTR lpszMessage)
{
    fprintf(stderr, "%s\n", lpszMessage);

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);

    ExitProcess(0);
}

VOID KeyEventProc(KEY_EVENT_RECORD ker)
{
    printf("Key event: ");

    if(ker.bKeyDown)
        printf("key pressed\n");
    else printf("key released\n");
}

VOID MouseEventProc(MOUSE_EVENT_RECORD mer)
{
#ifndef MOUSE_HWHEELED
#define MOUSE_HWHEELED 0x0008
#endif
    printf("Mouse event: ");

    switch(mer.dwEventFlags)
    {
        case 0:

            if(mer.dwButtonState == FROM_LEFT_1ST_BUTTON_PRESSED)
            {
                printf("left button press \n");
            }
            else if(mer.dwButtonState == RIGHTMOST_BUTTON_PRESSED)
            {
                printf("right button press \n");
            }
            else
            {
                printf("button press\n");
            }
            break;
        case DOUBLE_CLICK:
            printf("double click\n");
            break;
        case MOUSE_HWHEELED:
            printf("horizontal mouse wheel\n");
            break;
        case MOUSE_MOVED:
            printf("mouse moved\n");
            break;
        case MOUSE_WHEELED:
            printf("vertical mouse wheel\n");
            break;
        default:
            printf("unknown\n");
            break;
    }
}

VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD wbsr)
{
    printf("Resize event\n");
    printf("Console screen buffer is %d columns by %d rows.\n", wbsr.dwSize.X, wbsr.dwSize.Y);
}
```
