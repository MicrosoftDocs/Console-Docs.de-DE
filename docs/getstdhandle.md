---
title: Getstdhandle-Funktion
description: Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059626"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="06b1b-104">Getstdhandle-Funktion</span><span class="sxs-lookup"><span data-stu-id="06b1b-104">GetStdHandle function</span></span>


<span data-ttu-id="06b1b-105">Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).</span><span class="sxs-lookup"><span data-stu-id="06b1b-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="06b1b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="06b1b-106">Syntax</span></span>
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a><span data-ttu-id="06b1b-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="06b1b-107">Parameters</span></span>
----------

<span data-ttu-id="06b1b-108">*nstdhandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="06b1b-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="06b1b-109">Das Standardgerät.</span><span class="sxs-lookup"><span data-stu-id="06b1b-109">The standard device.</span></span> <span data-ttu-id="06b1b-110">Dieser Parameter kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="06b1b-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="06b1b-111">Wert</span><span class="sxs-lookup"><span data-stu-id="06b1b-111">Value</span></span></th>
<th><span data-ttu-id="06b1b-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="06b1b-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="06b1b-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="06b1b-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</span></span></td>
<td><p><span data-ttu-id="06b1b-114">Das Standardeingabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="06b1b-114">The standard input device.</span></span> <span data-ttu-id="06b1b-115">Anfänglich ist dies der Konsolen Eingabepuffer ("$").</span><span class="sxs-lookup"><span data-stu-id="06b1b-115">Initially, this is the console input buffer, CONIN$.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06b1b-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="06b1b-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</span></span></td>
<td><p><span data-ttu-id="06b1b-117">Das Standardausgabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="06b1b-117">The standard output device.</span></span> <span data-ttu-id="06b1b-118">Anfänglich handelt es sich hierbei um den aktiven Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="06b1b-118">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06b1b-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="06b1b-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</span></span></td>
<td><p><span data-ttu-id="06b1b-120">Das Standardfehler Gerät.</span><span class="sxs-lookup"><span data-stu-id="06b1b-120">The standard error device.</span></span> <span data-ttu-id="06b1b-121">Anfänglich handelt es sich hierbei um den aktiven Konsolenbildschirm Puffer.</span><span class="sxs-lookup"><span data-stu-id="06b1b-121">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="06b1b-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="06b1b-122">Return value</span></span>
------------

<span data-ttu-id="06b1b-123">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für das angegebene Gerät oder ein umgeleitetes handle, das durch einen vorherigen-Befehl von [**setstdhandle**](setstdhandle.md)festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="06b1b-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="06b1b-124">Das Handle verfügt über **allgemeine \_ Lese** -und **allgemeine \_ Schreib** Zugriffsrechte, es sei denn, die Anwendung hat **setstdhandle** verwendet, um ein Standard Handle mit geringerem Zugriff festzulegen.</span><span class="sxs-lookup"><span data-stu-id="06b1b-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="06b1b-125">Wenn die Funktion fehlschlägt, ist der Rückgabewert ein **ungültiger \_ handle- \_ Wert**.</span><span class="sxs-lookup"><span data-stu-id="06b1b-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="06b1b-126">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="06b1b-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="06b1b-127">Wenn einer Anwendung keine Standard Handles zugeordnet sind, z. b. ein Dienst, der auf einem interaktiven Desktop ausgeführt wird, und Sie nicht umgeleitet hat, ist der Rückgabewert **null**.</span><span class="sxs-lookup"><span data-stu-id="06b1b-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

<a name="remarks"></a><span data-ttu-id="06b1b-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="06b1b-128">Remarks</span></span>
-------

