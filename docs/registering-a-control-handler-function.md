---
title: Registrieren einer Steuerelementhandler-Funktion
description: Dies ist ein Beispiel für die SetConsoleCtrlHandler-Funktion, die verwendet wird, um einen Steuerelement Handler zu installieren.
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: 4142f4f0871bd11a56085324195702ab47301227
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039448"
---
# <a name="registering-a-control-handler-function"></a>Registrieren einer Steuerelementhandler-Funktion

Dies ist ein Beispiel für die [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion, die verwendet wird, um einen Steuerelement Handler zu installieren.

Wenn ein STRG + C-Signal empfangen wird, gibt der Steuerelement Handler **true** zurück, was darauf hinweist, dass das Signal behandelt wurde. Dadurch wird verhindert, dass andere Kontroll Handler aufgerufen werden.

Wenn ein **STRG \_ - \_ Ereignis** Signal zum Schließen empfangen wird, gibt der Steuerelement Handler **true** zurück, und der Prozess wird beendet.

Wenn ein **STRG- \_ break- \_ Ereignis** , ein STRG-Abmelde **\_ \_ Ereignis** oder ein **STRG-Shutdown- \_ \_ Ereignis** Signal empfangen wird, gibt der Steuerelement Handler **false** zurück. Dies bewirkt, dass das Signal an die nächste Steuerelement Handler-Funktion weitergeleitet wird. Wenn keine anderen Steuerelement Handler registriert wurden oder keiner der registrierten Handler **true** zurückgibt, wird der Standard Handler verwendet, was dazu führt, dass der Prozess beendet wird.

```C
// CtrlHandler.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include "pch.h"

#include <windows.h>
#include <stdio.h>

BOOL WINAPI CtrlHandler(DWORD fdwCtrlType)
{
    switch (fdwCtrlType)
    {
        // Handle the CTRL-C signal.
    case CTRL_C_EVENT:
        printf("Ctrl-C event\n\n");
        Beep(750, 300);
        return TRUE;

        // CTRL-CLOSE: confirm that the user wants to exit.
    case CTRL_CLOSE_EVENT:
        Beep(600, 200);
        printf("Ctrl-Close event\n\n");
        return TRUE;

        // Pass other signals to the next handler.
    case CTRL_BREAK_EVENT:
        Beep(900, 200);
        printf("Ctrl-Break event\n\n");
        return FALSE;

    case CTRL_LOGOFF_EVENT:
        Beep(1000, 200);
        printf("Ctrl-Logoff event\n\n");
        return FALSE;

    case CTRL_SHUTDOWN_EVENT:
        Beep(750, 500);
        printf("Ctrl-Shutdown event\n\n");
        return FALSE;

    default:
        return FALSE;
    }
}

int main(void)
{
    if (SetConsoleCtrlHandler(CtrlHandler, TRUE))
    {
        printf("\nThe Control Handler is installed.\n");
        printf("\n -- Now try pressing Ctrl+C or Ctrl+Break, or");
        printf("\n    try logging off or closing the console...\n");
        printf("\n(...waiting in a loop for events...)\n\n");

        while (1) {}
    }
    else
    {
        printf("\nERROR: Could not set control handler");
        return 1;
    }
    return 0;
}
```
