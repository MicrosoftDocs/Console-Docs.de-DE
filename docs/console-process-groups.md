---
title: Konsolen Prozessgruppen
description: Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion "Debugprozess" verwendet, kann er das \_ Flag "neue Prozessgruppe erstellen" angeben, \_ \_ damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 26a1b0b9001f64ea2dc7465fa298b1383f30aa61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038448"
---
# <a name="console-process-groups"></a>Konsolen Prozessgruppen

Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion " [**Debugprozess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) " verwendet, kann er das Flag " **\_ neue \_ Prozess \_ Gruppe erstellen** " angeben, damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird. Die Prozessgruppe umfasst alle Prozesse, bei denen es sich um nachfolgende Elemente des Stamm Prozesses handelt.

Ein Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um das Signal STRG + C oder STRG + UNTBR an alle Prozesse in einer Konsolen Prozessgruppe zu senden. Das Signal wird nur von den Prozessen in der Gruppe empfangen, die an dieselbe Konsole wie der Prozess mit dem Namen **generateconsolectrlevent** angefügt sind.
