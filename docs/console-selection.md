---
title: Konsolenauswahl
description: Eine Barrierefreiheits Anwendung benötigt Informationen zur Auswahl des Benutzers in der-Konsole.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_selection'
- base.console\_selection
- consoles.console\_selection
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f631e1b-d502-45b7-9c15-34c01e913738
ms.openlocfilehash: afc2d0a7615381b394df7f496aaf1b2a6002d04f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039158"
---
# <a name="console-selection"></a>Konsolenauswahl

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Eine Barrierefreiheits Anwendung benötigt Informationen zur Auswahl des Benutzers in der-Konsole. Rufen Sie die [**getconsoleselectioninfo**](getconsoleselectioninfo.md) -Funktion auf, um die aktuelle Konsolen Auswahl abzurufen. Die [**Konsolen \_ Auswahl \_ Info**](console-selection-info-str.md) -Struktur enthält Informationen zur Auswahl, z. b. den Anker, die Koordinaten und den Status.
