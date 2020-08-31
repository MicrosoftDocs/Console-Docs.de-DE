---
title: Konsolen Anwendungsprobleme
description: Überprüfen Sie Konsolen Anwendungsprobleme, z. b. Funktionen, die Zeichen folgen im OEM-Zeichensatz akzeptieren oder zurückgeben, oder Funktionen, die ANSI-Zeichensatz Zeichenfolgen verwenden
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: 4bf0d6792a991d8ae141ec0b1b9c940311e00ab9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060170"
---
# <a name="console-application-issues"></a><span data-ttu-id="4180c-104">Konsolen Anwendungsprobleme</span><span class="sxs-lookup"><span data-stu-id="4180c-104">Console Application Issues</span></span>

<span data-ttu-id="4180c-105">Die 8-Bit-Konsolenfunktionen verwenden die OEM-Codepage.</span><span class="sxs-lookup"><span data-stu-id="4180c-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="4180c-106">Alle anderen Funktionen verwenden standardmäßig die ANSI-Codepage.</span><span class="sxs-lookup"><span data-stu-id="4180c-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="4180c-107">Dies bedeutet, dass Zeichen folgen, die von den Konsolenfunktionen zurückgegeben werden, von den anderen Funktionen möglicherweise nicht ordnungsgemäß verarbeitet werden und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="4180c-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="4180c-108">Wenn **findfirstmelea** z. b. eine Zeichenfolge zurückgibt, die bestimmte Erweiterte ANSI-Zeichen enthält, wird die Zeichenfolge in " **Write-Consolea** " nicht ordnungsgemäß angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4180c-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="4180c-109">Die beste langfristige Lösung für eine Konsolenanwendung ist die Verwendung von Unicode.</span><span class="sxs-lookup"><span data-stu-id="4180c-109">The best long-term solution for a console application is to use Unicode.</span></span> <span data-ttu-id="4180c-110">Wenn Sie diese Lösung auslassen, sollte eine Konsolenanwendung die [setfileapistooem](https://msdn.microsoft.com/library/windows/desktop/aa365534) -Funktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="4180c-110">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="4180c-111">Diese Funktion ändert relevante Dateifunktionen, sodass Sie anstelle von ANSI-Zeichen folgen Zeichen folgen für den OEM-Zeichensatz erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="4180c-111">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="4180c-112">Im folgenden sind die Dateifunktionen aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="4180c-112">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="4180c-113">CopyFile</span><span class="sxs-lookup"><span data-stu-id="4180c-113">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="4180c-114">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="4180c-114">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="4180c-115">CreateFile</span><span class="sxs-lookup"><span data-stu-id="4180c-115">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="4180c-116">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="4180c-116">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="4180c-117">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="4180c-117">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="4180c-118">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="4180c-118">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="4180c-119">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="4180c-119">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="4180c-120">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="4180c-120">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="4180c-121">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="4180c-121">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="4180c-122">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="4180c-122">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="4180c-123">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="4180c-123">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="4180c-124">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="4180c-124">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="4180c-125">Fehler bei GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="4180c-125">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="4180c-126">Fehler bei GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="4180c-126">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="4180c-127">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="4180c-127">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="4180c-128">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="4180c-128">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="4180c-129">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="4180c-129">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="4180c-130">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="4180c-130">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="4180c-131">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="4180c-131">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="4180c-132">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="4180c-132">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="4180c-133">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="4180c-133">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="4180c-134">MoveFile</span><span class="sxs-lookup"><span data-stu-id="4180c-134">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="4180c-135">"Muvefileex"</span><span class="sxs-lookup"><span data-stu-id="4180c-135">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="4180c-136">OpenFile</span><span class="sxs-lookup"><span data-stu-id="4180c-136">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="4180c-137">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="4180c-137">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="4180c-138">SearchPath</span><span class="sxs-lookup"><span data-stu-id="4180c-138">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="4180c-139">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="4180c-139">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="4180c-140">Setfileattribute</span><span class="sxs-lookup"><span data-stu-id="4180c-140">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="4180c-141">Beim Umgang mit Befehlszeilen sollte eine Konsolenanwendung die Befehlszeile in Unicode-Form abrufen und Sie mithilfe der relevanten Zeichen-zu-OEM-Funktionen in das OEM-Formular konvertieren.</span><span class="sxs-lookup"><span data-stu-id="4180c-141">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="4180c-142">Beachten Sie auch, dass *argv* den ANSI-Zeichensatz verwendet.</span><span class="sxs-lookup"><span data-stu-id="4180c-142">Note, also, that *argv* uses the ANSI character set.</span></span>
