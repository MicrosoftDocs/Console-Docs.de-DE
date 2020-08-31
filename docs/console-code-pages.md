---
title: Konsolen Codepages
description: Eine Codepage ist eine Zuordnung von 256-Zeichen Codes zu einzelnen Zeichen. Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: cacc4cb1d88a7d2aa01c35e0f0d94b44c393d28c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060146"
---
# <a name="console-code-pages"></a><span data-ttu-id="d1745-105">Konsolen Codepages</span><span class="sxs-lookup"><span data-stu-id="d1745-105">Console Code Pages</span></span>


<span data-ttu-id="d1745-106">Eine *Codepage* ist eine Zuordnung von 256-Zeichen Codes zu einzelnen Zeichen.</span><span class="sxs-lookup"><span data-stu-id="d1745-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="d1745-107">Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="d1745-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="d1745-108">Jede Konsole ist mit zwei Codepages verknüpft: einer für die Eingabe und einer für die Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="d1745-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="d1745-109">Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="d1745-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="d1745-110">Er verwendet seine Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die Bilder zu übersetzen, die im Konsolenfenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d1745-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="d1745-111">Eine Anwendung kann die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) verwenden, um die Eingabe Codeseiten einer Konsole festzulegen und abzurufen, sowie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) zum Festlegen und Abrufen der Ausgabe Codepages.</span><span class="sxs-lookup"><span data-stu-id="d1745-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="d1745-112">Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden in der Registrierung unter dem folgenden Schlüssel gespeichert.</span><span class="sxs-lookup"><span data-stu-id="d1745-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key.</span></span>

<span data-ttu-id="d1745-113">**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ Control \\ nls \\ Codepage**</span><span class="sxs-lookup"><span data-stu-id="d1745-113">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="d1745-114">Informationen zum Verwenden der Registrierungsfunktionen zum Ermitteln der verfügbaren Codepages finden Sie unter [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span><span class="sxs-lookup"><span data-stu-id="d1745-114">For information about using the registry functions to determine the available code pages, see [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span></span>

 

 




