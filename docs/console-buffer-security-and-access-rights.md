---
title: Sicherheit und Zugriffsrechte für Konsolenpuffer
description: Das Windows-Sicherheitsmodell ermöglicht es Ihnen, den Zugriff auf Konsolen Eingabepuffer und Konsolenbildschirm Puffer zu steuern. Weitere Informationen zur Sicherheit finden Sie unter Access-Control Modell.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: dfafdbd59c2b06929c35612d7dcf03b24439eba2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93036978"
---
# <a name="console-buffer-security-and-access-rights"></a>Sicherheit und Zugriffsrechte für Konsolenpuffer

Das Windows-Sicherheitsmodell ermöglicht es Ihnen, den Zugriff auf Konsolen Eingabepuffer und Konsolenbildschirm Puffer zu steuern. Weitere Informationen zur Sicherheit finden Sie unter [Zugriffs Steuerungsmodell](https://msdn.microsoft.com/library/windows/desktop/aa374876).

## <a name="console-object-security-descriptors"></a>Sicherheits Deskriptoren für Konsolen Objekte

Sie können eine [Sicherheits Beschreibung](https://msdn.microsoft.com/library/windows/desktop/aa379563) für die Konsolen Eingabe und die Bildschirm Puffer der Konsole angeben, wenn Sie [**die Funktion**](https://msdn.microsoft.com/library/windows/desktop/aa363858) "up" oder " [**kreateconsoleskreenbuffer**](createconsolescreenbuffer.md) " aufrufen. Wenn Sie **null** angeben, erhält das Objekt eine Standard Sicherheits Beschreibung. Die ACLs in der Standard Sicherheits Beschreibung für einen Konsolen Puffer stammen aus dem primären Token oder dem Identitätswechsel Token des Erstellers.

Die von "", "", " [**", "**](https://msdn.microsoft.com/library/windows/desktop/aa363858)", " [**", "**](createconsolescreenbuffer.md)", "", " **" und " \_** [**getstdhandle**](getstdhandle.md) " zurückgegebenen Handles verfügen über die **allgemeinen \_ Lese** Zugriffsrechte und

Zu den gültigen Zugriffsrechten gehören die allgemeinen **\_ Lese** -und **generischen \_ Schreib** [Zugriffsrechte](https://msdn.microsoft.com/library/windows/desktop/aa446632).

| Wert | Bedeutung |
|-|-|
| **Generisch \_ Read** (0x80000000l)  | Fordert Lesezugriff auf den Konsolenbildschirm Puffer an und ermöglicht dem Prozess das Lesen von Daten aus dem Puffer. |
| **Generisch \_ Write** (0x40000000l) | Fordert Schreibzugriff auf den Konsolenbildschirm Puffer an und ermöglicht dem Prozess das Schreiben von Daten in den Puffer. |

> [!NOTE]
> **[Universelle Windows-Plattform Konsolen-apps](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** und solche mit einer niedrigeren **[Integritäts Stufe](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** als die angefügte Konsole sind nicht berechtigt, den Ausgabepuffer zu lesen und in den Eingabepuffer zu schreiben, auch wenn die oben aufgeführten Sicherheits Deskriptoren normalerweise dies zulassen. Weitere Informationen finden Sie im nachfolgenden **[Verben](#wrong-way-verbs)** -Diskussions Abschnitt.

## <a name="wrong-way-verbs"></a>Wrong-Way Verben

Einige Vorgänge für die Konsolen Objekte werden verweigert, auch wenn das Objekt über eine Sicherheits Beschreibung verfügt, mit der angegeben wird, dass Lese-oder Schreibvorgänge ausdrücklich zulässig sind. Dabei handelt es sich insbesondere um Befehlszeilen Anwendungen, die in einem Kontext mit eingeschränkten Berechtigungen ausgeführt werden und eine Konsolen Sitzung gemeinsam nutzen, die von einer Befehlszeilen Anwendung in einem besser Aufforderungs Kontext erstellt wurde.

Der Begriff "falsche-Wege-Verben" soll auf den Vorgang angewendet werden, der das Gegenteil des normalen Flows für eines der Konsolen Objekte ist. Insbesondere wird der normale Flow für den Ausgabepuffer geschrieben, und der normale Flow für den Eingabepuffer wird gelesen. Der "falsche Weg" wäre daher das Lesen des Ausgabepuffers oder das Schreiben des Eingabe Puffers. Dabei handelt es sich um Funktionen, die in der Dokumentation zu den e **[/a-Funktionen auf niedriger Ebene](low-level-console-i-o.md)** beschrieben werden.

Diese beiden Szenarien können gefunden werden:

1. **[Universelle Windows-Plattform Konsolen-apps](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** . Da es sich hierbei um die in anderen universelle Windows-Plattform Anwendungen handelt, haben Sie eine Zusage, dass Sie von anderen Anwendungen isoliert sind und die Benutzer Garantien für die Auswirkungen des Vorgangs bereitstellen.
1. Jede Konsolenanwendung, die absichtlich mit einer niedrigeren **[Integritäts Stufe](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** gestartet wird als die vorhandene Sitzung, die während der Verwendung von Bezeichnungs- **[oder tokenmanipulationen während der Bearbeitung](https://docs.microsoft.com/previous-versions/dotnet/articles/bb625960(v=msdn.10))** erreicht werden kann.

Wenn eines dieser Szenarien erkannt wird, wendet die Konsole das Flag "falsch-Wege-Verben" auf die Befehlszeilen-Anwendungs Verbindung an und lehnt Aufrufe der folgenden APIs ab, um die Oberfläche der Kommunikation zwischen den Ebenen zu verringern:

:::row:::
    :::column:::
        [ReadConsoleOutput](readconsoleoutput.md)  
        [ReadConsoleOutputCharacter](readconsoleoutputcharacter.md)  
        [ReadConsoleOutputAttribute](readconsoleoutputattribute.md)  
    :::column-end:::
    :::column:::
        [WriteConsoleInput](writeconsoleinput.md)  
    :::column-end:::
:::row-end:::

Abgelehnte Aufrufe erhalten den Fehlercode " **Zugriff verweigert** ", der dem entspricht, wenn die Lese-oder Schreib Berechtigung von den Sicherheits Beschreibungen für das Objekt verweigert wurde.
