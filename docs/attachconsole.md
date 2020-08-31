---
title: Attachconsole-Funktion
description: Siehe Referenzinformationen über die attachconsole-Funktion, die den aufrufenden Prozess an die Konsole des angegebenen Prozesses anfügt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060234"
---
# <a name="attachconsole-function"></a><span data-ttu-id="b36ab-104">Attachconsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="b36ab-104">AttachConsole function</span></span>


<span data-ttu-id="b36ab-105">Fügt den aufrufenden Prozess an die Konsole des angegebenen Prozesses an.</span><span class="sxs-lookup"><span data-stu-id="b36ab-105">Attaches the calling process to the console of the specified process.</span></span>

<a name="syntax"></a><span data-ttu-id="b36ab-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b36ab-106">Syntax</span></span>
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a><span data-ttu-id="b36ab-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="b36ab-107">Parameters</span></span>
----------

<span data-ttu-id="b36ab-108">*dwProcessId* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b36ab-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="b36ab-109">Der Bezeichner des Prozesses, dessen-Konsole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b36ab-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="b36ab-110">Dieser Parameter kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="b36ab-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="b36ab-111">Wert</span><span class="sxs-lookup"><span data-stu-id="b36ab-111">Value</span></span></th>
<th><span data-ttu-id="b36ab-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="b36ab-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="b36ab-113"><em>pid</em></span><span class="sxs-lookup"><span data-stu-id="b36ab-113"><em>pid</em></span></span></td>
<td><p><span data-ttu-id="b36ab-114">Verwenden Sie die Konsole des angegebenen Prozesses.</span><span class="sxs-lookup"><span data-stu-id="b36ab-114">Use the console of the specified process.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="b36ab-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span><span class="sxs-lookup"><span data-stu-id="b36ab-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span></span></td>
<td><p><span data-ttu-id="b36ab-116">Verwenden Sie die Konsole des übergeordneten Elements des aktuellen Prozesses.</span><span class="sxs-lookup"><span data-stu-id="b36ab-116">Use the console of the parent of the current process.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="b36ab-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b36ab-117">Return value</span></span>
------------

<span data-ttu-id="b36ab-118">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="b36ab-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b36ab-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="b36ab-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b36ab-120">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b36ab-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b36ab-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b36ab-121">Remarks</span></span>
-------

<span data-ttu-id="b36ab-122">Ein Prozess kann höchstens an eine Konsole angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="b36ab-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="b36ab-123">Wenn der Aufrufprozess bereits an eine Konsole angefügt ist, lautet der zurückgegebene Fehlercode **Error \_ Access \_ denied** (5).</span><span class="sxs-lookup"><span data-stu-id="b36ab-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (5).</span></span> <span data-ttu-id="b36ab-124">Wenn der angegebene Prozess über keine Konsole verfügt, wird der zurückgegebene Fehlercode \*\* \_ mit einem ungültigen \_ handle\*\* (6) zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b36ab-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (6).</span></span> <span data-ttu-id="b36ab-125">Wenn der angegebene Prozess nicht vorhanden ist, lautet der zurückgegebene Fehlercode " \*\* \_ ungültiger \_ Parameter\*\* " (87).</span><span class="sxs-lookup"><span data-stu-id="b36ab-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="b36ab-126">Ein Prozess kann die [**freeconsole**](freeconsole.md) -Funktion verwenden, um sich von seiner Konsole zu trennen.</span><span class="sxs-lookup"><span data-stu-id="b36ab-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="b36ab-127">Wenn andere Prozesse die-Konsole gemeinsam nutzen, wird die Konsole nicht zerstört, aber der Prozess, der **freeconsole** aufgerufen hat, kann nicht darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="b36ab-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="b36ab-128">Eine Konsole wird geschlossen, wenn der letzte daran angefügte Prozess beendet wird oder **freeconsole**aufruft.</span><span class="sxs-lookup"><span data-stu-id="b36ab-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="b36ab-129">Nachdem ein Prozess **freeconsole**aufgerufen hat, kann er die Funktion " [**Zuweisung**](allocconsole.md) " aufrufen, um eine neue Konsole **oder eine** anfügekonsole zum Anfügen an eine andere Konsole zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b36ab-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="b36ab-130">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="b36ab-130">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="b36ab-131">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="b36ab-131">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="b36ab-132">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b36ab-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b36ab-133">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b36ab-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b36ab-134">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b36ab-134">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b36ab-135">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b36ab-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b36ab-136">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b36ab-136">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b36ab-137">Header</span><span class="sxs-lookup"><span data-stu-id="b36ab-137">Header</span></span></p></td>
<td><span data-ttu-id="b36ab-138">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b36ab-138">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b36ab-139">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="b36ab-139">Library</span></span></p></td>
<td><span data-ttu-id="b36ab-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b36ab-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b36ab-141">DLL</span><span class="sxs-lookup"><span data-stu-id="b36ab-141">DLL</span></span></p></td>
<td><span data-ttu-id="b36ab-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b36ab-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b36ab-143"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b36ab-143"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b36ab-144">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b36ab-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b36ab-145">Trö</span><span class="sxs-lookup"><span data-stu-id="b36ab-145">Consoles</span></span>](consoles.md)

[<span data-ttu-id="b36ab-146">**"Zuweisung"-Konsole**</span><span class="sxs-lookup"><span data-stu-id="b36ab-146">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="b36ab-147">**Freeconsole**</span><span class="sxs-lookup"><span data-stu-id="b36ab-147">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="b36ab-148">**Getconsoleprocesslist**</span><span class="sxs-lookup"><span data-stu-id="b36ab-148">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)

 

 




