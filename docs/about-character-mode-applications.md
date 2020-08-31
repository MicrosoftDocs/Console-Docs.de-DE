---
title: Informationen zu-Konsolen
description: -Konsolen stellen auf hoher Ebene Unterstützung für Anwendungen im einfachen Zeichenmodus bereit, die mit dem Benutzer interagieren, indem Sie Funktionen verwenden, die aus der Standardeingabe lesen und in Standardausgabe oder Standardfehler schreiben.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060250"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="957f8-104">Informationen zu Zeichenmodus-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="957f8-104">About Character Mode Applications</span></span>

<span data-ttu-id="957f8-105">Zeichenmodus (oder Befehlszeilen Anwendung) Anwendungen:</span><span class="sxs-lookup"><span data-stu-id="957f8-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="957f8-106">Optional Lesen von Daten aus der Standardeingabe (stdin)</span><span class="sxs-lookup"><span data-stu-id="957f8-106">[Optionally] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="957f8-107">"Work"</span><span class="sxs-lookup"><span data-stu-id="957f8-107">Do "work"</span></span>
3. <span data-ttu-id="957f8-108">Optional Schreiben von Daten in Standardausgabe (stdout) oder Standardfehler (stderr)</span><span class="sxs-lookup"><span data-stu-id="957f8-108">[Optionally] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="957f8-109">Zeichenmodus-Anwendungen kommunizieren mit dem Endbenutzer über eine Konsolenanwendung (oder eine Terminalanwendung).</span><span class="sxs-lookup"><span data-stu-id="957f8-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="957f8-110">Eine-Konsole konvertiert Benutzereingaben von Tastatur, Maus, Touchscreen, Stift usw. und sendet diese an die stdin einer Anwendung im Zeichenmodus.</span><span class="sxs-lookup"><span data-stu-id="957f8-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="957f8-111">In einer-Konsole wird möglicherweise auch die Textausgabe einer Anwendung im Zeichenmodus auf dem Bildschirm des Benutzers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="957f8-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="957f8-112">In Windows ist die Konsole integriert und bietet eine umfangreiche API, über die Zeichenmodus-Anwendungen mit dem Benutzer interagieren können.</span><span class="sxs-lookup"><span data-stu-id="957f8-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span>

- [<span data-ttu-id="957f8-113">Trö</span><span class="sxs-lookup"><span data-stu-id="957f8-113">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="957f8-114">Eingabe-und Ausgabemethoden</span><span class="sxs-lookup"><span data-stu-id="957f8-114">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="957f8-115">Konsolen Codepages</span><span class="sxs-lookup"><span data-stu-id="957f8-115">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="957f8-116">Konsolen Steuerungs Handler</span><span class="sxs-lookup"><span data-stu-id="957f8-116">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="957f8-117">Konsolen Aliase</span><span class="sxs-lookup"><span data-stu-id="957f8-117">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="957f8-118">Sicherheit und Zugriffsrechte für die Konsolen Puffer</span><span class="sxs-lookup"><span data-stu-id="957f8-118">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="957f8-119">Konsolen Anwendungsprobleme</span><span class="sxs-lookup"><span data-stu-id="957f8-119">Console Application Issues</span></span>](console-application-issues.md)

 

 




