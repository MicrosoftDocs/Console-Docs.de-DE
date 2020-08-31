---
title: Tastenkombination STRG + C und Strg + Pause
description: Die Tastenkombinationen STRG + C und STRG + Break werden von Konsolen Prozessen besonders behandelt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 95e28c9d390e9edb0be7dcac5aa4600224ab118c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059891"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="9ef7e-104">Tastenkombination STRG + C und Strg + Pause</span><span class="sxs-lookup"><span data-stu-id="9ef7e-104">CTRL+C and CTRL+BREAK Signals</span></span>


<span data-ttu-id="9ef7e-105">Die Tastenkombinationen STRG + C und STRG + Break werden von Konsolen Prozessen besonders behandelt.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-105">The CTRL+C and CTRL+BREAK key combinations receive special handling by console processes.</span></span> <span data-ttu-id="9ef7e-106">Wenn ein Konsolenfenster den Tastaturfokus besitzt, wird standardmäßig STRG + C oder STRG + UNTBR als Signal (SIGINT oder sigbreak) und nicht als Tastatureingabe behandelt.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-106">By default, when a console window has the keyboard focus, CTRL+C or CTRL+BREAK is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="9ef7e-107">Standardmäßig werden diese Signale an alle Konsolen Prozesse übermittelt, die an die Konsole angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="9ef7e-108">(Getrennte Prozesse sind nicht betroffen.) Das System erstellt in jedem Client Prozess einen neuen Thread, um das Ereignis zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-108">(Detached processes are not affected.) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="9ef7e-109">Der Thread löst eine Ausnahme aus, wenn der Prozess gedebuggt wird.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-109">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="9ef7e-110">Der Debugger kann die Ausnahme verarbeiten oder mit der Ausnahme fortfahren, die nicht behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-110">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="9ef7e-111">STRG + UNTBR wird immer als Signal behandelt, aber eine Anwendung kann das Standardverhalten von STRG + C auf zwei Arten ändern, mit denen verhindert wird, dass die Handlerfunktionen aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="9ef7e-111">CTRL+BREAK is always treated as a signal, but an application can change the default CTRL+C behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="9ef7e-112">Die [**setconsolemode**](setconsolemode.md) -Funktion kann den **Aktivierungs Modus für \_ verarbeitete \_ Eingaben** für den Eingabepuffer einer Konsole deaktivieren, sodass STRG + C als Tastatureingabe und nicht als Signal gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-112">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="9ef7e-113">Wenn [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) mit **null** -und **true** -Werten für die zugehörigen Parameter aufgerufen wird, ignoriert der aufrufende Prozess STRG + C-Signale.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-113">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="9ef7e-114">Die normale STRG + C-Verarbeitung wird durch Aufrufen von **SetConsoleCtrlHandler** mit **null** -Werten und **false** -Werten wieder hergestellt.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-114">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="9ef7e-115">Dieses Attribut, bei dem STRG + C-Signale ignoriert oder nicht ignoriert werden, wird von untergeordneten Prozessen geerbt, kann jedoch von einem beliebigen Prozess aktiviert oder deaktiviert werden, ohne dass vorhandene Prozesse beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="9ef7e-115">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

 

 




