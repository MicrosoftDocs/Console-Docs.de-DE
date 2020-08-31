---
title: WINDOW_BUFFER_SIZE_RECORD Struktur
description: Siehe Referenzinformationen zur WINDOW_BUFFER_SIZE_RECORD Struktur, in der eine Änderung der Größe des Konsolenbildschirm Puffers beschrieben wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0041c4390fe331302df458965faec0ace2d1888f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060546"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="9faa6-104">\_ \_ \_ Daten Satzstruktur der Fensterpuffer Größe</span><span class="sxs-lookup"><span data-stu-id="9faa6-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>


<span data-ttu-id="9faa6-105">Beschreibt eine Änderung der Größe des Bildschirm Puffers der Konsole.</span><span class="sxs-lookup"><span data-stu-id="9faa6-105">Describes a change in the size of the console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="9faa6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9faa6-106">Syntax</span></span>
------

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

<a name="members"></a><span data-ttu-id="9faa6-107">Member</span><span class="sxs-lookup"><span data-stu-id="9faa6-107">Members</span></span>
-------

<span data-ttu-id="9faa6-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="9faa6-108">**dwSize**</span></span>  
<span data-ttu-id="9faa6-109">Eine [**Koord**](coord-str.md) -Struktur, die die Größe des Konsolenbildschirm Puffers in Zeichen Zellen Spalten und-Zeilen enthält.</span><span class="sxs-lookup"><span data-stu-id="9faa6-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

<a name="remarks"></a><span data-ttu-id="9faa6-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9faa6-110">Remarks</span></span>
-------

<span data-ttu-id="9faa6-111">Puffergrößen Ereignisse werden in den Eingabepuffer eingefügt, wenn sich die Konsole im Fenstermodus befindet (\*\* \_ Fenster \_ Eingabe aktivieren\*\*).</span><span class="sxs-lookup"><span data-stu-id="9faa6-111">Buffer size events are placed in the input buffer when the console is in window-aware mode (**ENABLE\_WINDOW\_INPUT**).</span></span>

<a name="examples"></a><span data-ttu-id="9faa6-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9faa6-112">Examples</span></span>
--------

<span data-ttu-id="9faa6-113">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="9faa6-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="9faa6-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9faa6-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="9faa6-115">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="9faa6-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="9faa6-116">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="9faa6-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9faa6-117">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="9faa6-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="9faa6-118">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="9faa6-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9faa6-119">Header</span><span class="sxs-lookup"><span data-stu-id="9faa6-119">Header</span></span></p></td>
<td><span data-ttu-id="9faa6-120">Wincontypes. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9faa6-120">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="9faa6-121"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9faa6-121"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="9faa6-122">**Koord**</span><span class="sxs-lookup"><span data-stu-id="9faa6-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9faa6-123">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="9faa6-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="9faa6-124">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9faa6-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)

 

 




