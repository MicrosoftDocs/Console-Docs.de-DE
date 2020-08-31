---
title: Funktion "Peer-ConsoleInput"
description: Liest Daten aus dem angegebenen Konsolen Eingabepuffer, ohne Sie aus dem Puffer zu entfernen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c74df91f3b70827cd0c5410d01b2a165694909f9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059579"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="b846f-104">Funktion "Peer-ConsoleInput"</span><span class="sxs-lookup"><span data-stu-id="b846f-104">PeekConsoleInput function</span></span>


<span data-ttu-id="b846f-105">Liest Daten aus dem angegebenen Konsolen Eingabepuffer, ohne Sie aus dem Puffer zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="b846f-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="b846f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b846f-106">Syntax</span></span>
------

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="b846f-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="b846f-107">Parameters</span></span>
----------

<span data-ttu-id="b846f-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b846f-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="b846f-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="b846f-109">A handle to the console input buffer.</span></span> <span data-ttu-id="b846f-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="b846f-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="b846f-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="b846f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b846f-112">*lpBuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="b846f-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="b846f-113">Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die die Eingabepuffer Daten empfangen.</span><span class="sxs-lookup"><span data-stu-id="b846f-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="b846f-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="b846f-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="b846f-115">Die Größe des Arrays, auf das durch den *lpBuffer* -Parameter in Array Elementen verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="b846f-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="b846f-116">*lpnumofeventsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="b846f-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="b846f-117">Ein Zeiger auf eine Variable, die die Anzahl der gelesenen Eingabedaten Sätze empfängt.</span><span class="sxs-lookup"><span data-stu-id="b846f-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="b846f-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b846f-118">Return value</span></span>
------------

<span data-ttu-id="b846f-119">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="b846f-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b846f-120">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="b846f-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b846f-121">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b846f-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b846f-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b846f-122">Remarks</span></span>
-------

<span data-ttu-id="b846f-123">Wenn die Anzahl der angeforderten Datensätze die Anzahl der Datensätze überschreitet, die im Puffer verfügbar sind, wird die verfügbare Zahl gelesen.</span><span class="sxs-lookup"><span data-stu-id="b846f-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="b846f-124">Wenn keine Daten verfügbar sind, gibt die Funktion sofort zurück.</span><span class="sxs-lookup"><span data-stu-id="b846f-124">If no data is available, the function returns immediately.</span></span>

<span data-ttu-id="b846f-125">Diese Funktion verwendet entweder Unicode-Zeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole.</span><span class="sxs-lookup"><span data-stu-id="b846f-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="b846f-126">Die Standard Codepage der Konsole wird zunächst auf die OEM-Codepage des Systems eingestellt.</span><span class="sxs-lookup"><span data-stu-id="b846f-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="b846f-127">Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**setconsolecp**](setconsolecp.md) oder [**setconsoleoutputcp**](setconsoleoutputcp.md) , oder verwenden Sie die Befehle **chcp** oder **Mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="b846f-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="b846f-128">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b846f-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b846f-129">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b846f-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b846f-130">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b846f-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b846f-131">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b846f-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b846f-132">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="b846f-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b846f-133">Header</span><span class="sxs-lookup"><span data-stu-id="b846f-133">Header</span></span></p></td>
<td><span data-ttu-id="b846f-134">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b846f-134">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b846f-135">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="b846f-135">Library</span></span></p></td>
<td><span data-ttu-id="b846f-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b846f-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b846f-137">DLL</span><span class="sxs-lookup"><span data-stu-id="b846f-137">DLL</span></span></p></td>
<td><span data-ttu-id="b846f-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b846f-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b846f-139">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="b846f-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="b846f-140">" <strong>Peer</strong> " (Unicode) und " <strong>ppconsoleinputa</strong> " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b846f-140"><strong>PeekConsoleInputW</strong> (Unicode) and <strong>PeekConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b846f-141"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b846f-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b846f-142">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b846f-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b846f-143">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b846f-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="b846f-144">**Setconsolecp**</span><span class="sxs-lookup"><span data-stu-id="b846f-144">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b846f-145">**Setconsoleoutputcp**</span><span class="sxs-lookup"><span data-stu-id="b846f-145">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="b846f-146">**Schreibconsoleinput**</span><span class="sxs-lookup"><span data-stu-id="b846f-146">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="b846f-147">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="b846f-147">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




