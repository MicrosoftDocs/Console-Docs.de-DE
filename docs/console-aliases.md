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
# <a name="console-aliases"></a>Konsolenaliase

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Konsolen Aliase werden zum Zuordnen von Quell Zeichenfolgen zu Ziel Zeichenfolgen verwendet. Beispielsweise können Sie einen-Konsolen Alias definieren, der "Test" zu "CD \\ a \_ very \_ Long \_ path \\ Test" zuordnet. Wenn Sie "Test" in der Befehlszeile eingeben, erweitert das Konsolen Subsystem den Alias und führt den angegebenen CD-Befehl aus.

Zum Definieren eines Konsolen Alias verwenden Sie [**Doskey.exe**](https://docs.microsoft.com/windows-server/administration/windows-commands/doskey) , um ein Makro zu erstellen, oder verwenden Sie die [**addconsolealias**](addconsolealias.md) -Funktion. Im folgenden Beispiel wird `Doskey.exe` verwendet:

**doskey-Test = \\ CD** <em>ein \_ sehr \_ langer \_ Pfadtest</em>**\\**

Der folgende [**addconsolealias**](addconsolealias.md) -Befehl erstellt denselben-Konsolen Alias:

``` C
AddConsoleAlias( TEXT("test"),
                 TEXT("cd \\<a_very_long_path>\\test"),
                 TEXT("cmd.exe"));
```

Verwenden Sie zum Hinzufügen von Parametern zu einem Konsolen Alias Makro mithilfe von `Doskey.exe` die Batch Parameter bis `$1` `$9` . Weitere Informationen zu den speziellen Codes, die in Doskey-Makro Definitionen verwendet werden können, finden Sie in der Befehlszeilen Hilfe für `Doskey.exe` oder [doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) auf TechNet.

Alle Instanzen einer ausführbaren Datei, die im selben Konsolenfenster ausgeführt wird, nutzen alle definierten Konsolen Aliase gemeinsam. Mehrere Instanzen derselben ausführbaren Datei, die in unterschiedlichen Konsolen Fenstern ausgeführt werden, haben keine Konsolen Aliase gemeinsam. Verschiedene ausführbare Dateien, die im selben Konsolenfenster ausgeführt werden, haben keine Konsolen Aliase gemeinsam.

Verwenden Sie die [**getconsolealias**](getconsolealias.md) -Funktion, um die Ziel Zeichenfolge für eine angegebene Quell Zeichenfolge und eine ausführbare Datei abzurufen. Um alle Aliase für eine angegebene ausführbare Datei abzurufen, verwenden Sie die [**getconsolealiases**](getconsolealiases.md) -Funktion. Verwenden Sie die [**getconsolealiasexes**](getconsolealiasexes.md) -Funktion, um die Namen aller Aliase abzurufen, für die Konsolen Aliase definiert wurden.
