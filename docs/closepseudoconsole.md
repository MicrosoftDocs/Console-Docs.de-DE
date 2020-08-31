---
title: Closepseudoconsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur closepseudoconsole-Funktion, die eine Pseudo Console aus dem angegebenen Handle schließt.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060179"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="96ac1-104">Closepseudoconsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="96ac1-104">ClosePseudoConsole function</span></span>


<span data-ttu-id="96ac1-105">Schließt eine pseudoconsole aus dem angegebenen Handle.</span><span class="sxs-lookup"><span data-stu-id="96ac1-105">Closes a pseudoconsole from the given handle.</span></span>

<a name="syntax"></a><span data-ttu-id="96ac1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="96ac1-106">Syntax</span></span>
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a><span data-ttu-id="96ac1-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="96ac1-107">Parameters</span></span>
----------

<span data-ttu-id="96ac1-108">*HPC* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="96ac1-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="96ac1-109">Ein Handle für eine aktive psuedoconsole, wie von " [deepseudoconsole](createpseudoconsole.md)" geöffnet.</span><span class="sxs-lookup"><span data-stu-id="96ac1-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<a name="return-value"></a><span data-ttu-id="96ac1-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="96ac1-110">Return value</span></span>
------------

<span data-ttu-id="96ac1-111">*keine*</span><span class="sxs-lookup"><span data-stu-id="96ac1-111">*none*</span></span>

<a name="remarks"></a><span data-ttu-id="96ac1-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="96ac1-112">Remarks</span></span>
-------

<span data-ttu-id="96ac1-113">Wenn Sie eine Pseudo Konsole schließen, werden auch Client Anwendungen beendet, die an die Sitzung angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="96ac1-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="96ac1-114">`hOutput`Wenn diese API aufgerufen wird, kann von der pseudoconsole ein abschließender gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="96ac1-114">A final painted frame may arrive on `hOutput` from the pseudoconsole when this API is called.</span></span> <span data-ttu-id="96ac1-115">Es wird erwartet, dass der Aufrufer diese Informationen aus dem Kommunikationskanal Puffer abfließt und ihn entweder vornimmt oder verwerfen kann.</span><span class="sxs-lookup"><span data-stu-id="96ac1-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="96ac1-116">Wenn der Puffer nicht entladen wird, kann es passieren, dass der Close-Befehl unbegrenzt wartet, bis er entladen wird oder die Kommunikationskanäle anders voneinander getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="96ac1-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

<a name="requirements"></a><span data-ttu-id="96ac1-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="96ac1-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="96ac1-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="96ac1-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="96ac1-119">Windows 10 1809 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="96ac1-119">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96ac1-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="96ac1-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="96ac1-121">Windows Server 2019 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="96ac1-121">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96ac1-122">Header</span><span class="sxs-lookup"><span data-stu-id="96ac1-122">Header</span></span></p></td>
<td><span data-ttu-id="96ac1-123">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="96ac1-123">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="96ac1-124">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="96ac1-124">Library</span></span></p></td>
<td><span data-ttu-id="96ac1-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="96ac1-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="96ac1-126">DLL</span><span class="sxs-lookup"><span data-stu-id="96ac1-126">DLL</span></span></p></td>
<td><span data-ttu-id="96ac1-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="96ac1-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="96ac1-128"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="96ac1-128"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="96ac1-129">Pseudo Konsolen</span><span class="sxs-lookup"><span data-stu-id="96ac1-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="96ac1-130">**"Kreatepseudoconsole"**</span><span class="sxs-lookup"><span data-stu-id="96ac1-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="96ac1-131">**Resizepseudoconsole**</span><span class="sxs-lookup"><span data-stu-id="96ac1-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
