---
title: Getconsoleprocesslist-Funktion
description: Siehe Referenzinformationen zur getconsoleprocesslist-Funktion, die eine Liste der Prozesse abruft, die an die aktuelle Konsole angefügt sind.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b032754172886fd83a8152caeb5e2228b917930
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059778"
---
# <a name="getconsoleprocesslist-function"></a><span data-ttu-id="2d2c4-104">Getconsoleprocesslist-Funktion</span><span class="sxs-lookup"><span data-stu-id="2d2c4-104">GetConsoleProcessList function</span></span>


<span data-ttu-id="2d2c4-105">Ruft eine Liste der Prozesse ab, die an die aktuelle Konsole angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-105">Retrieves a list of the processes attached to the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="2d2c4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2d2c4-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

<a name="parameters"></a><span data-ttu-id="2d2c4-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="2d2c4-107">Parameters</span></span>
----------

<span data-ttu-id="2d2c4-108">*lpdwprocesslist* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="2d2c4-108">*lpdwProcessList* \[out\]</span></span>  
<span data-ttu-id="2d2c4-109">Ein Zeiger auf einen Puffer, der bei erfolgreicher Ausführung ein Array von Prozess Bezeichners empfängt.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-109">A pointer to a buffer that receives an array of process identifiers upon success.</span></span> <span data-ttu-id="2d2c4-110">Dies muss ein gültiger Puffer sein und darf nicht sein `NULL` .</span><span class="sxs-lookup"><span data-stu-id="2d2c4-110">This must be a valid buffer and cannot be `NULL`.</span></span> <span data-ttu-id="2d2c4-111">Der Puffer muss über Speicherplatz verfügen, um mindestens eine zurückgegebene Prozess-ID zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-111">The buffer must have space to receive at least 1 returned process id.</span></span>

<span data-ttu-id="2d2c4-112">*dwprocesscount* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="2d2c4-112">*dwProcessCount* \[in\]</span></span>  
<span data-ttu-id="2d2c4-113">Die maximale Anzahl von Prozess bezeichern, die im *lpdwprocesslist* -Puffer gespeichert werden können.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-113">The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer.</span></span> <span data-ttu-id="2d2c4-114">Dieser Wert muss größer als 0 sein.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-114">This must be greater than 0.</span></span>

<a name="return-value"></a><span data-ttu-id="2d2c4-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="2d2c4-115">Return value</span></span>
------------

<span data-ttu-id="2d2c4-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert kleiner oder gleich *dwprocesscount* und stellt die Anzahl der Prozess-IDs dar, die im *lpdwprocesslist* -Puffer gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-116">If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.</span></span>

<span data-ttu-id="2d2c4-117">Wenn der Puffer zu klein ist, um alle gültigen Prozess-IDs aufzunehmen, ist der Rückgabewert die erforderliche Anzahl von Array Elementen.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-117">If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements.</span></span> <span data-ttu-id="2d2c4-118">Die Funktion hat keine Bezeichner im Puffer gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-118">The function will have stored no identifiers in the buffer.</span></span> <span data-ttu-id="2d2c4-119">Verwenden Sie in dieser Situation den Rückgabewert, um einen Puffer zuzuordnen, der groß genug ist, um die gesamte Liste zu speichern und die Funktion erneut aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-119">In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.</span></span>

<span data-ttu-id="2d2c4-120">Wenn der Rückgabewert 0 (null) ist, ist bei der Funktion ein Fehler aufgetreten, da jeder Konsole mindestens ein Prozess zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-120">If the return value is zero, the function has failed, because every console has at least one process associated with it.</span></span> <span data-ttu-id="2d2c4-121">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2d2c4-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="2d2c4-122">Wenn eine `NULL` Prozessliste bereitgestellt wurde oder die Prozess Anzahl 0 war, gibt der-Befehl 0 zurück und `GetLastError` gibt zurück `ERROR_INVALID_PARAMETER` .</span><span class="sxs-lookup"><span data-stu-id="2d2c4-122">If a `NULL` process list was provided or the process count was 0, the call will return 0 and `GetLastError` will return `ERROR_INVALID_PARAMETER`.</span></span> <span data-ttu-id="2d2c4-123">Geben Sie einen Puffer mit mindestens einem-Element an, um diese Funktion aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-123">Please provide a buffer of at least one element to call this function.</span></span> <span data-ttu-id="2d2c4-124">Weisen Sie einen größeren Puffer zu, und wiederholen Sie den Vorgang, wenn der Rückgabecode größer als die Länge des bereitgestellten Puffers ist.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-124">Allocate a larger buffer and call again if the return code is larger than the length of the provided buffer.</span></span>

<a name="remarks"></a><span data-ttu-id="2d2c4-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2d2c4-125">Remarks</span></span>
-------

<span data-ttu-id="2d2c4-126">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="2d2c4-126">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="2d2c4-127">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="2d2c4-127">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="2d2c4-128">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="2d2c4-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2d2c4-129">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="2d2c4-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2d2c4-130">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="2d2c4-130">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2d2c4-131">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="2d2c4-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2d2c4-132">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="2d2c4-132">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2d2c4-133">Header</span><span class="sxs-lookup"><span data-stu-id="2d2c4-133">Header</span></span></p></td>
<td><span data-ttu-id="2d2c4-134">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2d2c4-134">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2d2c4-135">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="2d2c4-135">Library</span></span></p></td>
<td><span data-ttu-id="2d2c4-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2d2c4-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2d2c4-137">DLL</span><span class="sxs-lookup"><span data-stu-id="2d2c4-137">DLL</span></span></p></td>
<td><span data-ttu-id="2d2c4-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2d2c4-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2d2c4-139"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2d2c4-139"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2d2c4-140">**Attachconsole**</span><span class="sxs-lookup"><span data-stu-id="2d2c4-140">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="2d2c4-141">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="2d2c4-141">Console Functions</span></span>](console-functions.md)

 

 




