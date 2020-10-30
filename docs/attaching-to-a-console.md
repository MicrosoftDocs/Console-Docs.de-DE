---
title: Anfügen an eine Konsole
description: Ein Prozess kann die attachconsole-Funktion verwenden, um eine Verbindung mit einer-Konsole anzufügen. Ein Prozess kann an eine Konsole angefügt werden.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: 793cc83c0af1f8b0ae4be026f966a79dd034250e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037458"
---
# <a name="attaching-to-a-console"></a><span data-ttu-id="91ada-105">Anfügen an eine Konsole</span><span class="sxs-lookup"><span data-stu-id="91ada-105">Attaching to a Console</span></span>

<span data-ttu-id="91ada-106">Ein Prozess kann die [**attachconsole**](attachconsole.md) -Funktion verwenden, um eine Verbindung mit einer Konsole als Client anzufügen.</span><span class="sxs-lookup"><span data-stu-id="91ada-106">A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console as a client.</span></span> <span data-ttu-id="91ada-107">Ein Prozess kann an eine Konsole angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="91ada-107">A process can be attached to one console.</span></span>

<span data-ttu-id="91ada-108">An eine Konsole können viele Prozesse angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="91ada-108">A console can have many processes attached to it.</span></span> <span data-ttu-id="91ada-109">Rufen Sie die [**getconsoleprocesslist**](getconsoleprocesslist.md) -Funktion auf, um eine Liste der Prozesse abzurufen, die an eine Konsole angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="91ada-109">To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.</span></span>

<span data-ttu-id="91ada-110">Informationen zum Anfügen als Server finden Sie unter Informationen zu [**Pseudo Konsolen**](pseudoconsoles.md).</span><span class="sxs-lookup"><span data-stu-id="91ada-110">To attach as a server, see information about [**Pseudoconsoles**](pseudoconsoles.md).</span></span>
