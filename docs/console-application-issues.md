---
title: Probleme mit der Konsolenanwendung
description: Überprüfen Sie Konsolen Anwendungsprobleme, z. b. Funktionen, die Zeichen folgen im OEM-Zeichensatz akzeptieren oder zurückgeben, oder Funktionen, die ANSI-Zeichensatz Zeichenfolgen verwenden
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: a1e49e605d1379984ebff7d1737db5ef96c4ff0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038458"
---
# <a name="console-application-issues"></a>Probleme mit der Konsolenanwendung

Die 8-Bit-Konsolenfunktionen verwenden die OEM-Codepage. Alle anderen Funktionen verwenden standardmäßig die ANSI-Codepage. Dies bedeutet, dass Zeichen folgen, die von den Konsolenfunktionen zurückgegeben werden, von den anderen Funktionen möglicherweise nicht ordnungsgemäß verarbeitet werden und umgekehrt. Wenn **findfirstmelea** z. b. eine Zeichenfolge zurückgibt, die bestimmte Erweiterte ANSI-Zeichen enthält, wird die Zeichenfolge in " **Write-Consolea** " nicht ordnungsgemäß angezeigt.

Die beste langfristige Lösung für eine Konsolenanwendung ist die Verwendung von **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** . Die-Konsole akzeptiert UTF-16-Codierung für die W-Variante der APIs oder UTF-8-Codierung für eine Variante der APIs nach der Verwendung von **[setconsolecp](setconsolecp.md)** und **[setconsoleoutputcp](setconsoleoutputcp.md)** `65001` `CP_UTF8` für die UTF-8-Codepage (konstant).

Wenn Sie diese Lösung auslassen, sollte eine Konsolenanwendung die [setfileapistooem](https://msdn.microsoft.com/library/windows/desktop/aa365534) -Funktion verwenden. Diese Funktion ändert relevante Dateifunktionen, sodass Sie anstelle von ANSI-Zeichen folgen Zeichen folgen für den OEM-Zeichensatz erzeugt werden.

Im folgenden sind die Dateifunktionen aufgeführt:

:::row:::
    :::column:::
        [CopyFile](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [CreateDirectory](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [CreateFile](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [DeleteFile](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [FindFirstFile](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [FindNextFile](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [GetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [GetDiskFreeSpace](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [GetDriveType](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [Fehler bei GetModuleFileName](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [Fehler bei GetModuleHandle](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [GetSystemDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [GetTempFileName](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [GetTempPath](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [GetVolumeInformation](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [GetWindowsDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [MoveFile](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        ["Muvefileex"](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [OpenFile](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [RemoveDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [SearchPath](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [SetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [Setfileattribute](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

Beim Umgang mit Befehlszeilen sollte eine Konsolenanwendung die Befehlszeile in Unicode-Form abrufen und Sie mithilfe der relevanten Zeichen-zu-OEM-Funktionen in das OEM-Formular konvertieren. Beachten Sie auch, dass *argv* den ANSI-Zeichensatz verwendet.
