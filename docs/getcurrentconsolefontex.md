---
title: Getcurrentconsolefontex-Funktion
description: Siehe Referenzinformationen zur getcurrentconsolefontex-Funktion, die erweiterte Informationen zur aktuell verwendeten Konsolen Schriftart abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e499cdb51a5ca71948dd40ebd3d4d151f2d71a8a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038728"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="03302-104">Getcurrentconsolefontex-Funktion</span><span class="sxs-lookup"><span data-stu-id="03302-104">GetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="03302-105">Ruft erweiterte Informationen über die aktuelle Konsolen Schriftart ab.</span><span class="sxs-lookup"><span data-stu-id="03302-105">Retrieves extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="03302-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="03302-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="03302-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="03302-107">Parameters</span></span>

<span data-ttu-id="03302-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="03302-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="03302-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="03302-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="03302-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="03302-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="03302-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="03302-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="03302-112">*bmaximumwindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="03302-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="03302-113">Wenn dieser Parameter **true** ist, werden für die maximale Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="03302-113">If this parameter is **TRUE** , font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="03302-114">Wenn dieser Parameter **false** ist, werden für die aktuelle Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="03302-114">If this parameter is **FALSE** , font information is retrieved for the current window size.</span></span>

<span data-ttu-id="03302-115">*lpconsolecurrentfontex* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="03302-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="03302-116">Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md) -Struktur, die die angeforderten Schriftart Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="03302-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="03302-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="03302-117">Return value</span></span>

<span data-ttu-id="03302-118">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="03302-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="03302-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="03302-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="03302-120">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="03302-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="03302-121">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="03302-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="03302-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="03302-122">Minimum supported client</span></span> | <span data-ttu-id="03302-123">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="03302-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="03302-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="03302-124">Minimum supported server</span></span> | <span data-ttu-id="03302-125">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="03302-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="03302-126">Header</span><span class="sxs-lookup"><span data-stu-id="03302-126">Header</span></span> | <span data-ttu-id="03302-127">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="03302-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="03302-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="03302-128">Library</span></span> | <span data-ttu-id="03302-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="03302-129">Kernel32.lib</span></span> |
| <span data-ttu-id="03302-130">DLL</span><span class="sxs-lookup"><span data-stu-id="03302-130">DLL</span></span> | <span data-ttu-id="03302-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="03302-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="03302-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="03302-132">See also</span></span>

[<span data-ttu-id="03302-133">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="03302-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="03302-134">**Konsolen \_ Schriftart \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="03302-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)
