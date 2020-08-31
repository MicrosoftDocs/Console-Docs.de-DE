---
title: Konsolen Prozessgruppen
description: Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion "Debugprozess" verwendet, kann er das \_ Flag "neue Prozessgruppe erstellen" angeben, \_ \_ damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 467959e651f7e0806742ca3920ca0d441d5543cc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060090"
---
# <a name="console-process-groups"></a>Konsolen Prozessgruppen


Wenn ein Prozess zum Erstellen eines neuen Konsolen Prozesses die Funktion " [**Debugprozess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) " verwendet, kann er das Flag " ** \_ neue \_ Prozess \_ Gruppe erstellen** " angeben, damit der neue Prozess der Stamm Prozess einer Konsolen Prozessgruppe wird. Die Prozessgruppe umfasst alle Prozesse, bei denen es sich um nachfolgende Elemente des Stamm Prozesses handelt.

Ein Prozess kann die [**generateconsolectrlevent**](generateconsolectrlevent.md) -Funktion verwenden, um das Signal STRG + C oder STRG + UNTBR an alle Prozesse in einer Konsolen Prozessgruppe zu senden. Das Signal wird nur von den Prozessen in der Gruppe empfangen, die an dieselbe Konsole wie der Prozess mit dem Namen **generateconsolectrlevent**angefügt sind.

 

 




