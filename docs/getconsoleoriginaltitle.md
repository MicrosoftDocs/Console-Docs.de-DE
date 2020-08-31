---
title: Getconsoleoriginaltitle-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur getconsoleoriginaltitle-Funktion, die den ursprünglichen Titel für das aktuelle Konsolenfenster abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059738"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="623b7-104">Getconsoleoriginaltitle-Funktion</span><span class="sxs-lookup"><span data-stu-id="623b7-104">GetConsoleOriginalTitle function</span></span>


<span data-ttu-id="623b7-105">Ruft den ursprünglichen Titel für das aktuelle Konsolenfenster ab.</span><span class="sxs-lookup"><span data-stu-id="623b7-105">Retrieves the original title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="623b7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="623b7-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="623b7-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="623b7-107">Parameters</span></span>
----------

<span data-ttu-id="623b7-108">*lpconsoletitle* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="623b7-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="623b7-109">Ein Zeiger auf einen Puffer, der eine NULL-terminierte Zeichenfolge mit dem ursprünglichen Titel empfängt.</span><span class="sxs-lookup"><span data-stu-id="623b7-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="623b7-110">*nSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="623b7-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="623b7-111">Die Größe des *lpconsoletitle* -Puffers in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="623b7-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="623b7-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="623b7-112">Return value</span></span>
------------

<span data-ttu-id="623b7-113">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert die Länge der Zeichenfolge, die in den Puffer kopiert wird (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="623b7-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="623b7-114">Wenn der Puffer nicht groß genug ist, um den Titel zu speichern, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt eine \*\* \_ erfolgreiche Fehlermeldung\*\*zurück.</span><span class="sxs-lookup"><span data-stu-id="623b7-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="623b7-115">Wenn die Funktion fehlschlägt, ist der Rückgabewert 0 (null), und [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) gibt den Fehlercode zurück.</span><span class="sxs-lookup"><span data-stu-id="623b7-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="623b7-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="623b7-116">Remarks</span></span>
-------

<span data-ttu-id="623b7-117">Um den Titel für ein Konsolenfenster festzulegen, verwenden Sie die [**setconsoletitle**](setconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="623b7-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="623b7-118">Um die aktuelle Titel Zeichenfolge abzurufen, verwenden Sie die [**getconsoletitle**](getconsoletitle.md) -Funktion.</span><span class="sxs-lookup"><span data-stu-id="623b7-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="623b7-119">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie \*\* \_ Win32 \_ Winnt\*\* als 0x0600 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="623b7-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="623b7-120">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="623b7-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="623b7-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="623b7-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="623b7-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="623b7-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="623b7-123">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="623b7-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="623b7-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="623b7-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="623b7-125">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="623b7-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="623b7-126">Header</span><span class="sxs-lookup"><span data-stu-id="623b7-126">Header</span></span></p></td>
<td><span data-ttu-id="623b7-127">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="623b7-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="623b7-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="623b7-128">Library</span></span></p></td>
<td><span data-ttu-id="623b7-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="623b7-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="623b7-130">DLL</span><span class="sxs-lookup"><span data-stu-id="623b7-130">DLL</span></span></p></td>
<td><span data-ttu-id="623b7-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="623b7-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="623b7-132">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="623b7-132">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="623b7-133"><strong>Getconsoleoriginaltitlew</strong> (Unicode) und <strong>getconsoleoriginaltitlea</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="623b7-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) and <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="623b7-134"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="623b7-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="623b7-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="623b7-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="623b7-136">**Getconsoletitle**</span><span class="sxs-lookup"><span data-stu-id="623b7-136">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="623b7-137">**Setconsoletitle**</span><span class="sxs-lookup"><span data-stu-id="623b7-137">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




