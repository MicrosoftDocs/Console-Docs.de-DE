---
title: Legacy-Konsolenmodus – Windows-Desktop
description: Der Legacy Konsolenmodus ist ein Kompatibilitäts Tool zur Unterstützung beim Ausführen von Befehlszeilen Anwendungen, die möglicherweise nicht mit dem Windows 10-Konsolen Host funktionieren.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Kompatibilität
ms.openlocfilehash: a69e192426cc178ae98565db07c49f9ff2ce4961
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060035"
---
# <a name="legacy-console-mode"></a>Legacy-Konsolenmodus

Der Legacy Konsolenmodus ist ein Kompatibilitäts Tool, das Benutzern von älteren Befehlszeilen Tools unter Windows 10 helfen soll. Für ein beliebiges Befehlszeilen Tool, das in der standardmäßigen Windows 10-Konsolen Umgebung nicht angezeigt oder ordnungsgemäß ausgeführt wird, bietet dieser Modus eine grobe Lösung, mit der das System auf eine ältere Version des hostingerlebnisses der Konsole zurück wechselt.

## <a name="using-legacy-console-mode"></a>Verwenden des Legacy-Konsolenmodus

Um den Legacy Konsolenmodus zu verwenden, öffnen Sie zunächst ein Konsolen Hostingfenster. Dies erfolgt in der Regel durchstarten eines der Befehls Interpreter [cmd](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) oder [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Klicken Sie mit der rechten Maustaste auf die Titelleiste der Anwendung, und wählen Sie die `Properties` Menüoption. Wählen Sie die erste Registerkarte aus `Options` . Aktivieren Sie dann das Kontrollkästchen unten auf der Seite, in dem beschrieben wird `Use legacy console` . Drücken `OK` Sie die anzuwendende Schaltfläche.

Die Einstellung kann wieder hergestellt werden, indem Sie zum gleichen Eigenschaften Blatt Menü zurückkehren und dann das Kontrollkästchen deaktivieren `OK` .

**Hinweis:** Diese Einstellung wird global auf alle Sitzungen angewendet, die gestartet werden, nachdem die Einstellung geändert wurde. Sitzungen, die bereits geöffnet sind, werden nicht geändert.

## <a name="differences-between-modes"></a>Unterschiede zwischen Modi

Das Konsolen Host Team versucht, die Unterschiede zwischen dem Legacy-und dem aktuellen Modus der Konsole zu minimieren, um sicherzustellen, dass so viele Kunden wie möglich die aktuellste Version ausführen können. Wenn ein Problem auftritt, bei dem Sie die Legacy-Konsole verwenden müssen, die hier nicht dokumentiert ist, wenden Sie sich an das Team im [Microsoft/Terminal](https://github.com/microsoft/terminal/) -GitHub-Repository oder über den [Feedback-Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) , um Unterstützung zu erhalten.

### <a name="16-bit-applications-on-32-bit-windows"></a>16-Bit-Anwendungen auf 32-Bit-Windows

Einige 16-Bit-Anwendungen auf 32-Bit-Windows verwenden eine Technologie für virtuelle Computer, um den Namen [ntvdm](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support)zu betreiben. Häufig verwenden diese Anwendungen einen grafischen Bildschirm Puffer Modus in Verbindung mit der Konsolen Host Umgebung. Nur die Legacy-Konsolen Oberfläche unterstützt diese grafischen Puffer Modi und die zusätzliche Unterstützung der Konsolen-API, die zum Einschalten dieser Anwendungen erforderlich ist. Das System wählt automatisch die Legacy Konsolen Umgebung aus, wenn eine dieser Anwendungen gestartet wird.

### <a name="ime-embedding"></a>IME-Einbettung

Der ältere Konsolen Host hat den Vorschlags Teil des IME innerhalb des hostingfensters eingebettet, indem er eine Zeile am unteren Bildschirmrand für Vorschläge reserviert. Die aktuelle Konsolen Host Umgebung delegiert diese Aktivität stattdessen an das IME-Subsystem, um ein Überlagerungs Fenster oberhalb des Konsolen Hosts mit Vorschlägen anzuzeigen. In einer Umgebung, in der über Lagerungs Fenster nicht möglich sind (z. b. mit bestimmten remotingtools), ist möglicherweise der Legacy-Konsolen Host erforderlich.

### <a name="api-differences"></a>API-Unterschiede

Der Hauptunterschied zwischen Legacy und Current ist die Implementierung von UTF-8. Der Legacy Host hat eine extrem rudimentäre und häufig falsche Unterstützung von UTF-8 mit der [Codepage 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). Der aktuelle Konsolen Host enthält inkrementelle Verbesserungen der Freigabe von Windows 10, um diese Unterstützung zu verbessern. Anwendungen, die versuchen, sich auf die Vorhersage von UTF-8 von UTF-8 von der Legacy Konsole aus zu verlassen, erhalten unterschiedliche Antworten, da die Unterstützung verbessert wird. 

Andere Unterschiede in Bezug auf APIs sollten an das [Microsoft/Terminal](https://github.com/microsoft/terminal/) -GitHub-Repository oder über den [Feedback-Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) gesendet werden, um selektiert und eine mögliche Behebung zu beheben.