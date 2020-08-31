---
title: Registrieren einer Steuerelement Handler-Funktion
description: Dies ist ein Beispiel für die SetConsoleCtrlHandler-Funktion, die verwendet wird, um einen Steuerelement Handler zu installieren.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: cda72574b13c8c8fa1644e78310c66598c7b9dcf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060346"
---
# <a name="registering-a-control-handler-function"></a><span data-ttu-id="a3da5-104">Registrieren einer Steuerelement Handler-Funktion</span><span class="sxs-lookup"><span data-stu-id="a3da5-104">Registering a Control Handler Function</span></span>


<span data-ttu-id="a3da5-105">Dies ist ein Beispiel für die [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion, die verwendet wird, um einen Steuerelement Handler zu installieren.</span><span class="sxs-lookup"><span data-stu-id="a3da5-105">This is an example of the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function that is used to install a control handler.</span></span>

<span data-ttu-id="a3da5-106">Wenn ein STRG + C-Signal empfangen wird, gibt der Steuerelement Handler **true**zurück, was darauf hinweist, dass das Signal behandelt wurde.</span><span class="sxs-lookup"><span data-stu-id="a3da5-106">When a CTRL+C signal is received, the control handler returns **TRUE**, indicating that it has handled the signal.</span></span> <span data-ttu-id="a3da5-107">Dadurch wird verhindert, dass andere Kontroll Handler aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="a3da5-107">Doing this prevents other control handlers from being called.</span></span>

<span data-ttu-id="a3da5-108">Wenn ein **STRG \_ - \_ Ereignis** Signal zum Schließen empfangen wird, gibt der Steuerelement Handler **true** zurück, und der Prozess wird beendet.</span><span class="sxs-lookup"><span data-stu-id="a3da5-108">When a **CTRL\_CLOSE\_EVENT** signal is received, the control handler returns **TRUE** and the process terminates.</span></span>

<span data-ttu-id="a3da5-109">Wenn ein **STRG- \_ break- \_ Ereignis**, ein STRG-Abmelde \*\* \_ \_ Ereignis\*\*oder ein **STRG-Shutdown- \_ \_ Ereignis** Signal empfangen wird, gibt der Steuerelement Handler **false**zurück.</span><span class="sxs-lookup"><span data-stu-id="a3da5-109">When a **CTRL\_BREAK\_EVENT**, **CTRL\_LOGOFF\_EVENT**, or **CTRL\_SHUTDOWN\_EVENT** signal is received, the control handler returns **FALSE**.</span></span> <span data-ttu-id="a3da5-110">Dies bewirkt, dass das Signal an die nächste Steuerelement Handler-Funktion weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="a3da5-110">Doing this causes the signal to be passed to the next control handler function.</span></span> <span data-ttu-id="a3da5-111">Wenn keine anderen Steuerelement Handler registriert wurden oder keiner der registrierten Handler **true**zurückgibt, wird der Standard Handler verwendet, was dazu führt, dass der Prozess beendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3da5-111">If no other control handlers have been registered or none of the registered handlers returns **TRUE**, the default handler will be used, resulting in the process being terminated.</span></span>

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

 

 




