---
title: Generateconsolectrlevent-Funktion
description: Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 31c0330a002362542a799ab7e038d3f65497ded3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059859"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="a32df-104">Generateconsolectrlevent-Funktion</span><span class="sxs-lookup"><span data-stu-id="a32df-104">GenerateConsoleCtrlEvent function</span></span>


<span data-ttu-id="a32df-105">Sendet ein angegebenes Signal an eine Konsolen Prozessgruppe, die die dem aufrufenden Prozess zugeordnete Konsole freigibt.</span><span class="sxs-lookup"><span data-stu-id="a32df-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="a32df-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a32df-106">Syntax</span></span>
------

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

<a name="parameters"></a><span data-ttu-id="a32df-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="a32df-107">Parameters</span></span>
----------

<span data-ttu-id="a32df-108">*dwctrlevent* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a32df-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="a32df-109">Der Typ des zu generierenden Signals.</span><span class="sxs-lookup"><span data-stu-id="a32df-109">The type of signal to be generated.</span></span> <span data-ttu-id="a32df-110">Dieser Parameter kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="a32df-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="a32df-111">Wert</span><span class="sxs-lookup"><span data-stu-id="a32df-111">Value</span></span></th>
<th><span data-ttu-id="a32df-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="a32df-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="a32df-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span><span class="sxs-lookup"><span data-stu-id="a32df-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span></span></td>
<td><p><span data-ttu-id="a32df-114">Generiert ein STRG + C-Signal.</span><span class="sxs-lookup"><span data-stu-id="a32df-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="a32df-115">Dieses Signal kann nicht für Prozessgruppen generiert werden.</span><span class="sxs-lookup"><span data-stu-id="a32df-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="a32df-116">Wenn <em>dwprocessgroupid</em> ungleich NULL ist, wird diese Funktion erfolgreich ausgeführt, aber das STRG + C-Signal wird nicht von Prozessen innerhalb der angegebenen Prozessgruppe empfangen.</span><span class="sxs-lookup"><span data-stu-id="a32df-116">If <em>dwProcessGroupId</em> is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a32df-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span><span class="sxs-lookup"><span data-stu-id="a32df-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span></span></td>
<td><p><span data-ttu-id="a32df-118">Generiert ein STRG + UNTBR-Signal.</span><span class="sxs-lookup"><span data-stu-id="a32df-118">Generates a CTRL+BREAK signal.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="a32df-119">*dwprocessgroupid* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="a32df-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="a32df-120">Der Bezeichner der Prozessgruppe, für die das Signal empfangen werden soll.</span><span class="sxs-lookup"><span data-stu-id="a32df-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="a32df-121">Eine Prozessgruppe wird erstellt, wenn das Flag " \*\* \_ neue \_ Prozess \_ Gruppe erstellen\*\* " in einem Aufrufen der Funktion " [**deateprocess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) " angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a32df-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function.</span></span> <span data-ttu-id="a32df-122">Der Prozess Bezeichner des neuen Prozesses ist auch der Prozessgruppen Bezeichner einer neuen Prozessgruppe.</span><span class="sxs-lookup"><span data-stu-id="a32df-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="a32df-123">Die Prozessgruppe umfasst alle Prozesse, bei denen es sich um nachfolgende Elemente des Stamm Prozesses handelt.</span><span class="sxs-lookup"><span data-stu-id="a32df-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="a32df-124">Nur die Prozesse in der Gruppe, die dieselbe Konsole wie der aufrufende Prozess nutzen, erhalten das Signal.</span><span class="sxs-lookup"><span data-stu-id="a32df-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="a32df-125">Anders ausgedrückt: Wenn ein Prozess in der Gruppe eine neue Konsole erstellt, empfängt dieser Prozess weder das Signal noch seine Nachfolger.</span><span class="sxs-lookup"><span data-stu-id="a32df-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="a32df-126">Wenn dieser Parameter 0 (null) ist, wird das Signal in allen Prozessen generiert, die die Konsole des aufrufenden Prozesses gemeinsam verwenden.</span><span class="sxs-lookup"><span data-stu-id="a32df-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

<a name="return-value"></a><span data-ttu-id="a32df-127">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="a32df-127">Return value</span></span>
------------

<span data-ttu-id="a32df-128">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="a32df-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="a32df-129">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="a32df-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="a32df-130">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="a32df-130">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="a32df-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a32df-131">Remarks</span></span>
-------

<span data-ttu-id="a32df-132">**Generateconsolectrlevent** bewirkt, dass die Handlerfunktionen der Prozesse in der Zielgruppe aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="a32df-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="a32df-133">Alle Konsolen Prozesse verfügen über eine Standardhandlerfunktion, die die [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) -Funktion aufruft.</span><span class="sxs-lookup"><span data-stu-id="a32df-133">All console processes have a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="a32df-134">Ein Konsolen Prozess kann die [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) -Funktion verwenden, um andere Handlerfunktionen zu installieren oder zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="a32df-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="a32df-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) kann auch ein Vererb bares Attribut aktivieren, das bewirkt, dass der aufrufende Prozess STRG + C-Signale ignoriert.</span><span class="sxs-lookup"><span data-stu-id="a32df-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="a32df-136">Wenn **generateconsolectrlevent** ein STRG + C-Signal an einen Prozess sendet, für den dieses Attribut aktiviert ist, werden die Handlerfunktionen für diesen Prozess nicht aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="a32df-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="a32df-137">STRG + untbugsignale bewirken immer, dass die Handlerfunktionen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="a32df-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

<a name="requirements"></a><span data-ttu-id="a32df-138">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a32df-138">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a32df-139">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="a32df-139">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a32df-140">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="a32df-140">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a32df-141">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="a32df-141">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a32df-142">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="a32df-142">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a32df-143">Header</span><span class="sxs-lookup"><span data-stu-id="a32df-143">Header</span></span></p></td>
<td><span data-ttu-id="a32df-144">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a32df-144">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a32df-145">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="a32df-145">Library</span></span></p></td>
<td><span data-ttu-id="a32df-146">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="a32df-146">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a32df-147">DLL</span><span class="sxs-lookup"><span data-stu-id="a32df-147">DLL</span></span></p></td>
<td><span data-ttu-id="a32df-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a32df-148">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a32df-149"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a32df-149"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a32df-150">Konsolen Steuerungs Handler</span><span class="sxs-lookup"><span data-stu-id="a32df-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="a32df-151">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="a32df-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="a32df-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="a32df-152">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="a32df-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="a32df-153">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="a32df-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="a32df-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)

 

 




