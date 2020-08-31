---
title: Konsolen Modi auf niedriger Ebene
description: Die Typen von Eingabe Ereignissen, die im Eingabepuffer einer Konsole gemeldet werden, hängen von den Maus-und Fenster Eingabemodi der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: 375b3b6eaef499324bdbde24ec973d91c50dda5b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060027"
---
# <a name="low-level-console-modes"></a><span data-ttu-id="3fc70-104">Konsolen Modi auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="3fc70-104">Low-Level Console Modes</span></span>


<span data-ttu-id="3fc70-105">Die Typen von Eingabe Ereignissen, die im Eingabepuffer einer Konsole gemeldet werden, hängen von den Maus-und Fenster Eingabemodi der Konsole ab.</span><span class="sxs-lookup"><span data-stu-id="3fc70-105">The types of input events reported in a console's input buffer depend on the console's mouse and window input modes.</span></span> <span data-ttu-id="3fc70-106">Der verarbeitete Eingabemodus der Konsole bestimmt, wie das System die Tastenkombination STRG + C behandelt.</span><span class="sxs-lookup"><span data-stu-id="3fc70-106">The console's processed input mode determines how the system handles the CTRL+C key combination.</span></span> <span data-ttu-id="3fc70-107">Um den Zustand der Eingabemodi einer Konsole festzulegen oder abzurufen, kann eine Anwendung ein Konsolen Eingabepuffer Handle in einem Aufrufen der Funktion [**setconsolemode**](setconsolemode.md) oder [**getconsolemode**](getconsolemode.md) angeben.</span><span class="sxs-lookup"><span data-stu-id="3fc70-107">To set or retrieve the state of a console's input modes, an application can specify a console input buffer handle in a call to the [**SetConsoleMode**](setconsolemode.md) or [**GetConsoleMode**](getconsolemode.md) function.</span></span> <span data-ttu-id="3fc70-108">Die folgenden Modi werden mit Konsolen Eingabe Handles verwendet.</span><span class="sxs-lookup"><span data-stu-id="3fc70-108">The following modes are used with console input handles.</span></span>


| <span data-ttu-id="3fc70-109">Mode</span><span class="sxs-lookup"><span data-stu-id="3fc70-109">Mode</span></span>                         | <span data-ttu-id="3fc70-110">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="3fc70-110">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3fc70-111">**\_Maus \_ Eingaben aktivieren**</span><span class="sxs-lookup"><span data-stu-id="3fc70-111">**ENABLE\_MOUSE\_INPUT**</span></span>     | <span data-ttu-id="3fc70-112">Steuert, ob Mausereignisse im Eingabepuffer gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="3fc70-112">Controls whether mouse events are reported in the input buffer.</span></span> <span data-ttu-id="3fc70-113">Die Mauseingabe ist standardmäßig aktiviert, und die Fenster Eingabe ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="3fc70-113">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="3fc70-114">Wenn Sie einen dieser Modi ändern, wirkt sich dies nur auf Eingaben aus, die nach dem Festlegen des Modus auftreten. ausstehende Maus-oder Fenster Ereignisse im Eingabepuffer werden nicht geleert.</span><span class="sxs-lookup"><span data-stu-id="3fc70-114">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="3fc70-115">Der Mauszeiger wird unabhängig vom Maus Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3fc70-115">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                                |
| <span data-ttu-id="3fc70-116">**\_Fenster \_ Eingabe aktivieren**</span><span class="sxs-lookup"><span data-stu-id="3fc70-116">**ENABLE\_WINDOW\_INPUT**</span></span>    | <span data-ttu-id="3fc70-117">Steuert, ob Puffer-resisierungsereignisse im Eingabepuffer gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="3fc70-117">Controls whether buffer-resizing events are reported in the input buffer.</span></span> <span data-ttu-id="3fc70-118">Die Mauseingabe ist standardmäßig aktiviert, und die Fenster Eingabe ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="3fc70-118">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="3fc70-119">Wenn Sie einen dieser Modi ändern, wirkt sich dies nur auf Eingaben aus, die nach dem Festlegen des Modus auftreten. ausstehende Maus-oder Fenster Ereignisse im Eingabepuffer werden nicht geleert.</span><span class="sxs-lookup"><span data-stu-id="3fc70-119">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="3fc70-120">Der Mauszeiger wird unabhängig vom Maus Modus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3fc70-120">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                      |
| <span data-ttu-id="3fc70-121">**\_verarbeitete \_ Eingaben aktivieren**</span><span class="sxs-lookup"><span data-stu-id="3fc70-121">**ENABLE\_PROCESSED\_INPUT**</span></span> | <span data-ttu-id="3fc70-122">Steuert die Verarbeitung von Eingaben für Anwendungen, die die e/a-Funktionen auf hoher Ebene verwenden.</span><span class="sxs-lookup"><span data-stu-id="3fc70-122">Controls the processing of input for applications using the high-level console I/O functions.</span></span> <span data-ttu-id="3fc70-123">Wenn der verarbeitete Eingabemodus jedoch aktiviert ist, wird die Tastenkombination STRG + C nicht im Eingabepuffer der Konsole angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3fc70-123">However, if processed input mode is enabled, the CTRL+C key combination is not reported in the console's input buffer.</span></span> <span data-ttu-id="3fc70-124">Stattdessen wird Sie an die entsprechende Handlerfunktion des Steuer Elements weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="3fc70-124">Instead, it is passed on to the appropriate control handler function.</span></span> <span data-ttu-id="3fc70-125">Weitere Informationen zu Steuerelement Handlern finden Sie unter [Konsolen Steuerungs Handler](console-control-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="3fc70-125">For more information about control handlers, see [Console Control Handlers](console-control-handlers.md).</span></span> |



<span data-ttu-id="3fc70-126">Die Ausgabe Modi eines Bildschirm Puffers wirken sich nicht auf das Verhalten der Ausgabefunktionen auf niedriger Ebene aus.</span><span class="sxs-lookup"><span data-stu-id="3fc70-126">The output modes of a screen buffer do not affect the behavior of the low-level output functions.</span></span>








