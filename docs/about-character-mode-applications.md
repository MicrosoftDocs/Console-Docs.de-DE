---
title: Informationen zu Konsolen
description: -Konsolen stellen auf hoher Ebene Unterstützung für Anwendungen im einfachen Zeichenmodus bereit, die mit dem Benutzer interagieren, indem Sie Funktionen verwenden, die aus der Standardeingabe lesen und in Standardausgabe oder Standardfehler schreiben.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037528"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="ca06b-104">Informationen zu Zeichenmodusanwendungen</span><span class="sxs-lookup"><span data-stu-id="ca06b-104">About Character Mode Applications</span></span>

<span data-ttu-id="ca06b-105">Zeichenmodus (oder Befehlszeilen Anwendung) Anwendungen:</span><span class="sxs-lookup"><span data-stu-id="ca06b-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="ca06b-106">\[Optionales \] Lesen von Daten aus der Standardeingabe (stdin)</span><span class="sxs-lookup"><span data-stu-id="ca06b-106">\[Optionally\] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="ca06b-107">"Work"</span><span class="sxs-lookup"><span data-stu-id="ca06b-107">Do "work"</span></span>
3. <span data-ttu-id="ca06b-108">\[Optionales \] Schreiben von Daten in Standardausgabe (stdout) oder Standardfehler (stderr)</span><span class="sxs-lookup"><span data-stu-id="ca06b-108">\[Optionally\] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="ca06b-109">Zeichenmodus-Anwendungen kommunizieren mit dem Endbenutzer über eine Konsolenanwendung (oder eine Terminalanwendung).</span><span class="sxs-lookup"><span data-stu-id="ca06b-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="ca06b-110">Eine-Konsole konvertiert Benutzereingaben von Tastatur, Maus, Touchscreen, Stift usw. und sendet diese an die stdin einer Anwendung im Zeichenmodus.</span><span class="sxs-lookup"><span data-stu-id="ca06b-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="ca06b-111">In einer-Konsole wird möglicherweise auch die Textausgabe einer Anwendung im Zeichenmodus auf dem Bildschirm des Benutzers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ca06b-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="ca06b-112">In Windows ist die Konsole integriert und bietet eine umfangreiche API, über die Zeichenmodus-Anwendungen mit dem Benutzer interagieren können.</span><span class="sxs-lookup"><span data-stu-id="ca06b-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span> <span data-ttu-id="ca06b-113">Allerdings ermutigt das Konsolen Team in der letzten Zeit, alle Zeichenmodus-Anwendungen mit [virtuellen Terminal Sequenzen](console-virtual-terminal-sequences.md) über die klassischen API-Aufrufe zu entwickeln, um die Kompatibilität zwischen Windows und anderen Betriebssystemen zu überschreiten.</span><span class="sxs-lookup"><span data-stu-id="ca06b-113">However, in the recent era, the console team is encouraging all character mode applications to be developed with [virtual terminal sequences](console-virtual-terminal-sequences.md) over the classic API calls for maximum compatibility between Windows and other operating systems.</span></span> <span data-ttu-id="ca06b-114">Weitere Informationen zu diesem Übergang und den beteiligten Kompromisse finden Sie in unserer Erörterung [klassischer APIs im Vergleich zu virtuellen Terminal Sequenzen](classic-vs-vt.md).</span><span class="sxs-lookup"><span data-stu-id="ca06b-114">More details on this transition and the trade offs involved can be found in our discussion of [classic APIs versus virtual terminal sequences](classic-vs-vt.md).</span></span>

- [<span data-ttu-id="ca06b-115">Trö</span><span class="sxs-lookup"><span data-stu-id="ca06b-115">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="ca06b-116">Eingabe-und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="ca06b-116">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="ca06b-117">Konsolen-Codepages</span><span class="sxs-lookup"><span data-stu-id="ca06b-117">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="ca06b-118">Konsolen-Bearbeitungssteuerelemente</span><span class="sxs-lookup"><span data-stu-id="ca06b-118">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="ca06b-119">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="ca06b-119">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="ca06b-120">Sicherheit und Zugriffsrechte für Konsolenpuffer</span><span class="sxs-lookup"><span data-stu-id="ca06b-120">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="ca06b-121">Probleme mit der Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="ca06b-121">Console Application Issues</span></span>](console-application-issues.md)
