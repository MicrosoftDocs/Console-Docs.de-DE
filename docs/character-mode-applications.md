---
title: Zeichenmodus-Anwendungen
description: Konsolen verwalten Eingabe und Ausgabe (e/a) für Anwendungen im Zeichenmodus (Anwendungen, die keine eigene grafische Benutzeroberfläche bereitstellen).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037348"
---
# <a name="character-mode-applications"></a><span data-ttu-id="10539-104">Zeichenmodus-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="10539-104">Character Mode Applications</span></span>

<span data-ttu-id="10539-105">Konsolen verwalten Eingabe und Ausgabe (e/a) für Anwendungen im Zeichenmodus (Anwendungen, die keine eigene grafische Benutzeroberfläche bereitstellen).</span><span class="sxs-lookup"><span data-stu-id="10539-105">Consoles manage input and output (I/O) for character-mode applications (applications that do not provide their own graphical user interface).</span></span>

<span data-ttu-id="10539-106">Die Konsolenfunktionen ermöglichen unterschiedliche Zugriffsebenen auf eine Konsole.</span><span class="sxs-lookup"><span data-stu-id="10539-106">The console functions enable different levels of access to a console.</span></span> <span data-ttu-id="10539-107">Die e/a-Funktionen auf hoher Ebene ermöglichen es einer Anwendung, aus der Standardeingabe zu lesen, um Tastatureingaben abzurufen, die im Eingabepuffer einer Konsole gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="10539-107">The high-level console I/O functions enable an application to read from standard input to retrieve keyboard input stored in a console's input buffer.</span></span> <span data-ttu-id="10539-108">Mit den Funktionen kann eine Anwendung auch in eine Standardausgabe oder einen Standardfehler schreiben, um Text im Bildschirm Puffer der Konsole anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="10539-108">The functions also enable an application to write to standard output or standard error to display text in the console's screen buffer.</span></span> <span data-ttu-id="10539-109">Die Funktionen auf hoher Ebene unterstützen auch die Umleitung von Standard Handles und die Steuerung der Konsolen Modi für verschiedene e/a-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="10539-109">The high-level functions also support redirection of standard handles and control of console modes for different I/O functionality.</span></span> <span data-ttu-id="10539-110">Die e/a-Funktionen auf niedriger Ebene ermöglichen es Anwendungen, ausführliche Eingaben zu Tastatur-und Mausereignissen zu empfangen, sowie Ereignisse, die Benutzerinteraktionen mit dem Konsolenfenster betreffen.</span><span class="sxs-lookup"><span data-stu-id="10539-110">The low-level console I/O functions enable applications to receive detailed input about keyboard and mouse events, as well as events involving user interactions with the console window.</span></span> <span data-ttu-id="10539-111">Die Funktionen auf niedriger Ebene ermöglichen auch eine bessere Kontrolle der Ausgabe auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="10539-111">The low-level functions also enable greater control of output to the screen.</span></span>

<span data-ttu-id="10539-112">In dieser Übersicht wird die Unterstützung für Anwendungen im Zeichenmodus beschrieben.</span><span class="sxs-lookup"><span data-stu-id="10539-112">This overview describes support for character-mode applications.</span></span>

- [<span data-ttu-id="10539-113">Informationen zu Konsolen</span><span class="sxs-lookup"><span data-stu-id="10539-113">About Consoles</span></span>](about-character-mode-applications.md)
- [<span data-ttu-id="10539-114">Verwenden der Konsole</span><span class="sxs-lookup"><span data-stu-id="10539-114">Using the Console</span></span>](using-the-console.md)
- [<span data-ttu-id="10539-115">Konsolen Referenz</span><span class="sxs-lookup"><span data-stu-id="10539-115">Console Reference</span></span>](console-reference.md)
