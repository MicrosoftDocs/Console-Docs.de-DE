---
title: Konsolenaliase
description: Beschreibt Konsolen Aliase und deren Verwendung zum Zuordnen von Quell Zeichenfolgen zu Ziel Zeichenfolgen.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: b31ae10faf2c8500b0100d1a4cbc126014bf8790
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037278"
---
# <a name="console-aliases"></a><span data-ttu-id="4d328-104">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="4d328-104">Console Aliases</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4d328-105">Konsolen Aliase werden zum Zuordnen von Quell Zeichenfolgen zu Ziel Zeichenfolgen verwendet.</span><span class="sxs-lookup"><span data-stu-id="4d328-105">Console aliases are used to map source strings to target strings.</span></span> <span data-ttu-id="4d328-106">Beispielsweise können Sie einen-Konsolen Alias definieren, der "Test" zu "CD \\ a \_ very \_ Long \_ path \\ Test" zuordnet.</span><span class="sxs-lookup"><span data-stu-id="4d328-106">For example, you can define a console alias that maps "test" to "cd \\a\_very\_long\_path\\test".</span></span> <span data-ttu-id="4d328-107">Wenn Sie "Test" in der Befehlszeile eingeben, erweitert das Konsolen Subsystem den Alias und führt den angegebenen CD-Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="4d328-107">When you type "test" at the command line, the console subsystem expands the alias and executes the specified cd command.</span></span>

<span data-ttu-id="4d328-108">Zum Definieren eines Konsolen Alias verwenden Sie [**Doskey.exe**](https://docs.microsoft.com/windows-server/administration/windows-commands/doskey) , um ein Makro zu erstellen, oder verwenden Sie die [**addconsolealias**](addconsolealias.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="4d328-108">To define a console alias, use [**Doskey.exe**](https://docs.microsoft.com/windows-server/administration/windows-commands/doskey) to create a macro, or use the [**AddConsoleAlias**](addconsolealias.md) function.</span></span> <span data-ttu-id="4d328-109">Im folgenden Beispiel wird `Doskey.exe` verwendet:</span><span class="sxs-lookup"><span data-stu-id="4d328-109">The following example uses `Doskey.exe`:</span></span>

<span data-ttu-id="4d328-110">**doskey-Test = \\ CD** <em>ein \_ sehr \_ langer \_ Pfadtest</em>**\\**</span><span class="sxs-lookup"><span data-stu-id="4d328-110">**doskey test=cd \\**<em>a\_very\_long\_path</em>**\\test**</span></span>

<span data-ttu-id="4d328-111">Der folgende [**addconsolealias**](addconsolealias.md) -Befehl erstellt denselben-Konsolen Alias:</span><span class="sxs-lookup"><span data-stu-id="4d328-111">The following call to [**AddConsoleAlias**](addconsolealias.md) creates the same console alias:</span></span>

``` C
AddConsoleAlias( TEXT("test"),
                 TEXT("cd \\<a_very_long_path>\\test"),
                 TEXT("cmd.exe"));
```

<span data-ttu-id="4d328-112">Verwenden Sie zum Hinzufügen von Parametern zu einem Konsolen Alias Makro mithilfe von `Doskey.exe` die Batch Parameter bis `$1` `$9` .</span><span class="sxs-lookup"><span data-stu-id="4d328-112">To add parameters to a console alias macro using `Doskey.exe`, use the batch parameters `$1` through `$9`.</span></span> <span data-ttu-id="4d328-113">Weitere Informationen zu den speziellen Codes, die in Doskey-Makro Definitionen verwendet werden können, finden Sie in der Befehlszeilen Hilfe für `Doskey.exe` oder [doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) auf TechNet.</span><span class="sxs-lookup"><span data-stu-id="4d328-113">For more information on the special codes that can be used in Doskey macro definitions, see the command-line help for `Doskey.exe` or [Doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) on TechNet.</span></span>

<span data-ttu-id="4d328-114">Alle Instanzen einer ausführbaren Datei, die im selben Konsolenfenster ausgeführt wird, nutzen alle definierten Konsolen Aliase gemeinsam.</span><span class="sxs-lookup"><span data-stu-id="4d328-114">All instances of an executable file running in the same console window share any defined console aliases.</span></span> <span data-ttu-id="4d328-115">Mehrere Instanzen derselben ausführbaren Datei, die in unterschiedlichen Konsolen Fenstern ausgeführt werden, haben keine Konsolen Aliase gemeinsam.</span><span class="sxs-lookup"><span data-stu-id="4d328-115">Multiple instances of the same executable file running in different console windows do not share console aliases.</span></span> <span data-ttu-id="4d328-116">Verschiedene ausführbare Dateien, die im selben Konsolenfenster ausgeführt werden, haben keine Konsolen Aliase gemeinsam.</span><span class="sxs-lookup"><span data-stu-id="4d328-116">Different executable files running in the same console window do not share console aliases.</span></span>

<span data-ttu-id="4d328-117">Verwenden Sie die [**getconsolealias**](getconsolealias.md) -Funktion, um die Ziel Zeichenfolge für eine angegebene Quell Zeichenfolge und eine ausführbare Datei abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4d328-117">To retrieve the target string for a specified source string and executable file, use the [**GetConsoleAlias**](getconsolealias.md) function.</span></span> <span data-ttu-id="4d328-118">Um alle Aliase für eine angegebene ausführbare Datei abzurufen, verwenden Sie die [**getconsolealiases**](getconsolealiases.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="4d328-118">To retrieve all aliases for a specified executable file, use the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span> <span data-ttu-id="4d328-119">Verwenden Sie die [**getconsolealiasexes**](getconsolealiasexes.md) -Funktion, um die Namen aller Aliase abzurufen, für die Konsolen Aliase definiert wurden.</span><span class="sxs-lookup"><span data-stu-id="4d328-119">To retrieve the names of all aliases for which console aliases have been defined, use the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>
