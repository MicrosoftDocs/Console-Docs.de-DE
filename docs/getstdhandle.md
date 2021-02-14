---
title: GetStdHandle-Funktion
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
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358750"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="b9db0-104">GetStdHandle-Funktion</span><span class="sxs-lookup"><span data-stu-id="b9db0-104">GetStdHandle function</span></span>

<span data-ttu-id="b9db0-105">Ruft ein Handle für das angegebene Standardgerät ab (Standardeingabe, Standardausgabe oder Standardfehler).</span><span class="sxs-lookup"><span data-stu-id="b9db0-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="b9db0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9db0-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="b9db0-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="b9db0-107">Parameters</span></span>

<span data-ttu-id="b9db0-108">*nStdHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b9db0-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="b9db0-109">Das Standardgerät.</span><span class="sxs-lookup"><span data-stu-id="b9db0-109">The standard device.</span></span> <span data-ttu-id="b9db0-110">Dieser Parameter kann einen der folgenden Werte annehmen.</span><span class="sxs-lookup"><span data-stu-id="b9db0-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="b9db0-111">Wert</span><span class="sxs-lookup"><span data-stu-id="b9db0-111">Value</span></span> | <span data-ttu-id="b9db0-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="b9db0-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="b9db0-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="b9db0-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="b9db0-114">Das Standardeingabegerät.</span><span class="sxs-lookup"><span data-stu-id="b9db0-114">The standard input device.</span></span> <span data-ttu-id="b9db0-115">Anfänglich ist dies der Konsoleneingabepuffer, `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="b9db0-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="b9db0-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="b9db0-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="b9db0-117">Das Standardausgabegerät.</span><span class="sxs-lookup"><span data-stu-id="b9db0-117">The standard output device.</span></span> <span data-ttu-id="b9db0-118">Anfänglich ist dies der aktive Konsolenbildschirmpuffer, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="b9db0-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="b9db0-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="b9db0-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="b9db0-120">Das Standardfehlergerät.</span><span class="sxs-lookup"><span data-stu-id="b9db0-120">The standard error device.</span></span> <span data-ttu-id="b9db0-121">Anfänglich ist dies der aktive Konsolenbildschirmpuffer, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="b9db0-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="b9db0-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b9db0-122">Return value</span></span>

<span data-ttu-id="b9db0-123">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für das angegebene Gerät oder ein umgeleitetes Handle, das durch einen vorhergehenden Aufruf von [**SetStdHandle**](setstdhandle.md) festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="b9db0-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="b9db0-124">Das Handle verfügt über die Zugriffsrechte **GENERIC\_READ** und **GENERIC\_WRITE**, es sei denn, die Anwendung hat **SetStdHandle** verwendet, um ein Standardhandle mit geringeren Zugriffsrechten festzulegen.</span><span class="sxs-lookup"><span data-stu-id="b9db0-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="b9db0-125">Wenn bei der Ausführung der Funktion ein Fehler auftritt, lautet der Rückgabewert **INVALID\_HANDLE\_VALUE**.</span><span class="sxs-lookup"><span data-stu-id="b9db0-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="b9db0-126">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="b9db0-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

<span data-ttu-id="b9db0-127">Wenn eine Anwendung nicht über zugeordnete Standardhandles verfügt, wie etwa ein Dienst, der auf einem interaktiven Desktop ausgeführt wird und diese nicht umgeleitet hat, ist der Rückgabewert **NULL**.</span><span class="sxs-lookup"><span data-stu-id="b9db0-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9db0-128">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="b9db0-128">Remarks</span></span>

