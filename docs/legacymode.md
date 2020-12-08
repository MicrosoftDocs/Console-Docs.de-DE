---
title: 'Legacy-Konsolenmodus: Windows-Desktop'
description: Der Legacy-Konsolenmodus ist ein Kompatibilitätstool zur Unterstützung beim Ausführen von Befehlszeilenanwendungen, die möglicherweise nicht mit dem Windows 10-Konsolenhost funktionieren.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API, Kompatibilität
ms.openlocfilehash: eeddfd00ffa8c3ad9d99583b89e4b3be7959f445
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037708"
---
# <a name="legacy-console-mode"></a>Legacy-Konsolenmodus

Der Legacy-Konsolenmodus ist ein Kompatibilitätstool, das Benutzern älterer Befehlszeilentools unter Windows 10 helfen soll. Dieser Modus bietet für jedes Befehlszeilentool, das in der standardmäßigen Windows 10-Konsolenerfahrung nicht angezeigt oder nicht ordnungsgemäß ausgeführt wird, eine grobe Lösung, mit der das System auf eine ältere Version der Konsolenhostingerfahrung zurückgesetzt werden kann.

## <a name="using-legacy-console-mode"></a>Verwenden des Legacy-Konsolenmodus

Um den Legacy-Konsolenmodus zu verwenden, öffnen Sie zunächst ein Konsolenhostingfenster. Dies erfolgt in der Regel durch Starten eines der Befehlsinterpreter [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) oder [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).

Klicken Sie mit der rechten Maustaste auf die Titelleiste der Anwendung, und wählen Sie die Menüoption `Properties` aus. Wählen Sie die erste Registerkarte aus, `Options`. Aktivieren Sie dann das Kontrollkästchen unten auf der Seite, `Use legacy console`. Drücken Sie die Taste `OK`, um die Option anzuwenden.

Die Einstellung kann zurückgesetzt werden, indem Sie zum selben Menü des Eigenschaftenblatts zurückkehren, das Kontrollkästchen deaktivieren und dann `OK` drücken.

> [!NOTE]
>Diese Einstellung wird global auf alle Sitzungen angewendet, die nach Änderung der Einstellung gestartet werden. Sitzungen, die bereits geöffnet sind, werden nicht geändert.

## <a name="differences-between-modes"></a>Unterschiede zwischen den Modi

Das Konsolenhostteam versucht, die Unterschiede zwischen den Legacy- und aktuellen Modi der Konsole zu minimieren, um sicherzustellen, dass so viele Kunden wie möglich die aktuellste Version ausführen können. Wenn ein Problem auftritt, das erfordert, dass Sie die Legacy-Konsole verwenden, die hier nicht dokumentiert ist, wenden Sie sich wegen Unterstützung an das Team über das GitHub-Repository [microsoft/terminal](https://github.com/microsoft/terminal/) oder den [Feedback-Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app).

### <a name="16-bit-applications-on-32-bit-windows"></a>16-Bit-Anwendungen unter 32-Bit-Windows

Einige 16-Bit-Anwendungen unter 32-Bit-Windows verwenden eine virtuelle Computertechnologie, um aufgerufene [NTVDMs](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support) zu betreiben. Häufig verwenden diese Anwendungen für ihren Betrieb einen grafischen Bildschirmpuffermodus in Verbindung mit der Konsolenhostingumgebung. Nur die Legacy-Konsolenerfahrung unterstützt diese grafischen Puffermodi sowie die zusätzliche Konsolen-API-Unterstützung, die zur Unterstützung dieser Anwendungen erforderlich ist. Das System wählt automatisch die Legacy-Konsolenumgebung aus, wenn eine dieser Anwendungen gestartet wird.

### <a name="ime-embedding"></a>IME-Einbettung

Beim Legacy-Konsolenhost wurde der Vorschlagsteil des IME innerhalb des Hostingfensters eingebettet, indem eine Zeile am unteren Bildschirmrand für Vorschläge reserviert wurde. Die aktuelle Konsolenhostumgebung delegiert diese Aktivität stattdessen an das IME-Subsystem, um ein Überlagerungsfenster mit Vorschlägen oberhalb des Konsolenhosts anzuzeigen. In einer Umgebung, in der Überlagerungsfenster nicht möglich sind (z. B. bei bestimmten Remotingtools), kann es erforderlich sein, den Legacy-Konsolenhost zu verwenden.

### <a name="api-differences"></a>API-Unterschiede

Der bekannte Hauptunterschied zwischen Legacy- und aktueller Version besteht in der Implementierung von UTF-8. Der Legacy-Host verfügt über eine äußerst rudimentäre und häufig fehlerhafte Unterstützung von UTF-8 mit [Codepage 65001](https://docs.microsoft.com/windows/win32/intl/code-pages). Der aktuelle Konsolenhost enthält inkrementelle Verbesserungen in jedem neuen Release von Windows 10, um diese Unterstützung zu verbessern. Anwendungen, die versuchen, sich auf die Vorhersage von „bekannt fehlerhaften“ Interpretationen von UTF-8 durch die Legacy-Konsole zu verlassen, erhalten unterschiedliche Antworten, wenn die Unterstützung verbessert wird.

Andere bei APIs auftretende Unterschiede sollten dem [GitHub-Repository „microsoft/terminal“](https://github.com/microsoft/terminal/) oder über den [Feedback-Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) zum Zwecke der Selektierung und möglichen Korrektur gemeldet werden.
