---
title: Funktion "Beschreib teconsoleinput"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Beschreib teconsoleinput", die Daten direkt in den Konsolen Eingabepuffer schreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc2c7930ab76587edc9ae1991d4493c858b0ec30
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039288"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="83dd7-104">Funktion "Beschreib teconsoleinput"</span><span class="sxs-lookup"><span data-stu-id="83dd7-104">WriteConsoleInput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="83dd7-105">Schreibt Daten direkt in den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="83dd7-105">Writes data directly to the console input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="83dd7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="83dd7-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="83dd7-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="83dd7-107">Parameters</span></span>

<span data-ttu-id="83dd7-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="83dd7-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="83dd7-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="83dd7-109">A handle to the console input buffer.</span></span> <span data-ttu-id="83dd7-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="83dd7-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="83dd7-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="83dd7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="83dd7-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="83dd7-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="83dd7-113">Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die Daten enthalten, die in den Eingabepuffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="83dd7-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="83dd7-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="83dd7-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="83dd7-115">Die Anzahl der Eingabedaten Sätze, die geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="83dd7-115">The number of input records to be written.</span></span>

<span data-ttu-id="83dd7-116">*lpnumofeventswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="83dd7-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="83dd7-117">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Eingabedaten Sätze empfängt.</span><span class="sxs-lookup"><span data-stu-id="83dd7-117">A pointer to a variable that receives the number of input records actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="83dd7-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="83dd7-118">Return value</span></span>

<span data-ttu-id="83dd7-119">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="83dd7-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="83dd7-120">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="83dd7-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="83dd7-121">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="83dd7-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="83dd7-122">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="83dd7-122">Remarks</span></span>

<span data-ttu-id="83dd7-123">" **Write-ConsoleInput** " fügt Eingabedaten Sätze in den Eingabepuffer hinter allen ausstehenden Ereignissen im Puffer ein.</span><span class="sxs-lookup"><span data-stu-id="83dd7-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="83dd7-124">Der Eingabepuffer wächst bei Bedarf dynamisch, um so viele Ereignisse zu speichern, wie Sie geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="83dd7-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="83dd7-125">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="83dd7-125">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="83dd7-126">Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus.</span><span class="sxs-lookup"><span data-stu-id="83dd7-126">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="83dd7-127">Dieser Vorgang wird als **[falsch-Wege-Verb](console-buffer-security-and-access-rights.md#wrong-way-verbs)** für diesen Puffer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="83dd7-127">This operation is considered the **[wrong-way verb](console-buffer-security-and-access-rights.md#wrong-way-verbs)** for this buffer.</span></span> <span data-ttu-id="83dd7-128">Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.</span><span class="sxs-lookup"><span data-stu-id="83dd7-128">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="83dd7-129">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="83dd7-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="83dd7-130">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="83dd7-130">Minimum supported client</span></span> | <span data-ttu-id="83dd7-131">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="83dd7-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="83dd7-132">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="83dd7-132">Minimum supported server</span></span> | <span data-ttu-id="83dd7-133">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="83dd7-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="83dd7-134">Header</span><span class="sxs-lookup"><span data-stu-id="83dd7-134">Header</span></span> | <span data-ttu-id="83dd7-135">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="83dd7-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="83dd7-136">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="83dd7-136">Library</span></span> | <span data-ttu-id="83dd7-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="83dd7-137">Kernel32.lib</span></span> |
| <span data-ttu-id="83dd7-138">DLL</span><span class="sxs-lookup"><span data-stu-id="83dd7-138">DLL</span></span> | <span data-ttu-id="83dd7-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="83dd7-139">Kernel32.dll</span></span> |
| <span data-ttu-id="83dd7-140">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="83dd7-140">Unicode and ANSI names</span></span> | <span data-ttu-id="83dd7-141">Schreiben von " **Write-consolinput w** (Unicode)" und " **Write-consolinput a** " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="83dd7-141">**WriteConsoleInputW** (Unicode) and **WriteConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="83dd7-142">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="83dd7-142">See also</span></span>

[<span data-ttu-id="83dd7-143">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="83dd7-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="83dd7-144">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="83dd7-144">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="83dd7-145">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="83dd7-145">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="83dd7-146">**Mapvirtualkey**</span><span class="sxs-lookup"><span data-stu-id="83dd7-146">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="83dd7-147">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="83dd7-147">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="83dd7-148">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="83dd7-148">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="83dd7-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="83dd7-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="83dd7-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="83dd7-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="83dd7-151">**Vkkeyscan**</span><span class="sxs-lookup"><span data-stu-id="83dd7-151">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)
