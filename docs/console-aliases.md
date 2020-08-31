---
title: Konsolen Aliase
description: Beschreibt Konsolen Aliase und deren Verwendung zum Zuordnen von Quell Zeichenfolgen zu Ziel Zeichenfolgen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: bce57b152262da06b1950eb3566ca8b67d0bb580
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060171"
---
# <a name="console-aliases"></a>Konsolen Aliase


Konsolen Aliase werden zum Zuordnen von Quell Zeichenfolgen zu Ziel Zeichenfolgen verwendet. Beispielsweise können Sie einen-Konsolen Alias definieren, der "Test" zu "CD \\ a \_ very \_ Long \_ path \\ Test" zuordnet. Wenn Sie "Test" in der Befehlszeile eingeben, erweitert das Konsolen Subsystem den Alias und führt den angegebenen CD-Befehl aus.

Zum Definieren eines Konsolen Alias verwenden Sie Doskey.exe, um ein Makro zu erstellen, oder verwenden Sie die [**addconsolealias**](addconsolealias.md) -Funktion. Im folgenden Beispiel wird Doskey.exe verwendet:

**doskey-Test = \\ CD** <em>ein \_ sehr \_ langer \_ Pfadtest</em>** \\ **

Der folgende [**addconsolealias**](addconsolealias.md) -Befehl erstellt denselben-Konsolen Alias:

``` syntax
AddConsoleAlias( TEXT("test"), 
                 TEXT("cd \\<a_very_long_path>\\test"), 
                 TEXT("cmd.exe"));
```

Verwenden Sie zum Hinzufügen von Parametern zu einem Konsolen Alias Makro mithilfe von Doskey.exe die Batch Parameter $1 bis $9. Weitere Informationen zu den speziellen Codes, die in Doskey-Makro Definitionen verwendet werden können, finden Sie in der Befehlszeilen Hilfe für Doskey.exe oder [doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) auf TechNet.

Alle Instanzen einer ausführbaren Datei, die im selben Konsolenfenster ausgeführt wird, nutzen alle definierten Konsolen Aliase gemeinsam. Mehrere Instanzen derselben ausführbaren Datei, die in unterschiedlichen Konsolen Fenstern ausgeführt werden, haben keine Konsolen Aliase gemeinsam. Verschiedene ausführbare Dateien, die im selben Konsolenfenster ausgeführt werden, haben keine Konsolen Aliase gemeinsam.

Verwenden Sie die [**getconsolealias**](getconsolealias.md) -Funktion, um die Ziel Zeichenfolge für eine angegebene Quell Zeichenfolge und eine ausführbare Datei abzurufen. Um alle Aliase für eine angegebene ausführbare Datei abzurufen, verwenden Sie die [**getconsolealiases**](getconsolealiases.md) -Funktion. Verwenden Sie die [**getconsolealiasexes**](getconsolealiasexes.md) -Funktion, um die Namen aller Aliase abzurufen, für die Konsolen Aliase definiert wurden.

 

 




