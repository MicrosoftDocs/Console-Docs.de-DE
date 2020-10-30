---
title: Getconsolecursorinfo-Funktion
description: Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 2d9869c5c291addaf94a06fa67e11e3195ead686
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038918"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="1ddc7-104">Getconsolecursorinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="1ddc7-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1ddc7-105">Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab.</span><span class="sxs-lookup"><span data-stu-id="1ddc7-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ddc7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ddc7-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="1ddc7-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1ddc7-107">Parameters</span></span>

<span data-ttu-id="1ddc7-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="1ddc7-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1ddc7-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="1ddc7-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1ddc7-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="1ddc7-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="1ddc7-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="1ddc7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1ddc7-112">*lpconsolecursorinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="1ddc7-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="1ddc7-113">Ein Zeiger auf eine [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur, die Informationen über den Cursor der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="1ddc7-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ddc7-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1ddc7-114">Return value</span></span>

<span data-ttu-id="1ddc7-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="1ddc7-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1ddc7-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="1ddc7-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1ddc7-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1ddc7-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="1ddc7-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1ddc7-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="1ddc7-119">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="1ddc7-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1ddc7-120">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="1ddc7-120">Minimum supported client</span></span> | <span data-ttu-id="1ddc7-121">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1ddc7-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ddc7-122">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="1ddc7-122">Minimum supported server</span></span> | <span data-ttu-id="1ddc7-123">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="1ddc7-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ddc7-124">Header</span><span class="sxs-lookup"><span data-stu-id="1ddc7-124">Header</span></span> | <span data-ttu-id="1ddc7-125">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1ddc7-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1ddc7-126">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="1ddc7-126">Library</span></span> | <span data-ttu-id="1ddc7-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1ddc7-127">Kernel32.lib</span></span> |
| <span data-ttu-id="1ddc7-128">DLL</span><span class="sxs-lookup"><span data-stu-id="1ddc7-128">DLL</span></span> | <span data-ttu-id="1ddc7-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1ddc7-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="1ddc7-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1ddc7-130">See also</span></span>

[<span data-ttu-id="1ddc7-131">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1ddc7-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1ddc7-132">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="1ddc7-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="1ddc7-133">**Konsolen \_ Cursor \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="1ddc7-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="1ddc7-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="1ddc7-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)