<span data-ttu-id="b9db0-129">Von **GetStdHandle** zurückgegebene Handles können von Anwendungen verwendet werden, die aus der Konsole lesen oder in die Konsole schreiben müssen.</span><span class="sxs-lookup"><span data-stu-id="b9db0-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="b9db0-130">Beim Erstellen einer Konsole ist das Standardeingabehandle ein Handle für den Eingabepuffer der Konsole, und die Standardausgabe- und Standardfehlerhandles sind Handles für den aktiven Bildschirmpuffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="b9db0-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="b9db0-131">Diese Handles können von den Funktionen [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) und [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) oder von jeder Konsolenfunktion verwendet werden, die auf den Konsoleneingabepuffer oder einen Bildschirmpuffer zugreift (beispielsweise die Funktionen [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) oder [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)).</span><span class="sxs-lookup"><span data-stu-id="b9db0-131">These handles can be used by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="b9db0-132">Die Standardhandles eines Prozesses können durch einen Aufruf von [**SetStdHandle**](setstdhandle.md) umgeleitet werden. In diesem Fall gibt **GetStdHandle** das umgeleitete Handle zurück.</span><span class="sxs-lookup"><span data-stu-id="b9db0-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="b9db0-133">Wenn die Standardhandles umgeleitet wurden, können Sie den `CONIN$`-Wert in einem Aufruf der Funktion [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) angeben, um ein Handle zum Eingabespeicher einer Konsole abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b9db0-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="b9db0-134">In ähnlicher Weise können Sie den `CONOUT$`-Wert angeben, um ein Handle für den aktiven Bildschirmpuffer einer Konsole abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b9db0-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="b9db0-135">Die Standardhandles eines Prozesses beim Eintritt in die main-Methode werden durch die Konfiguration des [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem)-Flags vorgeschrieben, das dem Linker zum Zeitpunkt des Erstellens der Anwendung übergeben wurde.</span><span class="sxs-lookup"><span data-stu-id="b9db0-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="b9db0-136">Für die Angabe von **/SUBSYSTEM:CONSOLE** ist es erforderlich, dass das Betriebssystem die Handles beim Start mit einer Konsolensitzung füllt, falls die Tabelle der Standardhandles nicht bereits mithilfe von Vererbung durch das übergeordnete Element aufgefüllt wurde.</span><span class="sxs-lookup"><span data-stu-id="b9db0-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="b9db0-137">Im Gegensatz dazu impliziert **/SUBSYSTEM:WINDOWS**, dass die Anwendung keine Konsole benötigt und von den Standardhandles wahrscheinlich keinen Gebrauch machen wird.</span><span class="sxs-lookup"><span data-stu-id="b9db0-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="b9db0-138">Weitere Informationen zur Handlevererbung finden Sie in der Dokumentation zu [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span><span class="sxs-lookup"><span data-stu-id="b9db0-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="b9db0-139">Einige Anwendungen werden außerhalb der Grenzen ihres deklarierten Subsystems betrieben; beispielsweise kann eine **/SUBSYSTEM:WINDOWS**-Anwendung die Standardhandles zu Protokollierungs- oder Debuggingzwecken überprüfen/verwenden, aber zugleich normal mit einer grafischen Benutzeroberfläche ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b9db0-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="b9db0-140">Diese Anwendungen müssen den Zustand von Standardhandles beim Start sorgfältig überprüfen und [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md) sowie [**FreeConsole**](freeconsole.md) verwenden, um bei Bedarf eine Konsole hinzuzufügen bzw. zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="b9db0-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="b9db0-141">Einige Anwendungen können sogar ihr Verhalten je nach dem Typ des geerbten Handles ändern.</span><span class="sxs-lookup"><span data-stu-id="b9db0-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="b9db0-142">Die Unterscheidung des Typs zwischen Konsole, Pipe, Datei und anderen kann mithilfe von [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype) durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b9db0-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="b9db0-143">Verhalten beim Zuordnen/Trennen</span><span class="sxs-lookup"><span data-stu-id="b9db0-143">Attach/detach behavior</span></span>

<span data-ttu-id="b9db0-144">Beim Zuordnen zu einer neuen Konsole werden Standardhandles immer durch Konsolenhandles ersetzt, es sei denn, während der Prozesserstellung wurde **STARTF\_USESTDHANDLES** angegeben.</span><span class="sxs-lookup"><span data-stu-id="b9db0-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="b9db0-145">Wenn der vorhandene Wert des Standardhandles **NULL** ist oder der vorhandene Wert des Standardhandles wie ein Konsolen-Pseudohandle aussieht, wird das Handle durch ein Konsolenhandle ersetzt.</span><span class="sxs-lookup"><span data-stu-id="b9db0-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="b9db0-146">Wenn ein übergeordnetes Element sowohl **CREATE\_NEW\_CONSOLE** als auch **STARTF\_USESTDHANDLES** verwendet, um einen Konsolenprozess zu erstellen, werden Standardhandles nicht ersetzt, es sei denn, der vorhandene Wert des Standardhandles ist **NULL**, oder es handelt sich um ein Konsolen-Pseudohandle.</span><span class="sxs-lookup"><span data-stu-id="b9db0-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="b9db0-147">Konsolenprozesse *müssen* mit gefüllten Standardhandles gestartet werden, sonst werden sie automatisch mit passenden Handles für eine neue Konsole gefüllt.</span><span class="sxs-lookup"><span data-stu-id="b9db0-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="b9db0-148">GUI-Anwendungen (Anwendungen mit grafischer Benutzeroberfläche) können ohne die Standardhandles gestartet werden, und sie werden nicht automatisch gefüllt.</span><span class="sxs-lookup"><span data-stu-id="b9db0-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="b9db0-149">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b9db0-149">Examples</span></span>

<span data-ttu-id="b9db0-150">Ein Beispiel finden Sie unter [Lesen von Eingabepufferereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="b9db0-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b9db0-151">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b9db0-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b9db0-152">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b9db0-152">Minimum supported client</span></span> | <span data-ttu-id="b9db0-153">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="b9db0-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b9db0-154">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b9db0-154">Minimum supported server</span></span> | <span data-ttu-id="b9db0-155">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="b9db0-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b9db0-156">Header</span><span class="sxs-lookup"><span data-stu-id="b9db0-156">Header</span></span> | <span data-ttu-id="b9db0-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span><span class="sxs-lookup"><span data-stu-id="b9db0-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="b9db0-158">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="b9db0-158">Library</span></span> | <span data-ttu-id="b9db0-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b9db0-159">Kernel32.lib</span></span> |
| <span data-ttu-id="b9db0-160">DLL</span><span class="sxs-lookup"><span data-stu-id="b9db0-160">DLL</span></span> | <span data-ttu-id="b9db0-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b9db0-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b9db0-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b9db0-162">See also</span></span>

[<span data-ttu-id="b9db0-163">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b9db0-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b9db0-164">Konsolenhandles</span><span class="sxs-lookup"><span data-stu-id="b9db0-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="b9db0-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="b9db0-165">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="b9db0-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="b9db0-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="b9db0-167">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b9db0-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="b9db0-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="b9db0-168">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="b9db0-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="b9db0-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="b9db0-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="b9db0-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="b9db0-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="b9db0-171">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)