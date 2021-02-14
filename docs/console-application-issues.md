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
ms.openlocfilehash: e81a2b8f6e3b7ba17a7fd704aac868425c86d52c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358270"
---
# <a name="console-application-issues"></a>Probleme mit der Konsolenanwendung

Die 8-Bit-Konsolenfunktionen verwenden die OEM-Codepage. Alle anderen Funktionen verwenden standardmäßig die ANSI-Codepage. Dies bedeutet, dass Zeichen folgen, die von den Konsolenfunktionen zurückgegeben werden, von den anderen Funktionen möglicherweise nicht ordnungsgemäß verarbeitet werden und umgekehrt. Wenn **findfirstmelea** z. b. eine Zeichenfolge zurückgibt, die bestimmte Erweiterte ANSI-Zeichen enthält, wird die Zeichenfolge in " **Write-Consolea** " nicht ordnungsgemäß angezeigt.

Die beste langfristige Lösung für eine Konsolenanwendung ist die Verwendung von **[Unicode](/windows/win32/intl/unicode)**. Die-Konsole akzeptiert UTF-16-Codierung für die W-Variante der APIs oder UTF-8-Codierung für eine Variante der APIs nach der Verwendung von **[setconsolecp](setconsolecp.md)** und **[setconsoleoutputcp](setconsoleoutputcp.md)** `65001` `CP_UTF8` für die UTF-8-Codepage (konstant).

Wenn Sie diese Lösung auslassen, sollte eine Konsolenanwendung die [setfileapistooem](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) -Funktion verwenden. Diese Funktion ändert relevante Dateifunktionen, sodass Sie anstelle von ANSI-Zeichen folgen Zeichen folgen für den OEM-Zeichensatz erzeugt werden.

Im folgenden sind die Dateifunktionen aufgeführt:

:::row:::
    :::column:::
        [CopyFile](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [CreateDirectory](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [DeleteFile](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [FindFirstFile](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [GetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [GetDiskFreeSpace](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [GetDriveType](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [Fehler bei GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [Fehler bei GetModuleHandle](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [GetSystemDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [GetTempFileName](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [GetVolumeInformation](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [GetWindowsDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [MoveFile](/windows/win32/api/winbase/nf-winbase-movefile)  
        ["Muvefileex"](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [OpenFile](/windows/win32/api/winbase/nf-winbase-openfile)  
        [RemoveDirectory](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [SearchPath](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [Setfileattribute](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

Beim Umgang mit Befehlszeilen sollte eine Konsolenanwendung die Befehlszeile in Unicode-Form abrufen und Sie mithilfe der relevanten Zeichen-zu-OEM-Funktionen in das OEM-Formular konvertieren. Beachten Sie auch, dass *argv* den ANSI-Zeichensatz verwendet.