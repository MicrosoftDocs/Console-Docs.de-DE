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
# <a name="console-code-pages"></a>Konsolen-Codepages

Eine *Codepage* ist eine Zuordnung von 256-Zeichen Codes zu einzelnen Zeichen. Zu verschiedenen Codepages gehören verschiedene spezielle Zeichen, die normalerweise für eine Sprache oder eine Gruppe von Sprachen angepasst sind.

Jede Konsole ist mit zwei Codepages verknüpft: einer für die Eingabe und einer für die Ausgabe. Eine-Konsole verwendet die Eingabe Codepage, um Tastatureingaben in den entsprechenden Zeichen Wert zu übersetzen. Er verwendet seine Ausgabe Codepage, um die von den verschiedenen Ausgabefunktionen geschriebenen Zeichen Werte in die Bilder zu übersetzen, die im Konsolenfenster angezeigt werden. Eine Anwendung kann die Funktionen [**setconsolecp**](setconsolecp.md) und [**getconsolecp**](getconsolecp.md) verwenden, um die Eingabe Codeseiten einer Konsole festzulegen und abzurufen, sowie die Funktionen [**setconsoleoutputcp**](setconsoleoutputcp.md) und [**getconsoleoutputcp**](getconsoleoutputcp.md) zum Festlegen und Abrufen der Ausgabe Codepages.

Die Bezeichner der auf dem lokalen Computer verfügbaren Codepages werden in der Registrierung unter folgendem Schlüssel gespeichert: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Informationen zum Verwenden der Registrierungsfunktionen zum Ermitteln der verfügbaren Codepages finden Sie unter [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).

> [!TIP]
> Es wird empfohlen, dass alle neuen und aktualisierten Befehlszeilen Anwendungen Codepages vermeiden und **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** verwenden. UTF-16-formatierter Text kann an die *W* -Familie der Konsolen-APIs gesendet werden. UTF-8-formatierter Text kann an *eine* Reihe von Konsolen-APIs gesendet werden, nachdem sichergestellt wurde, dass die Codepage zuerst mit den Funktionen [**setconsolecp**](setconsolecp.md) und [**setconsoleoutputcp**](setconsoleoutputcp.md) auf **[65001 (CP_UTF8)](https://docs.microsoft.com/windows/win32/intl/code-page-identifiers)** festgelegt wird.
