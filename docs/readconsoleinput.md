---
title: Read ConsoleInput-Funktion
description: Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 38a5ee0d1572d6e40ab103cfc402d616a99d2ca5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060402"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="ecdc5-104">Read ConsoleInput-Funktion</span><span class="sxs-lookup"><span data-stu-id="ecdc5-104">ReadConsoleInput function</span></span>


<span data-ttu-id="ecdc5-105">Liest Daten aus einem Konsolen Eingabepuffer und entfernt Sie aus dem Puffer.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="ecdc5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ecdc5-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="ecdc5-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="ecdc5-107">Parameters</span></span>
----------

<span data-ttu-id="ecdc5-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ecdc5-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="ecdc5-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-109">A handle to the console input buffer.</span></span> <span data-ttu-id="ecdc5-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ecdc5-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ecdc5-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ecdc5-112">*lpBuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="ecdc5-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="ecdc5-113">Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die die Eingabepuffer Daten empfangen.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="ecdc5-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ecdc5-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="ecdc5-115">Die Größe des Arrays, auf das durch den *lpBuffer* -Parameter in Array Elementen verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="ecdc5-116">*lpnumofeventsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="ecdc5-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="ecdc5-117">Ein Zeiger auf eine Variable, die die Anzahl der gelesenen Eingabedaten Sätze empfängt.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="ecdc5-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ecdc5-118">Return value</span></span>
------------

<span data-ttu-id="ecdc5-119">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="ecdc5-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ecdc5-120">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ecdc5-121">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ecdc5-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ecdc5-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ecdc5-122">Remarks</span></span>
-------

<span data-ttu-id="ecdc5-123">Wenn die Anzahl der im *nlength* -Parameter angeforderten Datensätze die Anzahl der Datensätze überschreitet, die im Puffer verfügbar sind, wird die Anzahl der verfügbaren Datensätze gelesen.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="ecdc5-124">Die Funktion gibt erst zurück, wenn mindestens ein Eingabedaten Satz gelesen wurde.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="ecdc5-125">Ein Prozess kann ein Konsolen Eingabepuffer Handle in einer der Wait- [Funktionen](https://msdn.microsoft.com/library/windows/desktop/ms687069) angeben, um zu bestimmen, wann eine ungelesene Konsolen Eingabe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-125">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="ecdc5-126">Wenn der Eingabepuffer nicht leer ist, wird der Status eines Konsolen Eingabepuffer-Handles signalisiert.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="ecdc5-127">Verwenden Sie die [**getnummeriofconsoleinputevents**](getnumberofconsoleinputevents.md) -Funktion, um die Anzahl der ungelesenen Eingabedaten Sätze im Eingabepuffer einer Konsole zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="ecdc5-128">Um Eingabedaten Sätze aus einem Konsolen Eingabepuffer zu lesen, ohne die Anzahl der ungelesenen Datensätze zu beeinträchtigen, verwenden Sie die Funktion " [**Peer**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="ecdc5-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="ecdc5-129">Verwenden Sie die [**flushconsoleinputbuffer**](flushconsoleinputbuffer.md) -Funktion, um alle ungelesenen Datensätze im Eingabepuffer einer Konsole zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

<span data-ttu-id="ecdc5-130">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-130">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="ecdc5-131">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="ecdc5-131">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="ecdc5-132">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="ecdc5-132">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="ecdc5-133">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ecdc5-133">Examples</span></span>
--------

<span data-ttu-id="ecdc5-134">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="ecdc5-134">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="ecdc5-135">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ecdc5-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ecdc5-136">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ecdc5-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ecdc5-137">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ecdc5-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ecdc5-138">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ecdc5-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ecdc5-139">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="ecdc5-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ecdc5-140">Header</span><span class="sxs-lookup"><span data-stu-id="ecdc5-140">Header</span></span></p></td>
<td><span data-ttu-id="ecdc5-141">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ecdc5-141">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ecdc5-142">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ecdc5-142">Library</span></span></p></td>
<td><span data-ttu-id="ecdc5-143">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ecdc5-143">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ecdc5-144">DLL</span><span class="sxs-lookup"><span data-stu-id="ecdc5-144">DLL</span></span></p></td>
<td><span data-ttu-id="ecdc5-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ecdc5-145">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ecdc5-146">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="ecdc5-146">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="ecdc5-147">"Read <strong>consolinput w</strong> (Unicode)" und "read <strong>consolinput a</strong> " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ecdc5-147"><strong>ReadConsoleInputW</strong> (Unicode) and <strong>ReadConsoleInputA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ecdc5-148"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ecdc5-148"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ecdc5-149">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ecdc5-149">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ecdc5-150">**Flushconsolinput Buffer**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-150">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="ecdc5-151">**Getnumofconsoleinputevents**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-151">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="ecdc5-152">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-152">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="ecdc5-153">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="ecdc5-153">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="ecdc5-154">**"Etekconsoleinput"**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-154">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="ecdc5-155">**"Read Console"**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-155">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="ecdc5-156">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-156">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="ecdc5-157">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-157">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ecdc5-158">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-158">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="ecdc5-159">**Schreibconsoleinput**</span><span class="sxs-lookup"><span data-stu-id="ecdc5-159">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




