---
title: Setconsolehistoryinfo-Funktion
description: Legt die Verlaufs Einstellungen für die Windows-Konsole des aufrufenden Prozesses fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bf194e154a06efc32510fe811ab89877e283e142
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059659"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="86c24-104">Setconsolehistoryinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="86c24-104">SetConsoleHistoryInfo function</span></span>


<span data-ttu-id="86c24-105">Legt die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses fest.</span><span class="sxs-lookup"><span data-stu-id="86c24-105">Sets the history settings for the calling process's console.</span></span>

<a name="syntax"></a><span data-ttu-id="86c24-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="86c24-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a><span data-ttu-id="86c24-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="86c24-107">Parameters</span></span>
----------

<span data-ttu-id="86c24-108">*lpconsolehistoryinfo* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="86c24-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="86c24-109">Ein Zeiger auf eine [**Konsolen \_ Verlauf- \_ Informations**](console-history-info.md) Struktur, die die Verlaufs Einstellungen für die Konsole des Prozesses enthält.</span><span class="sxs-lookup"><span data-stu-id="86c24-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

<a name="return-value"></a><span data-ttu-id="86c24-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="86c24-110">Return value</span></span>
------------

<span data-ttu-id="86c24-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="86c24-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="86c24-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="86c24-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="86c24-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="86c24-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="86c24-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="86c24-114">Remarks</span></span>
-------

<span data-ttu-id="86c24-115">Wenn es sich bei dem aufrufenden Prozess nicht um einen Konsolen Prozess handelt, schlägt die Funktion fehl und legt den letzten Fehlercode auf " **Fehler \_ Zugriff \_ verweigert**" fest.</span><span class="sxs-lookup"><span data-stu-id="86c24-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED**.</span></span>

<a name="requirements"></a><span data-ttu-id="86c24-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="86c24-116">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="86c24-117">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="86c24-117">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="86c24-118">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="86c24-118">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="86c24-119">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="86c24-119">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="86c24-120">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="86c24-120">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="86c24-121">Header</span><span class="sxs-lookup"><span data-stu-id="86c24-121">Header</span></span></p></td>
<td><span data-ttu-id="86c24-122">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="86c24-122">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="86c24-123">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="86c24-123">Library</span></span></p></td>
<td><span data-ttu-id="86c24-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="86c24-124">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="86c24-125">DLL</span><span class="sxs-lookup"><span data-stu-id="86c24-125">DLL</span></span></p></td>
<td><span data-ttu-id="86c24-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="86c24-126">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="86c24-127"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="86c24-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="86c24-128">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="86c24-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="86c24-129">**Informationen zum Konsolen \_ Verlauf \_**</span><span class="sxs-lookup"><span data-stu-id="86c24-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="86c24-130">**Getconsolehistoryinfo**</span><span class="sxs-lookup"><span data-stu-id="86c24-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

 

 




