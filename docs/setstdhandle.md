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
ms.openlocfilehash: 317acd84289e5138e1a947251e745077ba581083
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358510"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="77c6c-104">Setstdhandle-Funktion</span><span class="sxs-lookup"><span data-stu-id="77c6c-104">SetStdHandle function</span></span>

<span data-ttu-id="77c6c-105">Legt das Handle für das angegebene Standardgerät (Standardeingabe, Standardausgabe oder Standardfehler) fest.</span><span class="sxs-lookup"><span data-stu-id="77c6c-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="77c6c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="77c6c-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="77c6c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="77c6c-107">Parameters</span></span>

<span data-ttu-id="77c6c-108">*nStdHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="77c6c-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="77c6c-109">Das Standardgerät, für das das Handle festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="77c6c-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="77c6c-110">Dieser Parameter kann einen der folgenden Werte annehmen.</span><span class="sxs-lookup"><span data-stu-id="77c6c-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="77c6c-111">Wert</span><span class="sxs-lookup"><span data-stu-id="77c6c-111">Value</span></span> | <span data-ttu-id="77c6c-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="77c6c-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="77c6c-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="77c6c-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="77c6c-114">Das Standardeingabegerät.</span><span class="sxs-lookup"><span data-stu-id="77c6c-114">The standard input device.</span></span> <span data-ttu-id="77c6c-115">Anfänglich ist dies der Konsoleneingabepuffer, `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="77c6c-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="77c6c-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="77c6c-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="77c6c-117">Das Standardausgabegerät.</span><span class="sxs-lookup"><span data-stu-id="77c6c-117">The standard output device.</span></span> <span data-ttu-id="77c6c-118">Anfänglich ist dies der aktive Konsolenbildschirmpuffer, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="77c6c-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="77c6c-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="77c6c-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="77c6c-120">Das Standardfehlergerät.</span><span class="sxs-lookup"><span data-stu-id="77c6c-120">The standard error device.</span></span> <span data-ttu-id="77c6c-121">Anfänglich ist dies der aktive Konsolenbildschirmpuffer, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="77c6c-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="77c6c-122">*hHandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="77c6c-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="77c6c-123">Das Handle für das Standardgerät.</span><span class="sxs-lookup"><span data-stu-id="77c6c-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="77c6c-124">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="77c6c-124">Return value</span></span>

<span data-ttu-id="77c6c-125">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="77c6c-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="77c6c-126">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="77c6c-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="77c6c-127">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="77c6c-127">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="77c6c-128">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="77c6c-128">Remarks</span></span>

<span data-ttu-id="77c6c-129">Die Standard Handles eines Prozesses wurden möglicherweise durch einen Aufrufen von **setstdhandle** umgeleitet. in diesem Fall gibt [**getstdhandle**](getstdhandle.md) das umgeleitete Handle zurück.</span><span class="sxs-lookup"><span data-stu-id="77c6c-129">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="77c6c-130">Wenn die Standard Handles umgeleitet wurden, können Sie den Wert von "$" in einem Aufrufen der Funktion "angleichen [**Datei**](/windows/win32/api/fileapi/nf-fileapi-createfilea) " angeben, um ein Handle für den Eingabepuffer einer Konsole abzurufen.</span><span class="sxs-lookup"><span data-stu-id="77c6c-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="77c6c-131">Entsprechend können Sie den Wert für "$ $" angeben, um ein Handle für den aktiven Bildschirm Puffer der Konsole zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="77c6c-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="77c6c-132">Beispiele</span><span class="sxs-lookup"><span data-stu-id="77c6c-132">Examples</span></span>

<span data-ttu-id="77c6c-133">Ein Beispiel finden Sie unter [Erstellen eines untergeordneten Prozesses mit umgeleiteter Eingabe und Ausgabe](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="77c6c-133">For an example, see [Creating a Child Process with Redirected Input and Output](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span></span>

## <a name="requirements"></a><span data-ttu-id="77c6c-134">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="77c6c-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="77c6c-135">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="77c6c-135">Minimum supported client</span></span> | <span data-ttu-id="77c6c-136">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="77c6c-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="77c6c-137">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="77c6c-137">Minimum supported server</span></span> | <span data-ttu-id="77c6c-138">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="77c6c-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="77c6c-139">Header</span><span class="sxs-lookup"><span data-stu-id="77c6c-139">Header</span></span> | <span data-ttu-id="77c6c-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span><span class="sxs-lookup"><span data-stu-id="77c6c-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="77c6c-141">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="77c6c-141">Library</span></span> | <span data-ttu-id="77c6c-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="77c6c-142">Kernel32.lib</span></span> |
| <span data-ttu-id="77c6c-143">DLL</span><span class="sxs-lookup"><span data-stu-id="77c6c-143">DLL</span></span> | <span data-ttu-id="77c6c-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="77c6c-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="77c6c-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="77c6c-145">See also</span></span>

[<span data-ttu-id="77c6c-146">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="77c6c-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="77c6c-147">Konsolenhandles</span><span class="sxs-lookup"><span data-stu-id="77c6c-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="77c6c-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="77c6c-148">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="77c6c-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="77c6c-149">**GetStdHandle**</span></span>](getstdhandle.md)