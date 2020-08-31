---
title: Funktion "Beschreib teconsoleinput"
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "Beschreib teconsoleinput", die Daten direkt in den Konsolen Eingabepuffer schreibt.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 784bed6c1a7b7f7ed9ed204b8483d30371e510a3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060563"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="87b84-104">Funktion "Beschreib teconsoleinput"</span><span class="sxs-lookup"><span data-stu-id="87b84-104">WriteConsoleInput function</span></span>


<span data-ttu-id="87b84-105">Schreibt Daten direkt in den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="87b84-105">Writes data directly to the console input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="87b84-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="87b84-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

<a name="parameters"></a><span data-ttu-id="87b84-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="87b84-107">Parameters</span></span>
----------

<span data-ttu-id="87b84-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="87b84-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="87b84-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="87b84-109">A handle to the console input buffer.</span></span> <span data-ttu-id="87b84-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="87b84-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="87b84-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="87b84-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="87b84-112">*lpBuffer* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="87b84-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="87b84-113">Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die Daten enthalten, die in den Eingabepuffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="87b84-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="87b84-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="87b84-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="87b84-115">Die Anzahl der Eingabedaten Sätze, die geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="87b84-115">The number of input records to be written.</span></span>

<span data-ttu-id="87b84-116">*lpnumofeventswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="87b84-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="87b84-117">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Eingabedaten Sätze empfängt.</span><span class="sxs-lookup"><span data-stu-id="87b84-117">A pointer to a variable that receives the number of input records actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="87b84-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="87b84-118">Return value</span></span>
------------

<span data-ttu-id="87b84-119">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="87b84-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="87b84-120">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="87b84-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="87b84-121">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="87b84-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="87b84-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="87b84-122">Remarks</span></span>
-------

<span data-ttu-id="87b84-123">" **Write-ConsoleInput** " fügt Eingabedaten Sätze in den Eingabepuffer hinter allen ausstehenden Ereignissen im Puffer ein.</span><span class="sxs-lookup"><span data-stu-id="87b84-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="87b84-124">Der Eingabepuffer wächst bei Bedarf dynamisch, um so viele Ereignisse zu speichern, wie Sie geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="87b84-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

<span data-ttu-id="87b84-125">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="87b84-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="87b84-126">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="87b84-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="87b84-127">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="87b84-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="87b84-128">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="87b84-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="87b84-129">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="87b84-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="87b84-130">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="87b84-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87b84-131">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="87b84-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="87b84-132">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="87b84-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87b84-133">Header</span><span class="sxs-lookup"><span data-stu-id="87b84-133">Header</span></span></p></td>
<td><span data-ttu-id="87b84-134">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="87b84-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87b84-135">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="87b84-135">Library</span></span></p></td>
<td><span data-ttu-id="87b84-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="87b84-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87b84-137">DLL</span><span class="sxs-lookup"><span data-stu-id="87b84-137">DLL</span></span></p></td>
<td><span data-ttu-id="87b84-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="87b84-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87b84-139">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="87b84-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="87b84-140">Schreiben von " <strong>Write-consolinput w</strong> (Unicode)" und " <strong>Write-consolinput a</strong> " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="87b84-140"><strong>WriteConsoleInputW</strong> (Unicode) and <strong>WriteConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="87b84-141"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="87b84-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="87b84-142">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="87b84-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="87b84-143">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="87b84-143">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="87b84-144">Konsolen Eingabefunktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="87b84-144">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="87b84-145">**Mapvirtualkey**</span><span class="sxs-lookup"><span data-stu-id="87b84-145">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="87b84-146">**"Etekconsoleinput"**</span><span class="sxs-lookup"><span data-stu-id="87b84-146">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="87b84-147">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="87b84-147">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="87b84-148">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="87b84-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="87b84-149">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="87b84-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="87b84-150">**Vkkeyscan**</span><span class="sxs-lookup"><span data-stu-id="87b84-150">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 




