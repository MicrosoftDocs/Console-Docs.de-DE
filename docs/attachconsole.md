---
title: Attachconsole-Funktion
description: Siehe Referenzinformationen über die attachconsole-Funktion, die den aufrufenden Prozess an die Konsole des angegebenen Prozesses anfügt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a1be050dccc0c77b6ad448cc45e87906a115d82c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357840"
---
# <a name="attachconsole-function"></a><span data-ttu-id="3b1d3-104">Attachconsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="3b1d3-104">AttachConsole function</span></span>

<span data-ttu-id="3b1d3-105">Fügt den aufrufenden Prozess an die Konsole des angegebenen Prozesses als Client Anwendung an.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-105">Attaches the calling process to the console of the specified process as a client application.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b1d3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b1d3-106">Syntax</span></span>

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a><span data-ttu-id="3b1d3-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="3b1d3-107">Parameters</span></span>

<span data-ttu-id="3b1d3-108">*dwProcessId* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="3b1d3-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="3b1d3-109">Der Bezeichner des Prozesses, dessen-Konsole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="3b1d3-110">Dieser Parameter kann einen der folgenden Werte annehmen.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="3b1d3-111">Wert</span><span class="sxs-lookup"><span data-stu-id="3b1d3-111">Value</span></span> | <span data-ttu-id="3b1d3-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="3b1d3-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="3b1d3-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="3b1d3-113">*pid*</span></span> | <span data-ttu-id="3b1d3-114">Verwenden Sie die Konsole des angegebenen Prozesses.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-114">Use the console of the specified process.</span></span> |
| <span data-ttu-id="3b1d3-115">**Anfügen \_ übergeordneter \_ Prozess**`(DWORD)-1`</span><span class="sxs-lookup"><span data-stu-id="3b1d3-115">**ATTACH\_PARENT\_PROCESS** `(DWORD)-1`</span></span> | <span data-ttu-id="3b1d3-116">Verwenden Sie die Konsole des übergeordneten Elements des aktuellen Prozesses.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-116">Use the console of the parent of the current process.</span></span> |

## <a name="return-value"></a><span data-ttu-id="3b1d3-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3b1d3-117">Return value</span></span>

<span data-ttu-id="3b1d3-118">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3b1d3-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3b1d3-120">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="3b1d3-121">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="3b1d3-121">Remarks</span></span>

<span data-ttu-id="3b1d3-122">Ein Prozess kann höchstens an eine Konsole angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="3b1d3-123">Wenn der Aufrufprozess bereits an eine Konsole angefügt ist, lautet der zurückgegebene Fehlercode **Error \_ Access \_ denied** ( `5` ).</span><span class="sxs-lookup"><span data-stu-id="3b1d3-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (`5`).</span></span> <span data-ttu-id="3b1d3-124">Wenn der angegebene Prozess über keine Konsole verfügt, wird der zurückgegebene Fehlercode **als \_ ungültiges \_ handle** () zurückgegeben `6` .</span><span class="sxs-lookup"><span data-stu-id="3b1d3-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (`6`).</span></span> <span data-ttu-id="3b1d3-125">Wenn der angegebene Prozess nicht vorhanden ist, wird der Fehlercode " **\_ ungültiger \_ Parameter** ()" zurückgegeben `87` .</span><span class="sxs-lookup"><span data-stu-id="3b1d3-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (`87`).</span></span>

<span data-ttu-id="3b1d3-126">Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von seiner Konsole zu trennen.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="3b1d3-127">Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="3b1d3-128">Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder **freeconsole** aufruft.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="3b1d3-129">Nachdem ein Prozess **freeconsole** aufgerufen hat, kann er die Funktion " [**Zuweisung**](allocconsole.md) " aufrufen, um eine neue Konsole **oder eine** anfügekonsole zum Anfügen an eine andere Konsole zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="3b1d3-130">Diese Funktion ist in erster Linie für Anwendungen nützlich, die mit [**/Subsystem: Windows**](/cpp/build/reference/subsystem-specify-subsystem)verknüpft waren, was dem Betriebssystem impliziert, dass eine Konsole nicht benötigt wird, bevor die Hauptmethode des Programms eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-130">This function is primarily useful to applications that were linked with [**/SUBSYSTEM:WINDOWS**](/cpp/build/reference/subsystem-specify-subsystem), which implies to the operating system that a console is not needed before entering the program's main method.</span></span> <span data-ttu-id="3b1d3-131">In dieser Instanz sind die Standard Handles, die mit [**getstdhandle**](getstdhandle.md) abgerufen werden, beim Start wahrscheinlich ungültig, bis **attachconsole** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-131">In that instance, the standard handles retrieved with [**GetStdHandle**](getstdhandle.md) will likely be invalid on startup until **AttachConsole** is called.</span></span> <span data-ttu-id="3b1d3-132">Eine Ausnahme besteht darin, dass die Anwendung mit der Handle-Vererbung durch ihren übergeordneten Prozess gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-132">The exception to this is if the application is launched with handle inheritance by its parent process.</span></span>

<span data-ttu-id="3b1d3-133">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als `0x0501` oder höher.</span><span class="sxs-lookup"><span data-stu-id="3b1d3-133">To compile an application that uses this function, define **\_WIN32\_WINNT** as `0x0501` or later.</span></span> <span data-ttu-id="3b1d3-134">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="3b1d3-134">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

## <a name="requirements"></a><span data-ttu-id="3b1d3-135">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="3b1d3-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3b1d3-136">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="3b1d3-136">Minimum supported client</span></span> | <span data-ttu-id="3b1d3-137">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="3b1d3-137">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="3b1d3-138">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="3b1d3-138">Minimum supported server</span></span> | <span data-ttu-id="3b1d3-139">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="3b1d3-139">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="3b1d3-140">Header</span><span class="sxs-lookup"><span data-stu-id="3b1d3-140">Header</span></span> | <span data-ttu-id="3b1d3-141">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="3b1d3-141">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3b1d3-142">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="3b1d3-142">Library</span></span> | <span data-ttu-id="3b1d3-143">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="3b1d3-143">Kernel32.lib</span></span> |
| <span data-ttu-id="3b1d3-144">DLL</span><span class="sxs-lookup"><span data-stu-id="3b1d3-144">DLL</span></span> | <span data-ttu-id="3b1d3-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3b1d3-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="3b1d3-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3b1d3-146">See also</span></span>

[<span data-ttu-id="3b1d3-147">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="3b1d3-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3b1d3-148">Konsolen</span><span class="sxs-lookup"><span data-stu-id="3b1d3-148">Consoles</span></span>](consoles.md)

[<span data-ttu-id="3b1d3-149">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="3b1d3-149">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="3b1d3-150">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="3b1d3-150">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="3b1d3-151">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="3b1d3-151">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)