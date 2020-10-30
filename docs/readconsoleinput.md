---
title: Read ConsoleInput-Funktion
description: Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38778931522dff8d1d000bb6f0ce13c2849d76db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039488"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="82c40-104">Read ConsoleInput-Funktion</span><span class="sxs-lookup"><span data-stu-id="82c40-104">ReadConsoleInput function</span></span>

<span data-ttu-id="82c40-105">Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.</span><span class="sxs-lookup"><span data-stu-id="82c40-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="82c40-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="82c40-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="82c40-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="82c40-107">Parameters</span></span>

<span data-ttu-id="82c40-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="82c40-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="82c40-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="82c40-109">A handle to the console input buffer.</span></span> <span data-ttu-id="82c40-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="82c40-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="82c40-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="82c40-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="82c40-112">*lpBuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="82c40-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="82c40-113">Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die die Eingabepuffer Daten empfangen.</span><span class="sxs-lookup"><span data-stu-id="82c40-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="82c40-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="82c40-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="82c40-115">Die Größe des Arrays, auf das durch den *lpBuffer* -Parameter in Array Elementen verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="82c40-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="82c40-116">*lpnumofeventsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="82c40-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="82c40-117">Ein Zeiger auf eine Variable, die die Anzahl der gelesenen Eingabedaten Sätze empfängt.</span><span class="sxs-lookup"><span data-stu-id="82c40-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="82c40-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="82c40-118">Return value</span></span>

<span data-ttu-id="82c40-119">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="82c40-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="82c40-120">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="82c40-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="82c40-121">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="82c40-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="82c40-122">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="82c40-122">Remarks</span></span>

<span data-ttu-id="82c40-123">Wenn die Anzahl der im *nlength* -Parameter angeforderten Datensätze die Anzahl der Datensätze überschreitet, die im Puffer verfügbar sind, wird die Anzahl der verfügbaren Datensätze gelesen.</span><span class="sxs-lookup"><span data-stu-id="82c40-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="82c40-124">Die Funktion gibt erst zurück, wenn mindestens ein Eingabedaten Satz gelesen wurde.</span><span class="sxs-lookup"><span data-stu-id="82c40-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="82c40-125">Ein Prozess kann ein Konsolen Eingabepuffer Handle in einer der Wait- [Funktionen](https://msdn.microsoft.com/library/windows/desktop/ms687069) angeben, um zu bestimmen, wann eine ungelesene Konsolen Eingabe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="82c40-125">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="82c40-126">Wenn der Eingabepuffer nicht leer ist, wird der Status eines Konsolen Eingabepuffer-Handles signalisiert.</span><span class="sxs-lookup"><span data-stu-id="82c40-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="82c40-127">Verwenden Sie die [**getnummeriofconsoleinputevents**](getnumberofconsoleinputevents.md) -Funktion, um die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer einer Konsole zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="82c40-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="82c40-128">Um Eingabedaten Sätze aus einem Konsolen Eingabepuffer zu lesen, ohne die Anzahl der ungelesenen Datensätze zu beeinträchtigen, verwenden Sie die Funktion " [**Peer**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="82c40-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="82c40-129">Verwenden Sie die [**flushconsoleinputbuffer**](flushconsoleinputbuffer.md) -Funktion, um alle ungelesenen Datensätze im Eingabepuffer einer Konsole zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="82c40-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a><span data-ttu-id="82c40-130">Beispiele</span><span class="sxs-lookup"><span data-stu-id="82c40-130">Examples</span></span>

<span data-ttu-id="82c40-131">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="82c40-131">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="82c40-132">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="82c40-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="82c40-133">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="82c40-133">Minimum supported client</span></span> | <span data-ttu-id="82c40-134">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="82c40-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="82c40-135">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="82c40-135">Minimum supported server</span></span> | <span data-ttu-id="82c40-136">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="82c40-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="82c40-137">Header</span><span class="sxs-lookup"><span data-stu-id="82c40-137">Header</span></span> | <span data-ttu-id="82c40-138">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="82c40-138">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="82c40-139">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="82c40-139">Library</span></span> | <span data-ttu-id="82c40-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="82c40-140">Kernel32.lib</span></span> |
| <span data-ttu-id="82c40-141">DLL</span><span class="sxs-lookup"><span data-stu-id="82c40-141">DLL</span></span> | <span data-ttu-id="82c40-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="82c40-142">Kernel32.dll</span></span> |
| <span data-ttu-id="82c40-143">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="82c40-143">Unicode and ANSI names</span></span> | <span data-ttu-id="82c40-144">"Read **consolinput w** (Unicode)" und "read **consolinput a** " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="82c40-144">**ReadConsoleInputW** (Unicode) and **ReadConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="82c40-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="82c40-145">See also</span></span>

[<span data-ttu-id="82c40-146">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="82c40-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="82c40-147">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="82c40-147">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="82c40-148">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="82c40-148">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="82c40-149">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="82c40-149">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="82c40-150">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="82c40-150">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="82c40-151">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="82c40-151">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="82c40-152">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="82c40-152">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="82c40-153">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="82c40-153">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="82c40-154">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="82c40-154">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="82c40-155">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="82c40-155">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="82c40-156">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="82c40-156">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
