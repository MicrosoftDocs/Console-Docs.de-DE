---
title: Getstdhandle-Funktion
description: Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420209"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="1dfbb-104">Getstdhandle-Funktion</span><span class="sxs-lookup"><span data-stu-id="1dfbb-104">GetStdHandle function</span></span>

<span data-ttu-id="1dfbb-105">Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).</span><span class="sxs-lookup"><span data-stu-id="1dfbb-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="1dfbb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dfbb-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="1dfbb-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1dfbb-107">Parameters</span></span>

<span data-ttu-id="1dfbb-108">*nstdhandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1dfbb-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="1dfbb-109">Das Standardgerät.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-109">The standard device.</span></span> <span data-ttu-id="1dfbb-110">Dieser Parameter kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="1dfbb-111">Wert</span><span class="sxs-lookup"><span data-stu-id="1dfbb-111">Value</span></span> | <span data-ttu-id="1dfbb-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="1dfbb-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="1dfbb-113">**STD_INPUT_HANDLE** (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="1dfbb-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="1dfbb-114">Das Standardeingabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-114">The standard input device.</span></span> <span data-ttu-id="1dfbb-115">Anfänglich ist dies der Konsolen Eingabepuffer `CONIN$` .</span><span class="sxs-lookup"><span data-stu-id="1dfbb-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="1dfbb-116">**STD_OUTPUT_HANDLE** (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="1dfbb-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="1dfbb-117">Das Standardausgabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-117">The standard output device.</span></span> <span data-ttu-id="1dfbb-118">Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="1dfbb-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="1dfbb-119">**STD_ERROR_HANDLE** (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="1dfbb-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="1dfbb-120">Das Standardfehler Gerät.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-120">The standard error device.</span></span> <span data-ttu-id="1dfbb-121">Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="1dfbb-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1dfbb-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1dfbb-122">Return value</span></span>

<span data-ttu-id="1dfbb-123">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für das angegebene Gerät oder ein umgeleitetes handle, das durch einen vorherigen-Befehl von [**setstdhandle**](setstdhandle.md)festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="1dfbb-124">Das Handle verfügt über **allgemeine \_ Lese** -und **allgemeine \_ Schreib** Zugriffsrechte, es sei denn, die Anwendung hat **setstdhandle** verwendet, um ein Standard Handle mit geringerem Zugriff festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="1dfbb-125">Wenn die Funktion fehlschlägt, ist der Rückgabewert ein **ungültiger \_ handle- \_ Wert**.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="1dfbb-126">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1dfbb-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="1dfbb-127">Wenn einer Anwendung keine Standard Handles zugeordnet sind, z. b. ein Dienst, der auf einem interaktiven Desktop ausgeführt wird, und Sie nicht umgeleitet hat, ist der Rückgabewert **null**.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="1dfbb-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1dfbb-128">Remarks</span></span>

<span data-ttu-id="1dfbb-129">Von **getstdhandle** zurückgegebene Handles können von Anwendungen verwendet werden, die aus der Konsole lesen oder in diese schreiben müssen.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="1dfbb-130">Wenn eine-Konsole erstellt wird, ist das Standardeingabe Handle ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe und Standard-Fehler Handles sind Handles des aktiven Bildschirm Puffers der Konsole.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="1dfbb-131">Diese Handles können von den Funktionen " [**Infofile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " und " [**schreitefile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder von einer der Konsolenfunktionen verwendet werden, die auf den Konsolen Eingabepuffer oder einen Bildschirm Puffer zugreifen (z. b. die Funktionen " [**infoconsoleinput**](readconsoleinput.md)", " [**Write Console**](writeconsole.md)" oder " [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) ").</span><span class="sxs-lookup"><span data-stu-id="1dfbb-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="1dfbb-132">Die Standard Handles eines Prozesses können durch einen aufzurufenden [**setstdhandle**](setstdhandle.md)umgeleitet werden. in diesem Fall gibt **getstdhandle** das umgeleitete Handle zurück.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="1dfbb-133">Wenn die Standard Handles umgeleitet wurden, können Sie den `CONIN$` Wert in einem Aufrufen der Funktion "- [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) Funktion" angeben, um ein Handle für den Eingabepuffer einer Konsole zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="1dfbb-134">Entsprechend können Sie den Wert angeben, `CONOUT$` um ein Handle für den aktiven Bildschirm Puffer einer Konsole zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="1dfbb-135">Die Standard Handles eines Prozesses für den Eintrag der Main-Methode werden durch die Konfiguration des [**/Subsystem**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) -Flags vorgegeben, das beim Erstellen der Anwendung an den Linker weitergegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="1dfbb-136">Durch Angeben von **/Subsystem: Console** wird angefordert, dass das Betriebssystem die Handles beim Start mit einer Konsolen Sitzung aufgefüllt, wenn das übergeordnete Element die Standard handle-Tabelle nicht bereits nach Vererbung ausgefüllt hat.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="1dfbb-137">Im Gegensatz dazu bedeutet **/Subsystem: Windows** , dass die Anwendung keine Konsole benötigt und wahrscheinlich nicht die Standard Handles verwendet.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="1dfbb-138">Weitere Informationen zur Behandlung von Vererbungen finden Sie in der Dokumentation zu [**Startf \_ usestdhandles**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span><span class="sxs-lookup"><span data-stu-id="1dfbb-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="1dfbb-139">Einige Anwendungen arbeiten außerhalb der Grenzen Ihres deklarierten Subsystems. Beispielsweise kann eine **/Subsystem: Windows** -Anwendung Standard Handles für Protokollierungs-oder Debugzwecke überprüfen/verwenden, aber normal mit einer grafischen Benutzeroberfläche arbeiten.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="1dfbb-140">Diese Anwendungen müssen den Status der Standard Handles beim Start sorgfältig überprüfen und mithilfe von [**attachconsole**](attachconsole.md), [**Zuordnungen Console**](allocconsole.md)und [**freeconsole**](freeconsole.md) eine Konsole hinzufügen bzw. entfernen, wenn gewünscht.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="1dfbb-141">Einige Anwendungen können auch das Verhalten für den Typ des geerbten Handles verändern.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="1dfbb-142">Die Unterscheidung zwischen Konsolen, Pipe, Datei und anderen Typen kann mit " [**getfiletype**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype)" durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="1dfbb-143">Verhalten beim Anfügen/trennen</span><span class="sxs-lookup"><span data-stu-id="1dfbb-143">Attach/detach behavior</span></span>

<span data-ttu-id="1dfbb-144">Beim Anfügen an eine neue Konsole werden Standard Handles immer durch Konsolen Handles ersetzt, es sei denn, während der Prozesserstellung wurde **Startf \_ usestdhandles** angegeben.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="1dfbb-145">Wenn der vorhandene Wert des Standard Handles **null** ist, oder wenn der vorhandene Wert des Standard Handles wie ein Konsolen Pseudo handle aussieht, wird das Handle durch ein Konsolen handle ersetzt.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="1dfbb-146">Wenn ein übergeordnetes Element sowohl **Create \_ New \_ Console** als auch **Startf \_ usestdhandles** verwendet, um einen Konsolen Prozess zu erstellen, werden Standard Handles nicht ersetzt, es sei denn, der vorhandene Wert des Standard Handles ist **null** oder ein Konsolen Pseudo handle.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="1dfbb-147">Konsolen Prozesse *müssen* mit den ausgefüllten Standard Handles beginnen oder automatisch mit den entsprechenden Handles für eine neue Konsole aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="1dfbb-148">Grafische Benutzeroberflächen Anwendungen (GUI) können ohne die Standard Handles gestartet werden und werden nicht automatisch ausgefüllt.</span><span class="sxs-lookup"><span data-stu-id="1dfbb-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="1dfbb-149">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1dfbb-149">Examples</span></span>

<span data-ttu-id="1dfbb-150">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="1dfbb-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1dfbb-151">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1dfbb-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1dfbb-152">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1dfbb-152">Minimum supported client</span></span> | <span data-ttu-id="1dfbb-153">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1dfbb-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1dfbb-154">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1dfbb-154">Minimum supported server</span></span> | <span data-ttu-id="1dfbb-155">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1dfbb-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1dfbb-156">Header</span><span class="sxs-lookup"><span data-stu-id="1dfbb-156">Header</span></span> | <span data-ttu-id="1dfbb-157">Processenv. h (über Winbase. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1dfbb-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="1dfbb-158">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1dfbb-158">Library</span></span> | <span data-ttu-id="1dfbb-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1dfbb-159">Kernel32.lib</span></span> |
| <span data-ttu-id="1dfbb-160">DLL</span><span class="sxs-lookup"><span data-stu-id="1dfbb-160">DLL</span></span> | <span data-ttu-id="1dfbb-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1dfbb-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="1dfbb-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1dfbb-162">See also</span></span>

[<span data-ttu-id="1dfbb-163">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1dfbb-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1dfbb-164">Konsolenhandles</span><span class="sxs-lookup"><span data-stu-id="1dfbb-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="1dfbb-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="1dfbb-165">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="1dfbb-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="1dfbb-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="1dfbb-167">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="1dfbb-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="1dfbb-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="1dfbb-168">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="1dfbb-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="1dfbb-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="1dfbb-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="1dfbb-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="1dfbb-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="1dfbb-171">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
