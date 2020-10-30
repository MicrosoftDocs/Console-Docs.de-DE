---
title: Tastenkombination STRG + C und Strg + Pause
description: Die Tastenkombinationen STRG + C und STRG + Break werden von Konsolen Prozessen besonders behandelt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 12a4541d51cb18109caa6d1c15c25479c9e91a7a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039098"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="55d14-104">Tastenkombination STRG + C und Strg + Pause</span><span class="sxs-lookup"><span data-stu-id="55d14-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="55d14-105">Die <kbd>CTRL</kbd> + Tastenkombinationen STRG<kbd>C</kbd> und <kbd>STRG</kbd> + <kbd>BREAK</kbd> -Taste werden von Konsolen Prozessen besonders behandelt.</span><span class="sxs-lookup"><span data-stu-id="55d14-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="55d14-106">Wenn ein Konsolenfenster den Tastaturfokus besitzt, wird <kbd>STRG</kbd> + <kbd>C</kbd> oder <kbd>STRG</kbd>-Taste standardmäßig + <kbd>BREAK</kbd> als Signal (SIGINT oder sigbreak) und nicht als Tastatureingabe behandelt.</span><span class="sxs-lookup"><span data-stu-id="55d14-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="55d14-107">Standardmäßig werden diese Signale an alle Konsolen Prozesse übermittelt, die an die Konsole angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="55d14-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="55d14-108">(Getrennte Prozesse sind nicht betroffen.</span><span class="sxs-lookup"><span data-stu-id="55d14-108">(Detached processes are not affected.</span></span> <span data-ttu-id="55d14-109">Weitere Informationen finden Sie [**unter Erstellen einer-Konsole**](creation-of-a-console.md).) Das System erstellt in jedem Client Prozess einen neuen Thread, um das Ereignis zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="55d14-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="55d14-110">Der Thread löst eine Ausnahme aus, wenn der Prozess gedebuggt wird.</span><span class="sxs-lookup"><span data-stu-id="55d14-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="55d14-111">Der Debugger kann die Ausnahme verarbeiten oder mit der Ausnahme fortfahren, die nicht behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="55d14-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="55d14-112"><kbd>STRG</kbd> + <kbd>Break</kbd> wird immer als Signal behandelt, aber eine Anwendung kann das Standardverhalten von <kbd>STRG</kbd> + <kbd>C</kbd> auf zwei Arten ändern, die das Aufrufen der Handlerfunktionen verhindern:</span><span class="sxs-lookup"><span data-stu-id="55d14-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="55d14-113">Die [**setconsolemode**](setconsolemode.md) -Funktion kann den **Aktivierungs Modus für \_ verarbeitete \_ Eingaben** für den Eingabepuffer einer Konsole deaktivieren, sodass STRG + C als Tastatureingabe und nicht als Signal gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="55d14-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="55d14-114">Wenn [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) mit **null** -und **true** -Werten für die zugehörigen Parameter aufgerufen wird, ignoriert der aufrufende Prozess STRG + C-Signale.</span><span class="sxs-lookup"><span data-stu-id="55d14-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="55d14-115">Die normale STRG + C-Verarbeitung wird durch Aufrufen von **SetConsoleCtrlHandler** mit **null** -Werten und **false** -Werten wieder hergestellt.</span><span class="sxs-lookup"><span data-stu-id="55d14-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="55d14-116">Dieses Attribut, bei dem STRG + C-Signale ignoriert oder nicht ignoriert werden, wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="55d14-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="55d14-117">Weitere Informationen zur Verarbeitung dieser Signale, einschließlich Timeouts, finden Sie in der [**Handlerroutine**](handlerroutine.md) -Rückruf Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="55d14-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
