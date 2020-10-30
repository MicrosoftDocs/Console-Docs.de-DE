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
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037288"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="0955e-104">Closepseudoconsole-Funktion</span><span class="sxs-lookup"><span data-stu-id="0955e-104">ClosePseudoConsole function</span></span>

<span data-ttu-id="0955e-105">Schließt eine pseudoconsole aus dem angegebenen Handle.</span><span class="sxs-lookup"><span data-stu-id="0955e-105">Closes a pseudoconsole from the given handle.</span></span>

## <a name="syntax"></a><span data-ttu-id="0955e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0955e-106">Syntax</span></span>

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a><span data-ttu-id="0955e-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="0955e-107">Parameters</span></span>

<span data-ttu-id="0955e-108">*HPC* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0955e-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="0955e-109">Ein Handle für eine aktive pseudoconsole, wie von " [kreatepseudoconsole](createpseudoconsole.md)" geöffnet.</span><span class="sxs-lookup"><span data-stu-id="0955e-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="0955e-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0955e-110">Return value</span></span>

<span data-ttu-id="0955e-111">*keine*</span><span class="sxs-lookup"><span data-stu-id="0955e-111">*none*</span></span>

## <a name="remarks"></a><span data-ttu-id="0955e-112">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="0955e-112">Remarks</span></span>

<span data-ttu-id="0955e-113">Wenn Sie eine Pseudo Konsole schließen, werden auch Client Anwendungen beendet, die an die Sitzung angefügt sind.</span><span class="sxs-lookup"><span data-stu-id="0955e-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="0955e-114">Wenn diese API aufgerufen wird, wird möglicherweise ein abschließender Rahmen auf dem `hOutput` Handle angezeigt, das ursprünglich für " [kreatepsuedoconsole](createpseudoconsole.md) " bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="0955e-114">A final painted frame may arrive on the `hOutput` handle originally provided to [CreatePsuedoConsole](createpseudoconsole.md) when this API is called.</span></span> <span data-ttu-id="0955e-115">Es wird erwartet, dass der Aufrufer diese Informationen aus dem Kommunikationskanal Puffer abfließt und ihn entweder vornimmt oder verwerfen kann.</span><span class="sxs-lookup"><span data-stu-id="0955e-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="0955e-116">Wenn der Puffer nicht entladen wird, kann es passieren, dass der Close-Befehl unbegrenzt wartet, bis er entladen wird oder die Kommunikationskanäle anders voneinander getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="0955e-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

## <a name="requirements"></a><span data-ttu-id="0955e-117">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="0955e-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0955e-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0955e-118">Minimum supported client</span></span> | <span data-ttu-id="0955e-119">Windows 10-Update vom Oktober 2018 (Version 1809) \[ nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0955e-119">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="0955e-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0955e-120">Minimum supported server</span></span> | <span data-ttu-id="0955e-121">Nur Windows Server 2019 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0955e-121">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="0955e-122">Header</span><span class="sxs-lookup"><span data-stu-id="0955e-122">Header</span></span> | <span data-ttu-id="0955e-123">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0955e-123">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0955e-124">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="0955e-124">Library</span></span> | <span data-ttu-id="0955e-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0955e-125">Kernel32.lib</span></span> |
| <span data-ttu-id="0955e-126">DLL</span><span class="sxs-lookup"><span data-stu-id="0955e-126">DLL</span></span> | <span data-ttu-id="0955e-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0955e-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0955e-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0955e-128">See also</span></span>

[<span data-ttu-id="0955e-129">Pseudo Konsolen</span><span class="sxs-lookup"><span data-stu-id="0955e-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="0955e-130">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="0955e-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="0955e-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="0955e-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
