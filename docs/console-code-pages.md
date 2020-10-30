---
title: Konsolen-Codepages
description: Eine Codepage ist eine Zuordnung von 256-Zeichen Codes zu einzelnen Zeichen. Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: 931e882306c1aaff521b7b78c2b99cf1a5479da1
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039248"
---
# <a name="console-code-pages"></a><span data-ttu-id="01455-105">Konsolen-Codepages</span><span class="sxs-lookup"><span data-stu-id="01455-105">Console Code Pages</span></span>

<span data-ttu-id="01455-106">Eine *Codepage* ist eine Zuordnung von 256-Zeichen Codes zu einzelnen Zeichen.</span><span class="sxs-lookup"><span data-stu-id="01455-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="01455-107">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="01455-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="01455-108">Jede Konsole ist mit zwei Codepages verknüpft: einer für die Eingabe und einer für die Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="01455-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="01455-109">Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="01455-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="01455-110">Er verwendet seine Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die Bilder zu übersetzen, die im Konsolenfenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="01455-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="01455-111">Eine Anwendung kann die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) verwenden, um die Eingabe Codeseiten einer Konsole festzulegen und abzurufen, sowie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) zum Festlegen und Abrufen der Ausgabe Codepages.</span><span class="sxs-lookup"><span data-stu-id="01455-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="01455-112">Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden in der Registrierung unter folgendem Schlüssel gespeichert: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span><span class="sxs-lookup"><span data-stu-id="01455-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span></span>

<span data-ttu-id="01455-113">Informationen zum Verwenden der Registrierungsfunktionen zum Ermitteln der verfügbaren Codepages finden Sie unter [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span><span class="sxs-lookup"><span data-stu-id="01455-113">For information about using the registry functions to determine the available code pages, see [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span></span>

> [!TIP]
> <span data-ttu-id="01455-114">Es wird empfohlen, dass alle neuen und aktualisierten Befehlszeilen Anwendungen Codepages vermeiden und **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** verwenden.</span><span class="sxs-lookup"><span data-stu-id="01455-114">It is recommended for all new and updated command-line applications to avoid code pages and use **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span></span> <span data-ttu-id="01455-115">UTF-16-formatierter Text kann an die *W* -Familie der Konsolen-APIs gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="01455-115">UTF-16 formatted text can be sent to the *W* family of console APIs.</span></span> <span data-ttu-id="01455-116">UTF-8-formatierter Text kann an *eine* Reihe von Konsolen-APIs gesendet werden, nachdem sichergestellt wurde, dass die Codepage zuerst mit den Funktionen [**setconsolecp**](setconsolecp.md) und [**setconsoleoutputcp**](setconsoleoutputcp.md) auf **[65001 (CP_UTF8)](https://docs.microsoft.com/windows/win32/intl/code-page-identifiers)** festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="01455-116">UTF-8 formatted text can be sent to the *A* family of console APIs after ensuring the code page is first set to **[65001 (CP_UTF8)](https://docs.microsoft.com/windows/win32/intl/code-page-identifiers)** with the [**SetConsoleCP**](setconsolecp.md) and [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions.</span></span>
