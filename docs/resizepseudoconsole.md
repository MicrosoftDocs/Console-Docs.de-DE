---
title: Resizepseudoconsole-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur resizepseudoconsole-Funktion, die die Größe der internen Puffer für eine Pseudo Konsole auf die angegebene Größe anpasst.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API, Configuration Manager, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060347"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="feee7-104">Resizepseudoconsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="feee7-104">ResizePseudoConsole function</span></span>


<span data-ttu-id="feee7-105">Ändert die Größe der internen Puffer für eine pseudoconsole auf die angegebene Größe.</span><span class="sxs-lookup"><span data-stu-id="feee7-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

<a name="syntax"></a><span data-ttu-id="feee7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="feee7-106">Syntax</span></span>
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a><span data-ttu-id="feee7-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="feee7-107">Parameters</span></span>
----------

<span data-ttu-id="feee7-108">*HPC* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="feee7-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="feee7-109">Ein Handle für eine aktive psuedoconsole, wie von " [deepseudoconsole](createpseudoconsole.md)" geöffnet.</span><span class="sxs-lookup"><span data-stu-id="feee7-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="feee7-110">*Größe* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="feee7-110">*size* \[in\]</span></span>  
<span data-ttu-id="feee7-111">Die Abmessungen des Fensters/Puffers in der Anzahl von Zeichen, die für den internen Puffer dieser pseudoconsole verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="feee7-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span> 

<a name="return-value"></a><span data-ttu-id="feee7-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="feee7-112">Return value</span></span>
------------

<span data-ttu-id="feee7-113">Typ: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="feee7-113">Type: **HRESULT**</span></span>

<span data-ttu-id="feee7-114">Wenn diese Methode erfolgreich ausgeführt wird, wird **S_OK**zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="feee7-114">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="feee7-115">Andernfalls wird ein **HRESULT** -Fehlercode zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="feee7-115">Otherwise, it returns an **HRESULT** error code.</span></span>

<a name="remarks"></a><span data-ttu-id="feee7-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="feee7-116">Remarks</span></span>
-------

<span data-ttu-id="feee7-117">Diese Funktion kann die Größe der internen Puffer in der pseudoconsole-Sitzung ändern, sodass Sie der Fenster-/Puffergröße entspricht, die für die Anzeige am Terminal Ende verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="feee7-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="feee7-118">Dadurch wird sichergestellt, dass bei der Kommunikation mit den [Konsolenfunktionen](console-functions.md) angefügte Befehlszeilenschnittstelle (CUI) Anwendungen die richtigen Dimensionen in ihren Aufrufen zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="feee7-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

<a name="requirements"></a><span data-ttu-id="feee7-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="feee7-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="feee7-120">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="feee7-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="feee7-121">Windows 10 1809 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="feee7-121">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="feee7-122">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="feee7-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="feee7-123">Windows Server 2019 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="feee7-123">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="feee7-124">Header</span><span class="sxs-lookup"><span data-stu-id="feee7-124">Header</span></span></p></td>
<td><span data-ttu-id="feee7-125">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="feee7-125">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="feee7-126">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="feee7-126">Library</span></span></p></td>
<td><span data-ttu-id="feee7-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="feee7-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="feee7-128">DLL</span><span class="sxs-lookup"><span data-stu-id="feee7-128">DLL</span></span></p></td>
<td><span data-ttu-id="feee7-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="feee7-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="feee7-130"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="feee7-130"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="feee7-131">Pseudo Konsolen</span><span class="sxs-lookup"><span data-stu-id="feee7-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="feee7-132">**"Kreatepseudoconsole"**</span><span class="sxs-lookup"><span data-stu-id="feee7-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="feee7-133">**Closepseudoconsole**</span><span class="sxs-lookup"><span data-stu-id="feee7-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
