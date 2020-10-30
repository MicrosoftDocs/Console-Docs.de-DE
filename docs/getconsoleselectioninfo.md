---
title: Getconsoleselectioninfo-Funktion
description: Siehe Referenzinformationen zur getconsoleselectioninfo-Funktion, die Informationen über die aktuelle Konsolen Auswahl abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 2f1052940b468455121cc363317c2b7cfa8246b3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038848"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="b189b-104">Getconsoleselectioninfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="b189b-104">GetConsoleSelectionInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b189b-105">Ruft Informationen über die aktuelle Konsolen Auswahl ab.</span><span class="sxs-lookup"><span data-stu-id="b189b-105">Retrieves information about the current console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="b189b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b189b-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

## <a name="parameters"></a><span data-ttu-id="b189b-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="b189b-107">Parameters</span></span>

<span data-ttu-id="b189b-108">*lpconsoleselectioninfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="b189b-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="b189b-109">Ein Zeiger auf eine [**Konsolen \_ Auswahl \_ Info**](console-selection-info-str.md) -Struktur, die die Auswahl Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="b189b-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

## <a name="return-value"></a><span data-ttu-id="b189b-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b189b-110">Return value</span></span>

<span data-ttu-id="b189b-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="b189b-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b189b-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="b189b-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b189b-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b189b-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="b189b-114">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="b189b-114">Remarks</span></span>

<span data-ttu-id="b189b-115">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="b189b-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="b189b-116">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="b189b-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="b189b-117">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="b189b-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b189b-118">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="b189b-118">Minimum supported client</span></span> | <span data-ttu-id="b189b-119">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="b189b-119">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="b189b-120">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="b189b-120">Minimum supported server</span></span> | <span data-ttu-id="b189b-121">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="b189b-121">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="b189b-122">Header</span><span class="sxs-lookup"><span data-stu-id="b189b-122">Header</span></span> | <span data-ttu-id="b189b-123">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b189b-123">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b189b-124">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="b189b-124">Library</span></span> | <span data-ttu-id="b189b-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b189b-125">Kernel32.lib</span></span> |
| <span data-ttu-id="b189b-126">DLL</span><span class="sxs-lookup"><span data-stu-id="b189b-126">DLL</span></span> | <span data-ttu-id="b189b-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b189b-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b189b-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b189b-128">See also</span></span>

[<span data-ttu-id="b189b-129">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b189b-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b189b-130">Konsolenauswahl</span><span class="sxs-lookup"><span data-stu-id="b189b-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="b189b-131">**Konsolen \_ Auswahl \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="b189b-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)
