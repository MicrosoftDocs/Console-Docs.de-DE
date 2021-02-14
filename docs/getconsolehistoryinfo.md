---
title: Getconsolehistoryinfo-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur getconsolehistoryinfo-Funktion, die die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: a26dbeb2a873bd780f91c240bf2658cde11b45ec
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359020"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="bd544-104">Getconsolehistoryinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="bd544-104">GetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="bd544-105">Ruft die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses ab.</span><span class="sxs-lookup"><span data-stu-id="bd544-105">Retrieves the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd544-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bd544-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="bd544-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="bd544-107">Parameters</span></span>

<span data-ttu-id="bd544-108">*lpconsolehistoryinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="bd544-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="bd544-109">Ein Zeiger auf eine [**Konsolen \_ Verlauf- \_ Informations**](console-history-info.md) Struktur, die die Verlaufs Einstellungen für die Konsole des aufrufenden Prozesses empfängt.</span><span class="sxs-lookup"><span data-stu-id="bd544-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd544-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="bd544-110">Return value</span></span>

<span data-ttu-id="bd544-111">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="bd544-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="bd544-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="bd544-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bd544-113">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="bd544-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="bd544-114">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="bd544-114">Remarks</span></span>

<span data-ttu-id="bd544-115">Wenn es sich bei dem aufrufenden Prozess nicht um einen Konsolen Prozess handelt, schlägt die Funktion fehl und legt den letzten Fehler auf " **Fehler \_ Zugriff \_ verweigert**" fest.</span><span class="sxs-lookup"><span data-stu-id="bd544-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="bd544-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="bd544-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="bd544-117">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="bd544-117">Minimum supported client</span></span> | <span data-ttu-id="bd544-118">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="bd544-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="bd544-119">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="bd544-119">Minimum supported server</span></span> | <span data-ttu-id="bd544-120">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="bd544-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="bd544-121">Header</span><span class="sxs-lookup"><span data-stu-id="bd544-121">Header</span></span> | <span data-ttu-id="bd544-122">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bd544-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="bd544-123">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="bd544-123">Library</span></span> | <span data-ttu-id="bd544-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="bd544-124">Kernel32.lib</span></span> |
| <span data-ttu-id="bd544-125">DLL</span><span class="sxs-lookup"><span data-stu-id="bd544-125">DLL</span></span> | <span data-ttu-id="bd544-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bd544-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="bd544-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bd544-127">See also</span></span>

[<span data-ttu-id="bd544-128">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="bd544-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bd544-129">**Informationen zum Konsolen \_ Verlauf \_**</span><span class="sxs-lookup"><span data-stu-id="bd544-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="bd544-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="bd544-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)