<span data-ttu-id="06b1b-129">Von **getstdhandle** zurückgegebene Handles können von Anwendungen verwendet werden, die aus der Konsole lesen oder in diese schreiben müssen.</span><span class="sxs-lookup"><span data-stu-id="06b1b-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="06b1b-130">Wenn eine-Konsole erstellt wird, ist das Standardeingabe Handle ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standard-Fehler Handles sind Handles des aktiven Bildschirm Puffers der Konsole.</span><span class="sxs-lookup"><span data-stu-id="06b1b-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="06b1b-131">Diese Handles können von den Funktionen " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**schreitefile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder von einer der Konsolenfunktionen verwendet werden, die auf den Konsolen Eingabepuffer oder einen Bildschirm Puffer zugreifen (z. b. die Funktionen " [**infoconsoleinput**](readconsoleinput.md)", " [**Write Console**](writeconsole.md)" oder " [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) ").</span><span class="sxs-lookup"><span data-stu-id="06b1b-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="06b1b-132">Die Standard Handles eines Prozesses können durch einen aufzurufenden [**setstdhandle**](setstdhandle.md)umgeleitet werden. in diesem Fall gibt **getstdhandle** das umgeleitete Handle zurück.</span><span class="sxs-lookup"><span data-stu-id="06b1b-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="06b1b-133">Wenn die Standard Handles umgeleitet wurden, können Sie den Wert von "$" in einem Aufrufen der Funktion "angleichen [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " angeben, um ein Handle für den Eingabepuffer einer Konsole abzurufen.</span><span class="sxs-lookup"><span data-stu-id="06b1b-133">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="06b1b-134">Entsprechend können Sie den Wert für "$ $" angeben, um ein Handle für den aktiven Bildschirm Puffer einer Konsole zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="06b1b-134">Similarly, you can specify the CONOUT$ value to get a handle to a console's active screen buffer.</span></span>

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span data-ttu-id="06b1b-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Verhalten beim Anfügen/trennen</span><span class="sxs-lookup"><span data-stu-id="06b1b-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Attach/detach behavior</span></span>

<span data-ttu-id="06b1b-136">Beim Anfügen an eine neue Konsole werden Standard Handles immer durch Konsolen Handles ersetzt, es sei denn, während der Prozesserstellung wurde **Startf \_ usestdhandles** angegeben.</span><span class="sxs-lookup"><span data-stu-id="06b1b-136">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="06b1b-137">Wenn der vorhandene Wert des Standard Handles **null**ist, oder wenn der vorhandene Wert des Standard Handles wie ein Konsolen Pseudo handle aussieht, wird das Handle durch ein Konsolen handle ersetzt.</span><span class="sxs-lookup"><span data-stu-id="06b1b-137">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="06b1b-138">Wenn ein übergeordnetes Element sowohl **Create \_ New \_ Console** als auch **Startf \_ usestdhandles** verwendet, um einen Konsolen Prozess zu erstellen, werden Standard Handles nicht ersetzt, es sei denn, der vorhandene Wert des Standard Handles ist NULL oder ein Konsolen Pseudo handle.</span><span class="sxs-lookup"><span data-stu-id="06b1b-138">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is NULL or a console pseudohandle.</span></span>

<a name="examples"></a><span data-ttu-id="06b1b-139">Beispiele</span><span class="sxs-lookup"><span data-stu-id="06b1b-139">Examples</span></span>
--------

<span data-ttu-id="06b1b-140">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="06b1b-140">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="06b1b-141">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="06b1b-141">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="06b1b-142">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="06b1b-142">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="06b1b-143">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="06b1b-143">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="06b1b-144">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="06b1b-144">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="06b1b-145">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="06b1b-145">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="06b1b-146">Header</span><span class="sxs-lookup"><span data-stu-id="06b1b-146">Header</span></span></p></td>
<td><span data-ttu-id="06b1b-147">Processenv. h (über Winbase. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="06b1b-147">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="06b1b-148">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="06b1b-148">Library</span></span></p></td>
<td><span data-ttu-id="06b1b-149">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="06b1b-149">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="06b1b-150">DLL</span><span class="sxs-lookup"><span data-stu-id="06b1b-150">DLL</span></span></p></td>
<td><span data-ttu-id="06b1b-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="06b1b-151">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="06b1b-152"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="06b1b-152"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="06b1b-153">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="06b1b-153">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="06b1b-154">Konsolen Handles</span><span class="sxs-lookup"><span data-stu-id="06b1b-154">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="06b1b-155">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="06b1b-155">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="06b1b-156">**Getconsoleskreenbufferinfo**</span><span class="sxs-lookup"><span data-stu-id="06b1b-156">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="06b1b-157">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="06b1b-157">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="06b1b-158">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="06b1b-158">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="06b1b-159">**Setstdhandle**</span><span class="sxs-lookup"><span data-stu-id="06b1b-159">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="06b1b-160">**Schreib Konsole**</span><span class="sxs-lookup"><span data-stu-id="06b1b-160">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="06b1b-161">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="06b1b-161">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




