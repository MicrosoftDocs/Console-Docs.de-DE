---
title: Sicherheit und Zugriffsrechte für die Konsolen Puffer
description: Das Windows-Sicherheitsmodell ermöglicht es Ihnen, den Zugriff auf Konsolen Eingabepuffer und Konsolenbildschirm Puffer zu steuern. Weitere Informationen zur Sicherheit finden Sie unter Zugriffs Steuerungsmodell.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060162"
---
# <a name="console-buffer-security-and-access-rights"></a>Sicherheit und Zugriffsrechte für die Konsolen Puffer


Das Windows-Sicherheitsmodell ermöglicht es Ihnen, den Zugriff auf Konsolen Eingabepuffer und Konsolenbildschirm Puffer zu steuern. Weitere Informationen zur Sicherheit finden Sie unter [Zugriffs Steuerungsmodell](https://msdn.microsoft.com/library/windows/desktop/aa374876).

Sie können eine [Sicherheits Beschreibung](https://msdn.microsoft.com/library/windows/desktop/aa379563) für die Konsolen Eingabe und die Bildschirm Puffer der Konsole angeben, wenn Sie [**die Funktion**](https://msdn.microsoft.com/library/windows/desktop/aa363858) "up" oder " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " aufrufen. Wenn Sie **null**angeben, erhält das Objekt eine Standard Sicherheits Beschreibung. Die ACLs in der Standard Sicherheits Beschreibung für einen Konsolen Puffer stammen aus dem primären Token oder dem Identitätswechsel Token des Erstellers.

Die von "", "", " [**", "**](https://msdn.microsoft.com/library/windows/desktop/aa363858)", " [**", "**](createconsolescreenbuffer.md)", "", " **" und " \_ ** [**getstdhandle**](getstdhandle.md) " zurückgegebenen Handles verfügen über die **allgemeinen \_ Lese** Zugriffsrechte und

Zu den gültigen Zugriffsrechten gehören die allgemeinen ** \_ Lese** -und **generischen \_ Schreib** [Zugriffsrechte](https://msdn.microsoft.com/library/windows/desktop/aa446632).


| Wert                            | Bedeutung                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| **Generisch \_ Read** (0x80000000l)  | Fordert Lesezugriff auf den Konsolenbildschirm Puffer an und ermöglicht dem Prozess das Lesen von Daten aus dem Puffer. |
| **Generisch \_ Write** (0x40000000l) | Fordert Schreibzugriff auf den Konsolenbildschirm Puffer an und ermöglicht dem Prozess das Schreiben von Daten in den Puffer. |










