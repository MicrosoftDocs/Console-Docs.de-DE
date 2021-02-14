---
title: Generateconsolectrlevent-Funktion
description: Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4002ec67000edda38c7b14476528a0167e521bbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357530"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="c7740-104">Generateconsolectrlevent-Funktion</span><span class="sxs-lookup"><span data-stu-id="c7740-104">GenerateConsoleCtrlEvent function</span></span>

<span data-ttu-id="c7740-105">Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt.</span><span class="sxs-lookup"><span data-stu-id="c7740-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7740-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7740-106">Syntax</span></span>

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a><span data-ttu-id="c7740-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c7740-107">Parameters</span></span>

<span data-ttu-id="c7740-108">*dwctrlevent* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c7740-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="c7740-109">Der Typ des zu generierenden Signals.</span><span class="sxs-lookup"><span data-stu-id="c7740-109">The type of signal to be generated.</span></span> <span data-ttu-id="c7740-110">Dieser Parameter kann einen der folgenden Werte annehmen.</span><span class="sxs-lookup"><span data-stu-id="c7740-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="c7740-111">Wert</span><span class="sxs-lookup"><span data-stu-id="c7740-111">Value</span></span> | <span data-ttu-id="c7740-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="c7740-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="c7740-113">**CTRL_C_EVENT** 0</span><span class="sxs-lookup"><span data-stu-id="c7740-113">**CTRL_C_EVENT** 0</span></span> | <span data-ttu-id="c7740-114">Generiert ein STRG + C-Signal.</span><span class="sxs-lookup"><span data-stu-id="c7740-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="c7740-115">Dieses Signal kann nicht für Prozessgruppen generiert werden.</span><span class="sxs-lookup"><span data-stu-id="c7740-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="c7740-116">Wenn *dwprocessgroupid* ungleich NULL ist, wird diese Funktion erfolgreich ausgeführt, aber das STRG + C-Signal wird nicht von Prozessen innerhalb der angegebenen Prozessgruppe empfangen.</span><span class="sxs-lookup"><span data-stu-id="c7740-116">If *dwProcessGroupId* is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span> |
| <span data-ttu-id="c7740-117">**CTRL_BREAK_EVENT** 1</span><span class="sxs-lookup"><span data-stu-id="c7740-117">**CTRL_BREAK_EVENT** 1</span></span> | <span data-ttu-id="c7740-118">Generiert ein STRG + UNTBR-Signal.</span><span class="sxs-lookup"><span data-stu-id="c7740-118">Generates a CTRL+BREAK signal.</span></span> |

<span data-ttu-id="c7740-119">*dwprocessgroupid* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="c7740-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="c7740-120">Der Bezeichner der Prozessgruppe, für die das Signal empfangen werden soll.</span><span class="sxs-lookup"><span data-stu-id="c7740-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="c7740-121">Eine Prozessgruppe wird erstellt, wenn das Flag " **\_ neue \_ Prozess \_ Gruppe erstellen** " in einem Aufrufen der Funktion " [**deateprocess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) " angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c7740-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function.</span></span> <span data-ttu-id="c7740-122">Der Prozess Bezeichner des neuen Prozesses ist auch der Prozessgruppen Bezeichner einer neuen Prozessgruppe.</span><span class="sxs-lookup"><span data-stu-id="c7740-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="c7740-123">Die Prozessgruppe umfasst alle Prozesse, bei denen es sich um nachfolgende Elemente des Stamm Prozesses handelt.</span><span class="sxs-lookup"><span data-stu-id="c7740-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="c7740-124">Nur die Prozesse in der Gruppe, die dieselbe Konsole wie der aufrufende Prozess nutzen, erhalten das Signal.</span><span class="sxs-lookup"><span data-stu-id="c7740-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="c7740-125">Anders ausgedrückt: Wenn ein Prozess in der Gruppe eine neue Konsole erstellt, empfängt dieser Prozess weder das Signal noch seine Nachfolger.</span><span class="sxs-lookup"><span data-stu-id="c7740-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="c7740-126">Wenn dieser Parameter 0 (null) ist, wird das Signal in allen Prozessen generiert, die die Konsole des aufrufenden Prozesses gemeinsam verwenden.</span><span class="sxs-lookup"><span data-stu-id="c7740-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7740-127">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c7740-127">Return value</span></span>

<span data-ttu-id="c7740-128">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="c7740-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c7740-129">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="c7740-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c7740-130">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="c7740-130">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c7740-131">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="c7740-131">Remarks</span></span>

<span data-ttu-id="c7740-132">**Generateconsolectrlevent** bewirkt, dass die Handlerfunktionen der Prozesse in der Zielgruppe aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="c7740-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="c7740-133">Alle Konsolen Prozesse verfügen über eine Standardhandlerfunktion, die die [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) -Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="c7740-133">All console processes have a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="c7740-134">Ein Konsolen Prozess kann die [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion verwenden, um andere Handlerfunktionen zu installieren oder zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="c7740-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="c7740-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) kann auch ein Vererb bares Attribut aktivieren, das bewirkt, dass der aufrufende Prozess STRG + C-Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="c7740-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="c7740-136">Wenn **generateconsolectrlevent** ein STRG + C-Signal an einen Prozess sendet, für den dieses Attribut aktiviert ist, werden die Handlerfunktionen für diesen Prozess nicht aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="c7740-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="c7740-137">STRG + untbugsignale bewirken immer, dass die Handlerfunktionen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="c7740-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7740-138">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c7740-138">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c7740-139">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="c7740-139">Minimum supported client</span></span> | <span data-ttu-id="c7740-140">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c7740-140">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c7740-141">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="c7740-141">Minimum supported server</span></span> | <span data-ttu-id="c7740-142">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="c7740-142">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c7740-143">Header</span><span class="sxs-lookup"><span data-stu-id="c7740-143">Header</span></span> | <span data-ttu-id="c7740-144">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c7740-144">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c7740-145">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="c7740-145">Library</span></span> | <span data-ttu-id="c7740-146">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c7740-146">Kernel32.lib</span></span> |
| <span data-ttu-id="c7740-147">DLL</span><span class="sxs-lookup"><span data-stu-id="c7740-147">DLL</span></span> | <span data-ttu-id="c7740-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c7740-148">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c7740-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c7740-149">See also</span></span>

[<span data-ttu-id="c7740-150">Konsolen-Bearbeitungssteuerelemente</span><span class="sxs-lookup"><span data-stu-id="c7740-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="c7740-151">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="c7740-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c7740-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="c7740-152">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="c7740-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="c7740-153">**ExitProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[<span data-ttu-id="c7740-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="c7740-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)