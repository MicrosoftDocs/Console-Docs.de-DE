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
# <a name="console-application-issues"></a><span data-ttu-id="9ee21-104">Probleme mit der Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="9ee21-104">Console Application Issues</span></span>

<span data-ttu-id="9ee21-105">Die 8-Bit-Konsolenfunktionen verwenden die OEM-Codepage.</span><span class="sxs-lookup"><span data-stu-id="9ee21-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="9ee21-106">Alle anderen Funktionen verwenden standardmäßig die ANSI-Codepage.</span><span class="sxs-lookup"><span data-stu-id="9ee21-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="9ee21-107">Dies bedeutet, dass Zeichen folgen, die von den Konsolenfunktionen zurückgegeben werden, von den anderen Funktionen möglicherweise nicht ordnungsgemäß verarbeitet werden und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="9ee21-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="9ee21-108">Wenn **findfirstmelea** z. b. eine Zeichenfolge zurückgibt, die bestimmte Erweiterte ANSI-Zeichen enthält, wird die Zeichenfolge in " **Write-Consolea** " nicht ordnungsgemäß angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9ee21-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="9ee21-109">Die beste langfristige Lösung für eine Konsolenanwendung ist die Verwendung von **[Unicode](/windows/win32/intl/unicode)**.</span><span class="sxs-lookup"><span data-stu-id="9ee21-109">The best long-term solution for a console application is to use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="9ee21-110">Die-Konsole akzeptiert UTF-16-Codierung für die W-Variante der APIs oder UTF-8-Codierung für eine Variante der APIs nach der Verwendung von **[setconsolecp](setconsolecp.md)** und **[setconsoleoutputcp](setconsoleoutputcp.md)** `65001` `CP_UTF8` für die UTF-8-Codepage (konstant).</span><span class="sxs-lookup"><span data-stu-id="9ee21-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="9ee21-111">Wenn Sie diese Lösung auslassen, sollte eine Konsolenanwendung die [setfileapistooem](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) -Funktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="9ee21-111">Barring that solution, a console application should use the [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) function.</span></span> <span data-ttu-id="9ee21-112">Diese Funktion ändert relevante Dateifunktionen, sodass Sie anstelle von ANSI-Zeichen folgen Zeichen folgen für den OEM-Zeichensatz erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="9ee21-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="9ee21-113">Im folgenden sind die Dateifunktionen aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="9ee21-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="9ee21-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="9ee21-114">CopyFile</span></span>](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [<span data-ttu-id="9ee21-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="9ee21-115">CreateDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [<span data-ttu-id="9ee21-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="9ee21-116">CreateFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [<span data-ttu-id="9ee21-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="9ee21-117">CreateProcess</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [<span data-ttu-id="9ee21-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="9ee21-118">DeleteFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [<span data-ttu-id="9ee21-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="9ee21-119">FindFirstFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [<span data-ttu-id="9ee21-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="9ee21-120">FindNextFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [<span data-ttu-id="9ee21-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="9ee21-121">GetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [<span data-ttu-id="9ee21-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="9ee21-122">GetDiskFreeSpace</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [<span data-ttu-id="9ee21-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="9ee21-123">GetDriveType</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="9ee21-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="9ee21-124">GetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [<span data-ttu-id="9ee21-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="9ee21-125">GetFullPathName</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [<span data-ttu-id="9ee21-126">Fehler bei GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="9ee21-126">GetModuleFileName</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [<span data-ttu-id="9ee21-127">Fehler bei GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="9ee21-127">GetModuleHandle</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [<span data-ttu-id="9ee21-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="9ee21-128">GetSystemDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [<span data-ttu-id="9ee21-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="9ee21-129">GetTempFileName</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [<span data-ttu-id="9ee21-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="9ee21-130">GetTempPath</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [<span data-ttu-id="9ee21-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="9ee21-131">GetVolumeInformation</span></span>](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [<span data-ttu-id="9ee21-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="9ee21-132">GetWindowsDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [<span data-ttu-id="9ee21-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="9ee21-133">LoadLibrary</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="9ee21-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="9ee21-134">LoadLibraryEx</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [<span data-ttu-id="9ee21-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="9ee21-135">MoveFile</span></span>](/windows/win32/api/winbase/nf-winbase-movefile)  
        [<span data-ttu-id="9ee21-136">"Muvefileex"</span><span class="sxs-lookup"><span data-stu-id="9ee21-136">MoveFileEx</span></span>](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [<span data-ttu-id="9ee21-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="9ee21-137">OpenFile</span></span>](/windows/win32/api/winbase/nf-winbase-openfile)  
        [<span data-ttu-id="9ee21-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="9ee21-138">RemoveDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [<span data-ttu-id="9ee21-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="9ee21-139">SearchPath</span></span>](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [<span data-ttu-id="9ee21-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="9ee21-140">SetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [<span data-ttu-id="9ee21-141">Setfileattribute</span><span class="sxs-lookup"><span data-stu-id="9ee21-141">SetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="9ee21-142">Beim Umgang mit Befehlszeilen sollte eine Konsolenanwendung die Befehlszeile in Unicode-Form abrufen und Sie mithilfe der relevanten Zeichen-zu-OEM-Funktionen in das OEM-Formular konvertieren.</span><span class="sxs-lookup"><span data-stu-id="9ee21-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="9ee21-143">Beachten Sie auch, dass *argv* den ANSI-Zeichensatz verwendet.</span><span class="sxs-lookup"><span data-stu-id="9ee21-143">Note, also, that *argv* uses the ANSI character set.</span></span>