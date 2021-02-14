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
ms.openlocfilehash: 622dc96598df9a851934c73645afb7691f77f1be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358860"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="1aa6e-104">Getnumofconsoleinputevents-Funktion</span><span class="sxs-lookup"><span data-stu-id="1aa6e-104">GetNumberOfConsoleInputEvents function</span></span>

<span data-ttu-id="1aa6e-105">Ruft die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole ab.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="1aa6e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1aa6e-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a><span data-ttu-id="1aa6e-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1aa6e-107">Parameters</span></span>

<span data-ttu-id="1aa6e-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1aa6e-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="1aa6e-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-109">A handle to the console input buffer.</span></span> <span data-ttu-id="1aa6e-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="1aa6e-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="1aa6e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1aa6e-112">*lpcnumofevents* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="1aa6e-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="1aa6e-113">Ein Zeiger auf eine Variable, die die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="1aa6e-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1aa6e-114">Return value</span></span>

<span data-ttu-id="1aa6e-115">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1aa6e-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1aa6e-117">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="1aa6e-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1aa6e-118">Remarks</span></span>

<span data-ttu-id="1aa6e-119">Die **getnumofconsoleinputevents** -Funktion meldet die Gesamtzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer, einschließlich der Tastatur-, Maus-und Fenstergröße für Eingabedaten Sätze.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="1aa6e-120">Prozesse, die die Funktion "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) " oder "read [**Console**](readconsole.md) " verwenden, können nur Tastatureingaben lesen.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-120">Processes using the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="1aa6e-121">Prozesse, die die Funktion " [**leseconsoleinput**](readconsoleinput.md) " verwenden, können alle Typen von Eingabedaten Sätzen lesen.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="1aa6e-122">Ein Prozess kann ein Konsolen Eingabepuffer Handle in einer der Wait- [Funktionen](/windows/win32/sync/wait-functions) angeben, um zu bestimmen, wann eine ungelesene Konsolen Eingabe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-122">A process can specify a console input buffer handle in one of the [wait functions](/windows/win32/sync/wait-functions) to determine when there is unread console input.</span></span> <span data-ttu-id="1aa6e-123">Wenn der Eingabepuffer nicht leer ist, wird der Status eines Konsolen Eingabepuffer-Handles signalisiert.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="1aa6e-124">Um Eingabedaten Sätze aus einem Konsolen Eingabepuffer zu lesen, ohne die Anzahl der ungelesenen Datensätze zu beeinträchtigen, verwenden Sie die Funktion " [**Peer**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="1aa6e-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="1aa6e-125">Verwenden Sie die [**flushconsoleinputbuffer**](flushconsoleinputbuffer.md) -Funktion, um alle ungelesenen Datensätze im Eingabepuffer einer Konsole zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="1aa6e-126">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1aa6e-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1aa6e-127">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1aa6e-127">Minimum supported client</span></span> | <span data-ttu-id="1aa6e-128">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1aa6e-128">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1aa6e-129">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1aa6e-129">Minimum supported server</span></span> | <span data-ttu-id="1aa6e-130">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1aa6e-130">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1aa6e-131">Header</span><span class="sxs-lookup"><span data-stu-id="1aa6e-131">Header</span></span> | <span data-ttu-id="1aa6e-132">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="1aa6e-132">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1aa6e-133">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1aa6e-133">Library</span></span> | <span data-ttu-id="1aa6e-134">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="1aa6e-134">Kernel32.lib</span></span> |
| <span data-ttu-id="1aa6e-135">DLL</span><span class="sxs-lookup"><span data-stu-id="1aa6e-135">DLL</span></span> | <span data-ttu-id="1aa6e-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1aa6e-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="1aa6e-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1aa6e-137">See also</span></span>

[<span data-ttu-id="1aa6e-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1aa6e-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1aa6e-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="1aa6e-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="1aa6e-140">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="1aa6e-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="1aa6e-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="1aa6e-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="1aa6e-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="1aa6e-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="1aa6e-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="1aa6e-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="1aa6e-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="1aa6e-144">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)