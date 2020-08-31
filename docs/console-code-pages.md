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
# <a name="console-code-pages"></a>Konsolen Codepages


Eine *Codepage* ist eine Zuordnung von 256-Zeichen Codes zu einzelnen Zeichen. Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.

Jede Konsole ist mit zwei Codepages verknüpft: einer für die Eingabe und einer für die Ausgabe. Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen. Er verwendet seine Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die Bilder zu übersetzen, die im Konsolenfenster angezeigt werden. Eine Anwendung kann die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) verwenden, um die Eingabe Codeseiten einer Konsole festzulegen und abzurufen, sowie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) zum Festlegen und Abrufen der Ausgabe Codepages.

Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden in der Registrierung unter dem folgenden Schlüssel gespeichert.

**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ Control \\ nls \\ Codepage**

Informationen zum Verwenden der Registrierungsfunktionen zum Ermitteln der verfügbaren Codepages finden Sie unter [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).

 

 




