---
title: Konsolen Modi High-Level
description: Das Verhalten der hauptkonsolen Funktionen ist von den Konsolen Eingabe-und Ausgabe Modi betroffen.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: 418983a788957578e97fee70624fd80c1b09bc04
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038642"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="cdce7-104">Konsolen Modi High-Level</span><span class="sxs-lookup"><span data-stu-id="cdce7-104">High-Level Console Modes</span></span>

<span data-ttu-id="cdce7-105">Das Verhalten der hauptkonsolen Funktionen ist von den Konsolen Eingabe-und Ausgabe Modi betroffen.</span><span class="sxs-lookup"><span data-stu-id="cdce7-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="cdce7-106">Alle folgenden Konsolen Eingabemodi werden bei der Erstellung einer-Konsole für den Eingabepuffer einer Konsole aktiviert:</span><span class="sxs-lookup"><span data-stu-id="cdce7-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="cdce7-107">Zeilen Eingabemodus</span><span class="sxs-lookup"><span data-stu-id="cdce7-107">Line input mode</span></span>
- <span data-ttu-id="cdce7-108">Verarbeiteter Eingabemodus</span><span class="sxs-lookup"><span data-stu-id="cdce7-108">Processed input mode</span></span>
- <span data-ttu-id="cdce7-109">Echo Eingabemodus</span><span class="sxs-lookup"><span data-stu-id="cdce7-109">Echo input mode</span></span>

<span data-ttu-id="cdce7-110">Beide der folgenden Konsolenausgabe Modi sind bei der Erstellung für einen Konsolenbildschirm Puffer aktiviert:</span><span class="sxs-lookup"><span data-stu-id="cdce7-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="cdce7-111">Verarbeiteter Ausgabemodus</span><span class="sxs-lookup"><span data-stu-id="cdce7-111">Processed output mode</span></span>
- <span data-ttu-id="cdce7-112">Umwickeln im EOL-Ausgabemodus</span><span class="sxs-lookup"><span data-stu-id="cdce7-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="cdce7-113">Alle drei Eingabemodi, zusammen mit dem verarbeiteten Ausgabemodus, sind so konzipiert, dass Sie zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="cdce7-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="cdce7-114">Es empfiehlt sich, alle diese Modi als Gruppe zu aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="cdce7-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="cdce7-115">Wenn alle aktiviert sind, wird die Anwendung als "gekochter" Modus bezeichnet, was bedeutet, dass der meiste Teil der Verarbeitung für die Anwendung verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="cdce7-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="cdce7-116">Wenn alle deaktiviert sind, befindet sich die Anwendung im RAW-Modus, was bedeutet, dass die Eingabe ungefiltert und jede Verarbeitung an die Anwendung übertragen wird.</span><span class="sxs-lookup"><span data-stu-id="cdce7-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="cdce7-117">Eine Anwendung kann die [**getconsolemode**](getconsolemode.md) -Funktion verwenden, um den aktuellen Modus des Eingabe Puffers oder Bildschirm Puffers einer Konsole zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="cdce7-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="cdce7-118">Sie können jeden dieser Modi aktivieren oder deaktivieren, indem Sie die folgenden Werte in der [**setconsolemode**](setconsolemode.md) -Funktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="cdce7-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="cdce7-119">Beachten Sie, dass sich das Festlegen des Ausgabemodus eines Bildschirm Puffers nicht auf den Ausgabemodus anderer Bildschirm Puffer auswirkt.</span><span class="sxs-lookup"><span data-stu-id="cdce7-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
