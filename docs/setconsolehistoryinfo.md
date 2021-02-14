---
title: Setconsolehistoryinfo-Funktion
description: Legt die Verlaufs Einstellungen für die Windows-Konsole des aufrufenden Prozesses fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 3c2dcce41994929292253793fe94512ab7bc5a01
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357650"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="db835-104">Setconsolehistoryinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="db835-104">SetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="db835-105">Legt die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses fest.</span><span class="sxs-lookup"><span data-stu-id="db835-105">Sets the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="db835-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="db835-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="db835-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="db835-107">Parameters</span></span>

<span data-ttu-id="db835-108">*lpconsolehistoryinfo* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="db835-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="db835-109">Ein Zeiger auf eine [**Konsolen \_ Verlauf- \_ Informations**](console-history-info.md) Struktur, die die Verlaufs Einstellungen für die Konsole des Prozesses enthält.</span><span class="sxs-lookup"><span data-stu-id="db835-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="db835-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="db835-110">Return value</span></span>

<span data-ttu-id="db835-111">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="db835-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="db835-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="db835-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="db835-113">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="db835-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="db835-114">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="db835-114">Remarks</span></span>

<span data-ttu-id="db835-115">Wenn es sich bei dem aufrufenden Prozess nicht um einen Konsolen Prozess handelt, schlägt die Funktion fehl und legt den letzten Fehlercode auf " **Fehler \_ Zugriff \_ verweigert**" fest.</span><span class="sxs-lookup"><span data-stu-id="db835-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED**.</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="db835-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="db835-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="db835-117">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="db835-117">Minimum supported client</span></span> | <span data-ttu-id="db835-118">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="db835-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="db835-119">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="db835-119">Minimum supported server</span></span> | <span data-ttu-id="db835-120">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="db835-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="db835-121">Header</span><span class="sxs-lookup"><span data-stu-id="db835-121">Header</span></span> | <span data-ttu-id="db835-122">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="db835-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="db835-123">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="db835-123">Library</span></span> | <span data-ttu-id="db835-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="db835-124">Kernel32.lib</span></span> |
| <span data-ttu-id="db835-125">DLL</span><span class="sxs-lookup"><span data-stu-id="db835-125">DLL</span></span> | <span data-ttu-id="db835-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="db835-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="db835-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="db835-127">See also</span></span>

[<span data-ttu-id="db835-128">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="db835-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="db835-129">**Informationen zum Konsolen \_ Verlauf \_**</span><span class="sxs-lookup"><span data-stu-id="db835-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="db835-130">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="db835-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)