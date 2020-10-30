---
title: Getnumofconsoleinputevents-Funktion
description: Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b4cad78d35114c509f4e810a858e6ae3b8bfb644
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038688"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="41279-104">Getnumofconsoleinputevents-Funktion</span><span class="sxs-lookup"><span data-stu-id="41279-104">GetNumberOfConsoleInputEvents function</span></span>

<span data-ttu-id="41279-105">Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.</span><span class="sxs-lookup"><span data-stu-id="41279-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="41279-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="41279-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a><span data-ttu-id="41279-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="41279-107">Parameters</span></span>

<span data-ttu-id="41279-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="41279-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="41279-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="41279-109">A handle to the console input buffer.</span></span> <span data-ttu-id="41279-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="41279-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="41279-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="41279-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="41279-112">*lpcnumofevents* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="41279-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="41279-113">Ein Zeiger auf eine Variable, die die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="41279-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="41279-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="41279-114">Return value</span></span>

<span data-ttu-id="41279-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="41279-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="41279-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="41279-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="41279-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="41279-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="41279-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="41279-118">Remarks</span></span>

<span data-ttu-id="41279-119">Die **getnumofconsoleinputevents** -Funktion meldet die Gesamtzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer, einschließlich der Tastatur-, Maus-und Fenstergröße für Eingabedaten Sätze.</span><span class="sxs-lookup"><span data-stu-id="41279-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="41279-120">Prozesse, die die Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) " verwenden, können nur Tastatureingaben lesen.</span><span class="sxs-lookup"><span data-stu-id="41279-120">Processes using the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="41279-121">Prozesse, die die Funktion " [**leseconsoleinput**](readconsoleinput.md) " verwenden, können alle Typen von Eingabedaten Sätzen lesen.</span><span class="sxs-lookup"><span data-stu-id="41279-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="41279-122">Ein Prozess kann ein Konsolen Eingabepuffer Handle in einer der Wait- [Funktionen](https://msdn.microsoft.com/library/windows/desktop/ms687069) angeben, um zu bestimmen, wann eine ungelesene Konsolen Eingabe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="41279-122">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="41279-123">Wenn der Eingabepuffer nicht leer ist, wird der Status eines Konsolen Eingabepuffer-Handles signalisiert.</span><span class="sxs-lookup"><span data-stu-id="41279-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="41279-124">Um Eingabedaten Sätze aus einem Konsolen Eingabepuffer zu lesen, ohne die Anzahl der ungelesenen Datensätze zu beeinträchtigen, verwenden Sie die Funktion " [**Peer**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="41279-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="41279-125">Verwenden Sie die [**flushconsoleinputbuffer**](flushconsoleinputbuffer.md) -Funktion, um alle ungelesenen Datensätze im Eingabepuffer einer Konsole zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="41279-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="41279-126">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="41279-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="41279-127">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="41279-127">Minimum supported client</span></span> | <span data-ttu-id="41279-128">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="41279-128">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="41279-129">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="41279-129">Minimum supported server</span></span> | <span data-ttu-id="41279-130">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="41279-130">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="41279-131">Header</span><span class="sxs-lookup"><span data-stu-id="41279-131">Header</span></span> | <span data-ttu-id="41279-132">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="41279-132">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="41279-133">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="41279-133">Library</span></span> | <span data-ttu-id="41279-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="41279-134">Kernel32.lib</span></span> |
| <span data-ttu-id="41279-135">DLL</span><span class="sxs-lookup"><span data-stu-id="41279-135">DLL</span></span> | <span data-ttu-id="41279-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="41279-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="41279-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="41279-137">See also</span></span>

[<span data-ttu-id="41279-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="41279-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="41279-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="41279-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="41279-140">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="41279-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="41279-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="41279-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="41279-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="41279-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="41279-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="41279-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="41279-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="41279-144">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)
