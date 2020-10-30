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
# <a name="console-application-issues"></a><span data-ttu-id="603ef-104">Probleme mit der Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="603ef-104">Console Application Issues</span></span>

<span data-ttu-id="603ef-105">Die 8-Bit-Konsolenfunktionen verwenden die OEM-Codepage.</span><span class="sxs-lookup"><span data-stu-id="603ef-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="603ef-106">Alle anderen Funktionen verwenden standardmäßig die ANSI-Codepage.</span><span class="sxs-lookup"><span data-stu-id="603ef-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="603ef-107">Dies bedeutet, dass Zeichen folgen, die von den Konsolenfunktionen zurückgegeben werden, von den anderen Funktionen möglicherweise nicht ordnungsgemäß verarbeitet werden und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="603ef-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="603ef-108">Wenn **findfirstmelea** z. b. eine Zeichenfolge zurückgibt, die bestimmte Erweiterte ANSI-Zeichen enthält, wird die Zeichenfolge in " **Write-Consolea** " nicht ordnungsgemäß angezeigt.</span><span class="sxs-lookup"><span data-stu-id="603ef-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="603ef-109">Die beste langfristige Lösung für eine Konsolenanwendung ist die Verwendung von **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span><span class="sxs-lookup"><span data-stu-id="603ef-109">The best long-term solution for a console application is to use **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span></span> <span data-ttu-id="603ef-110">Die-Konsole akzeptiert UTF-16-Codierung für die W-Variante der APIs oder UTF-8-Codierung für eine Variante der APIs nach der Verwendung von **[setconsolecp](setconsolecp.md)** und **[setconsoleoutputcp](setconsoleoutputcp.md)** `65001` `CP_UTF8` für die UTF-8-Codepage (konstant).</span><span class="sxs-lookup"><span data-stu-id="603ef-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="603ef-111">Wenn Sie diese Lösung auslassen, sollte eine Konsolenanwendung die [setfileapistooem](https://msdn.microsoft.com/library/windows/desktop/aa365534) -Funktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="603ef-111">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="603ef-112">Diese Funktion ändert relevante Dateifunktionen, sodass Sie anstelle von ANSI-Zeichen folgen Zeichen folgen für den OEM-Zeichensatz erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="603ef-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="603ef-113">Im folgenden sind die Dateifunktionen aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="603ef-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="603ef-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="603ef-114">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="603ef-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="603ef-115">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="603ef-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="603ef-116">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="603ef-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="603ef-117">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="603ef-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="603ef-118">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="603ef-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="603ef-119">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="603ef-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="603ef-120">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="603ef-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="603ef-121">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="603ef-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="603ef-122">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="603ef-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="603ef-123">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="603ef-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="603ef-124">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="603ef-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="603ef-125">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="603ef-126">Fehler bei GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="603ef-126">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="603ef-127">Fehler bei GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="603ef-127">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="603ef-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="603ef-128">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="603ef-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="603ef-129">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="603ef-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="603ef-130">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="603ef-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="603ef-131">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="603ef-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="603ef-132">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="603ef-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="603ef-133">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="603ef-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="603ef-134">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="603ef-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="603ef-135">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="603ef-136">"Muvefileex"</span><span class="sxs-lookup"><span data-stu-id="603ef-136">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="603ef-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="603ef-137">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="603ef-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="603ef-138">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="603ef-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="603ef-139">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="603ef-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="603ef-140">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="603ef-141">Setfileattribute</span><span class="sxs-lookup"><span data-stu-id="603ef-141">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="603ef-142">Beim Umgang mit Befehlszeilen sollte eine Konsolenanwendung die Befehlszeile in Unicode-Form abrufen und Sie mithilfe der relevanten Zeichen-zu-OEM-Funktionen in das OEM-Formular konvertieren.</span><span class="sxs-lookup"><span data-stu-id="603ef-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="603ef-143">Beachten Sie auch, dass *argv* den ANSI-Zeichensatz verwendet.</span><span class="sxs-lookup"><span data-stu-id="603ef-143">Note, also, that *argv* uses the ANSI character set.</span></span>
