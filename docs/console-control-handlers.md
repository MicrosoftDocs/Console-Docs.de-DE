---
title: Konsolen-Bearbeitungssteuerelemente
description: Jeder Konsolen Prozess verfügt über eine eigene Liste von Steuerelement-Handlerfunktionen, die vom System aufgerufen werden, wenn der Prozess das Signal STRG + C, Strg + Pause oder STRG + schließen empfängt.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: 41a1326b5b27531bf74ac571d6881a0f67c2b073
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038428"
---
# <a name="console-control-handlers"></a><span data-ttu-id="2bbd8-104">Konsolen-Bearbeitungssteuerelemente</span><span class="sxs-lookup"><span data-stu-id="2bbd8-104">Console Control Handlers</span></span>

<span data-ttu-id="2bbd8-105">Jeder Konsolen Prozess verfügt über eine eigene Liste von Steuerelement-Handlerfunktionen, die vom System aufgerufen werden, wenn der Prozess das Signal [STRG + C](ctrl-c-and-ctrl-break-signals.md), [Strg + Pause](ctrl-c-and-ctrl-break-signals.md)oder [STRG + schließen](ctrl-close-signal.md) empfängt.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-105">Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal.</span></span> <span data-ttu-id="2bbd8-106">Anfänglich enthält die Liste der Steuerelement Handler für jeden Prozess nur eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-106">Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="2bbd8-107">Ein Konsolen Prozess kann zusätzliche [**Handlerroutine**](handlerroutine.md) -Funktionen hinzufügen oder entfernen, indem er die [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-107">A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function.</span></span> <span data-ttu-id="2bbd8-108">Diese Funktion hat keine Auswirkung auf die Listen von Steuerelement Handlern für andere Prozesse.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-108">This function does not affect the lists of control handlers for other processes.</span></span> <span data-ttu-id="2bbd8-109">Wenn ein Konsolen Prozess eines der Steuersignale empfängt, ruft er die Handlerfunktionen für eine zuletzt registrierte, erste Methode auf, bis einer der Handler " **true** " zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-109">When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE** .</span></span> <span data-ttu-id="2bbd8-110">Wenn keiner der Handler **true** zurückgibt, wird der Standard Handler aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-110">If none of the handlers returns **TRUE** , the default handler is called.</span></span>

<span data-ttu-id="2bbd8-111">Der *dwctrltype* -Parameter der Funktion identifiziert, welches Steuerungs Signal empfangen wurde, und der Rückgabewert gibt an, ob das Signal behandelt wurde.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-111">The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.</span></span>

<span data-ttu-id="2bbd8-112">Im Befehlszeilen Client-Prozess wird ein neuer Thread gestartet, um die Handlerroutinen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-112">A new thread is started inside the command-line client process to run the handler routines.</span></span> <span data-ttu-id="2bbd8-113">Weitere Informationen zu den Timeout Werten und Aktionen dieses Threads finden Sie in der [**Handlerroutine**](handlerroutine.md#remarks) -Funktions Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="2bbd8-113">More information on the timeout values and action of this thread can be found in the [**HandlerRoutine**](handlerroutine.md#remarks) function documentation.</span></span>

<span data-ttu-id="2bbd8-114">Ein Beispiel für eine steuerungshandlerfunktion finden Sie unter [Registrieren einer Steuerelement Handler-Funktion](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="2bbd8-114">For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>
