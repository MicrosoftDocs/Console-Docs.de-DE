---
title: STRG+C- und STRG+UNTBR-Signale
description: Die Tastenkombinationen STRG+C und STRG+UNTBR werden von Konsolenprozessen besonders behandelt.
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
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420189"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="15a34-104">STRG+C- und STRG+UNTBR-Signale</span><span class="sxs-lookup"><span data-stu-id="15a34-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="15a34-105">Die Tastenkombinationen <kbd>STRG</kbd>+<kbd>C</kbd> und <kbd>STRG</kbd>+<kbd>UNTBR</kbd> werden von Konsolenprozessen besonders behandelt.</span><span class="sxs-lookup"><span data-stu-id="15a34-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="15a34-106">Wenn ein Konsolenfenster den Tastaturfokus besitzt, wird <kbd>STRG</kbd>+<kbd>C</kbd> oder <kbd>STRG</kbd>+<kbd>UNTBR</kbd> standardmäßig als Signal (SIGINT oder SIGBREAK) und nicht als Tastatureingabe behandelt.</span><span class="sxs-lookup"><span data-stu-id="15a34-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="15a34-107">Standardmäßig werden diese Signale an alle Konsolenprozesse übermittelt, die an die Konsole angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="15a34-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="15a34-108">(Getrennte Prozesse sind nicht betroffen.</span><span class="sxs-lookup"><span data-stu-id="15a34-108">(Detached processes are not affected.</span></span> <span data-ttu-id="15a34-109">Siehe [**Erstellung einer Konsole**](creation-of-a-console.md).) Das System erstellt in jedem Clientprozess einen neuen Thread, um das Ereignis zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="15a34-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="15a34-110">Der Thread löst eine Ausnahme aus, wenn der Prozess debuggt wird.</span><span class="sxs-lookup"><span data-stu-id="15a34-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="15a34-111">Der Debugger kann die Ausnahme verarbeiten oder fortfahren, ohne die Ausnahme zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="15a34-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="15a34-112"><kbd>STRG</kbd>+<kbd>UNTBR</kbd> wird immer als Signal behandelt, aber eine Anwendung kann das Standardverhalten für <kbd>STRG</kbd>+<kbd>C</kbd> auf zwei Arten ändern, mit denen verhindert wird, dass die Handlerfunktionen aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="15a34-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="15a34-113">Die [**SetConsoleMode**](setconsolemode.md)-Funktion kann den Eingabemodus **ENABLE\_PROCESSED\_INPUT** für den Eingabepuffer einer Konsole aktivieren, sodass STRG+C als Tastatureingabe anstatt als Signal gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="15a34-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="15a34-114">Wenn [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) mit **NULL**- und **TRUE**-Werten für seine Parameter aufgerufen wird, ignoriert der aufrufende Prozess STRG+C-Signale.</span><span class="sxs-lookup"><span data-stu-id="15a34-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="15a34-115">Die normale STRG+C-Verarbeitung wird durch Aufrufen von **SetConsoleCtrlHandler** mit **NULL**- und **FALSE**-Werten wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="15a34-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="15a34-116">Dieses Attribut, mit dem STRG+C-Signale ignoriert oder nicht ignoriert werden, wird von untergeordneten Prozessen geerbt, kann jedoch von jedem Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse davon betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="15a34-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="15a34-117">Weitere Informationen zur Verarbeitung dieser Signale, einschließlich Timeouts, finden Sie in der [**Handlerroutine**](handlerroutine.md)-Rückrufdokumentation.</span><span class="sxs-lookup"><span data-stu-id="15a34-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
