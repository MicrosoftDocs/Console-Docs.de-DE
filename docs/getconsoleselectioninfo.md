---
title: Getconsoleselectioninfo-Funktion
description: Siehe Referenzinformationen zur getconsoleselectioninfo-Funktion, die Informationen über die aktuelle Konsolen Auswahl abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d29a960bc6b8d96d98e0667084e31354f2aa9653
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059706"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="0834b-104">Getconsoleselectioninfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="0834b-104">GetConsoleSelectionInfo function</span></span>


<span data-ttu-id="0834b-105">Ruft Informationen über die aktuelle Konsolen Auswahl ab.</span><span class="sxs-lookup"><span data-stu-id="0834b-105">Retrieves information about the current console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="0834b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0834b-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

<a name="parameters"></a><span data-ttu-id="0834b-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="0834b-107">Parameters</span></span>
----------

<span data-ttu-id="0834b-108">*lpconsoleselectioninfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="0834b-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="0834b-109">Ein Zeiger auf eine [**Konsolen \_ Auswahl \_ Info**](console-selection-info-str.md) -Struktur, die die Auswahl Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="0834b-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

<a name="return-value"></a><span data-ttu-id="0834b-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0834b-110">Return value</span></span>
------------

<span data-ttu-id="0834b-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="0834b-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0834b-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="0834b-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0834b-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="0834b-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="0834b-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0834b-114">Remarks</span></span>
-------

<span data-ttu-id="0834b-115">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="0834b-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="0834b-116">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="0834b-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="0834b-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0834b-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0834b-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0834b-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0834b-119">Windows XP [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0834b-119">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0834b-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0834b-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0834b-121">Windows Server 2003 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="0834b-121">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0834b-122">Header</span><span class="sxs-lookup"><span data-stu-id="0834b-122">Header</span></span></p></td>
<td><span data-ttu-id="0834b-123">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0834b-123">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0834b-124">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="0834b-124">Library</span></span></p></td>
<td><span data-ttu-id="0834b-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="0834b-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0834b-126">DLL</span><span class="sxs-lookup"><span data-stu-id="0834b-126">DLL</span></span></p></td>
<td><span data-ttu-id="0834b-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0834b-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0834b-128"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0834b-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0834b-129">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="0834b-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0834b-130">Konsolen Auswahl</span><span class="sxs-lookup"><span data-stu-id="0834b-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="0834b-131">**Konsolen \_ Auswahl \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="0834b-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

 

 




