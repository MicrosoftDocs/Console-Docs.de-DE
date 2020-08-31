---
title: Getconsolehistoryinfo-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur getconsolehistoryinfo-Funktion, die die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 176cf5517f18f022f00824de02872adcb916f231
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059746"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="4c118-104">Getconsolehistoryinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="4c118-104">GetConsoleHistoryInfo function</span></span>


<span data-ttu-id="4c118-105">Ruft die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses ab.</span><span class="sxs-lookup"><span data-stu-id="4c118-105">Retrieves the history settings for the calling process's console.</span></span>

<a name="syntax"></a><span data-ttu-id="4c118-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c118-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a><span data-ttu-id="4c118-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="4c118-107">Parameters</span></span>
----------

<span data-ttu-id="4c118-108">*lpconsolehistoryinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="4c118-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="4c118-109">Ein Zeiger auf eine [**Konsolen \_ Verlauf- \_ Informations**](console-history-info.md) Struktur, die die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses empfängt.</span><span class="sxs-lookup"><span data-stu-id="4c118-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

<a name="return-value"></a><span data-ttu-id="4c118-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="4c118-110">Return value</span></span>
------------

<span data-ttu-id="4c118-111">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="4c118-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="4c118-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="4c118-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4c118-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4c118-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4c118-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4c118-114">Remarks</span></span>
-------

<span data-ttu-id="4c118-115">Wenn es sich bei dem aufrufenden Prozess nicht um einen Konsolen Prozess handelt, schlägt die Funktion fehl und legt den letzten Fehler auf " **Fehler \_ Zugriff \_ verweigert**" fest.</span><span class="sxs-lookup"><span data-stu-id="4c118-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.</span></span>

<a name="requirements"></a><span data-ttu-id="4c118-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4c118-116">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4c118-117">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="4c118-117">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4c118-118">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4c118-118">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4c118-119">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="4c118-119">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4c118-120">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="4c118-120">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4c118-121">Header</span><span class="sxs-lookup"><span data-stu-id="4c118-121">Header</span></span></p></td>
<td><span data-ttu-id="4c118-122">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4c118-122">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4c118-123">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="4c118-123">Library</span></span></p></td>
<td><span data-ttu-id="4c118-124">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4c118-124">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4c118-125">DLL</span><span class="sxs-lookup"><span data-stu-id="4c118-125">DLL</span></span></p></td>
<td><span data-ttu-id="4c118-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4c118-126">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4c118-127"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4c118-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4c118-128">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="4c118-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4c118-129">**Informationen zum Konsolen \_ Verlauf \_**</span><span class="sxs-lookup"><span data-stu-id="4c118-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="4c118-130">**Setconsolehistoryinfo**</span><span class="sxs-lookup"><span data-stu-id="4c118-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 




