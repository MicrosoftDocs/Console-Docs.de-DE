---
title: CONSOLE_HISTORY_INFO Struktur
description: Siehe Referenzinformationen zur CONSOLE_HISTORY_INFO Struktur, die Informationen über den Konsolen Verlauf enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: ee0161f0c4aac5a280fd18260ebbb1f7ca57d54a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060459"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="445bb-104">Struktur der Konsolen \_ Verlauf- \_ Informationen</span><span class="sxs-lookup"><span data-stu-id="445bb-104">CONSOLE\_HISTORY\_INFO structure</span></span>


<span data-ttu-id="445bb-105">Enthält Informationen über den Konsolen Verlauf.</span><span class="sxs-lookup"><span data-stu-id="445bb-105">Contains information about the console history.</span></span>

<a name="syntax"></a><span data-ttu-id="445bb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="445bb-106">Syntax</span></span>
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

<a name="members"></a><span data-ttu-id="445bb-107">Member</span><span class="sxs-lookup"><span data-stu-id="445bb-107">Members</span></span>
-------

<span data-ttu-id="445bb-108">**CBSIZE**</span><span class="sxs-lookup"><span data-stu-id="445bb-108">**cbSize**</span></span>  
<span data-ttu-id="445bb-109">Die Größe der-Struktur in Bytes.</span><span class="sxs-lookup"><span data-stu-id="445bb-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="445bb-110">Legen Sie diesen Member auf fest `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="445bb-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="445bb-111">**Historybuffersize**</span><span class="sxs-lookup"><span data-stu-id="445bb-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="445bb-112">Die Anzahl der Befehle, die in jedem Verlaufs Puffer aufbewahrt werden.</span><span class="sxs-lookup"><span data-stu-id="445bb-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="445bb-113">**"Numofhistorybuffers"**</span><span class="sxs-lookup"><span data-stu-id="445bb-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="445bb-114">Die Anzahl der Verlaufs Puffer, die für diesen Konsolen Prozess aufbewahrt werden.</span><span class="sxs-lookup"><span data-stu-id="445bb-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="445bb-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="445bb-115">**dwFlags**</span></span>  
<span data-ttu-id="445bb-116">Dieser Parameter kann NULL oder der folgende Wert sein.</span><span class="sxs-lookup"><span data-stu-id="445bb-116">This parameter can be zero or the following value.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="445bb-117">Wert</span><span class="sxs-lookup"><span data-stu-id="445bb-117">Value</span></span></th>
<th><span data-ttu-id="445bb-118">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="445bb-118">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="445bb-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span><span class="sxs-lookup"><span data-stu-id="445bb-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span></span></td>
<td><p><span data-ttu-id="445bb-120">Doppelte Einträge werden nicht im Verlaufs Puffer gespeichert.</span><span class="sxs-lookup"><span data-stu-id="445bb-120">Duplicate entries will not be stored in the history buffer.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a><span data-ttu-id="445bb-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="445bb-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="445bb-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="445bb-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="445bb-123">Windows Vista [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="445bb-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="445bb-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="445bb-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="445bb-125">Windows Server 2008 [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="445bb-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="445bb-126">Header</span><span class="sxs-lookup"><span data-stu-id="445bb-126">Header</span></span></p></td>
<td><span data-ttu-id="445bb-127">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="445bb-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="445bb-128"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="445bb-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="445bb-129">**Getconsolehistoryinfo**</span><span class="sxs-lookup"><span data-stu-id="445bb-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="445bb-130">**Setconsolehistoryinfo**</span><span class="sxs-lookup"><span data-stu-id="445bb-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 




