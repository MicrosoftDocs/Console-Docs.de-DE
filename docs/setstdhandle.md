---
title: Setstdhandle-Funktion
description: Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039298"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="7566a-104">Setstdhandle-Funktion</span><span class="sxs-lookup"><span data-stu-id="7566a-104">SetStdHandle function</span></span>

<span data-ttu-id="7566a-105">Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.</span><span class="sxs-lookup"><span data-stu-id="7566a-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="7566a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7566a-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="7566a-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="7566a-107">Parameters</span></span>

<span data-ttu-id="7566a-108">*nstdhandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="7566a-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="7566a-109">Das Standardgerät, für das das Handle festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="7566a-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="7566a-110">Dieser Parameter kann einen der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="7566a-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="7566a-111">Wert</span><span class="sxs-lookup"><span data-stu-id="7566a-111">Value</span></span> | <span data-ttu-id="7566a-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="7566a-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="7566a-113">**STD_INPUT_HANDLE** (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="7566a-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="7566a-114">Das Standardeingabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="7566a-114">The standard input device.</span></span> <span data-ttu-id="7566a-115">Anfänglich ist dies der Konsolen Eingabepuffer `CONIN$` .</span><span class="sxs-lookup"><span data-stu-id="7566a-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="7566a-116">**STD_OUTPUT_HANDLE** (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="7566a-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="7566a-117">Das Standardausgabe Gerät.</span><span class="sxs-lookup"><span data-stu-id="7566a-117">The standard output device.</span></span> <span data-ttu-id="7566a-118">Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="7566a-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="7566a-119">**STD_ERROR_HANDLE** (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="7566a-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="7566a-120">Das Standardfehler Gerät.</span><span class="sxs-lookup"><span data-stu-id="7566a-120">The standard error device.</span></span> <span data-ttu-id="7566a-121">Anfänglich ist dies der aktive Konsolenbildschirm Puffer `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="7566a-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="7566a-122">*hHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="7566a-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="7566a-123">Das Handle für das Standardgerät.</span><span class="sxs-lookup"><span data-stu-id="7566a-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="7566a-124">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="7566a-124">Return value</span></span>

<span data-ttu-id="7566a-125">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="7566a-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7566a-126">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="7566a-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7566a-127">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="7566a-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="7566a-128">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="7566a-128">Remarks</span></span>

<span data-ttu-id="7566a-129">Die Standard Handles eines Prozesses wurden möglicherweise durch einen Aufrufen von **setstdhandle** umgeleitet. in diesem Fall gibt [**getstdhandle**](getstdhandle.md) das umgeleitete Handle zurück.</span><span class="sxs-lookup"><span data-stu-id="7566a-129">The standard handles of a process may have been redirected by a call to **SetStdHandle** , in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="7566a-130">Wenn die Standard Handles umgeleitet wurden, können Sie den Wert von "$" in einem Aufrufen der Funktion "angleichen [**Datei**](https://msdn.microsoft.com/library/windows/desktop/aa363858) " angeben, um ein Handle für den Eingabepuffer einer Konsole abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7566a-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="7566a-131">Entsprechend können Sie den Wert für "$ $" angeben, um ein Handle für den aktiven Bildschirm Puffer der Konsole zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7566a-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="7566a-132">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7566a-132">Examples</span></span>

<span data-ttu-id="7566a-133">Ein Beispiel finden Sie unter [Erstellen eines untergeordneten Prozesses mit umgeleiteter Eingabe und Ausgabe](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="7566a-133">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

## <a name="requirements"></a><span data-ttu-id="7566a-134">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="7566a-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7566a-135">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="7566a-135">Minimum supported client</span></span> | <span data-ttu-id="7566a-136">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="7566a-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7566a-137">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="7566a-137">Minimum supported server</span></span> | <span data-ttu-id="7566a-138">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="7566a-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7566a-139">Header</span><span class="sxs-lookup"><span data-stu-id="7566a-139">Header</span></span> | <span data-ttu-id="7566a-140">Processenv. h (über Winbase. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7566a-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="7566a-141">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="7566a-141">Library</span></span> | <span data-ttu-id="7566a-142">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="7566a-142">Kernel32.lib</span></span> |
| <span data-ttu-id="7566a-143">DLL</span><span class="sxs-lookup"><span data-stu-id="7566a-143">DLL</span></span> | <span data-ttu-id="7566a-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7566a-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="7566a-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7566a-145">See also</span></span>

[<span data-ttu-id="7566a-146">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="7566a-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7566a-147">Konsolenhandles</span><span class="sxs-lookup"><span data-stu-id="7566a-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="7566a-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="7566a-148">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="7566a-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="7566a-149">**GetStdHandle**</span></span>](getstdhandle.md)
