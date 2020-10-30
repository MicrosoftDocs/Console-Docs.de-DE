---
title: CONSOLE_HISTORY_INFO-Struktur
description: Siehe Referenzinformationen zur CONSOLE_HISTORY_INFO Struktur, die Informationen über den Konsolen Verlauf enthält.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039218"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="7d4ed-104">Struktur der Konsolen \_ Verlauf- \_ Informationen</span><span class="sxs-lookup"><span data-stu-id="7d4ed-104">CONSOLE\_HISTORY\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="7d4ed-105">Enthält Informationen über den Konsolen Verlauf.</span><span class="sxs-lookup"><span data-stu-id="7d4ed-105">Contains information about the console history.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d4ed-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d4ed-106">Syntax</span></span>

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a><span data-ttu-id="7d4ed-107">Member</span><span class="sxs-lookup"><span data-stu-id="7d4ed-107">Members</span></span>

<span data-ttu-id="7d4ed-108">**CBSIZE**</span><span class="sxs-lookup"><span data-stu-id="7d4ed-108">**cbSize**</span></span>  
<span data-ttu-id="7d4ed-109">Die Größe der-Struktur in Bytes.</span><span class="sxs-lookup"><span data-stu-id="7d4ed-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="7d4ed-110">Legen Sie diesen Member auf fest `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="7d4ed-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="7d4ed-111">**Historybuffersize**</span><span class="sxs-lookup"><span data-stu-id="7d4ed-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="7d4ed-112">Die Anzahl der Befehle, die in jedem Verlaufs Puffer aufbewahrt werden.</span><span class="sxs-lookup"><span data-stu-id="7d4ed-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="7d4ed-113">**"Numofhistorybuffers"**</span><span class="sxs-lookup"><span data-stu-id="7d4ed-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="7d4ed-114">Die Anzahl der Verlaufs Puffer, die für diesen Konsolen Prozess aufbewahrt werden.</span><span class="sxs-lookup"><span data-stu-id="7d4ed-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="7d4ed-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="7d4ed-115">**dwFlags**</span></span>  
<span data-ttu-id="7d4ed-116">Dieser Parameter kann NULL oder der folgende Wert sein.</span><span class="sxs-lookup"><span data-stu-id="7d4ed-116">This parameter can be zero or the following value.</span></span>

| <span data-ttu-id="7d4ed-117">Wert</span><span class="sxs-lookup"><span data-stu-id="7d4ed-117">Value</span></span> | <span data-ttu-id="7d4ed-118">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="7d4ed-118">Meaning</span></span> |
|-|-|
| <span data-ttu-id="7d4ed-119">**HISTORY_NO_DUP_FLAG** 0x1</span><span class="sxs-lookup"><span data-stu-id="7d4ed-119">**HISTORY_NO_DUP_FLAG** 0x1</span></span> | <span data-ttu-id="7d4ed-120">Doppelte Einträge werden nicht im Verlaufs Puffer gespeichert.</span><span class="sxs-lookup"><span data-stu-id="7d4ed-120">Duplicate entries will not be stored in the history buffer.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d4ed-121">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="7d4ed-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7d4ed-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="7d4ed-122">Minimum supported client</span></span> | <span data-ttu-id="7d4ed-123">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="7d4ed-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="7d4ed-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="7d4ed-124">Minimum supported server</span></span> | <span data-ttu-id="7d4ed-125">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="7d4ed-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="7d4ed-126">Header</span><span class="sxs-lookup"><span data-stu-id="7d4ed-126">Header</span></span> | <span data-ttu-id="7d4ed-127">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7d4ed-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="7d4ed-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7d4ed-128">See also</span></span>

[<span data-ttu-id="7d4ed-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="7d4ed-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="7d4ed-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="7d4ed-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)
