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
ms.openlocfilehash: e7932d286723886f671be051294fcffb23155bf6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358880"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="13da1-104">Getcurrentconsolefontex-Funktion</span><span class="sxs-lookup"><span data-stu-id="13da1-104">GetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="13da1-105">Ruft erweiterte Informationen über die aktuelle Konsolen Schriftart ab.</span><span class="sxs-lookup"><span data-stu-id="13da1-105">Retrieves extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="13da1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="13da1-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="13da1-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="13da1-107">Parameters</span></span>

<span data-ttu-id="13da1-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="13da1-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="13da1-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="13da1-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="13da1-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="13da1-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="13da1-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="13da1-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="13da1-112">*bmaximumwindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="13da1-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="13da1-113">Wenn dieser Parameter **true** ist, werden für die maximale Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="13da1-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="13da1-114">Wenn dieser Parameter **false** ist, werden für die aktuelle Fenstergröße Schriftart Informationen abgerufen.</span><span class="sxs-lookup"><span data-stu-id="13da1-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="13da1-115">*lpconsolecurrentfontex* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="13da1-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="13da1-116">Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md) -Struktur, die die angeforderten Schriftart Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="13da1-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="13da1-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="13da1-117">Return value</span></span>

<span data-ttu-id="13da1-118">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="13da1-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="13da1-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="13da1-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="13da1-120">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="13da1-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="13da1-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="13da1-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="13da1-122">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="13da1-122">Minimum supported client</span></span> | <span data-ttu-id="13da1-123">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="13da1-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="13da1-124">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="13da1-124">Minimum supported server</span></span> | <span data-ttu-id="13da1-125">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="13da1-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="13da1-126">Header</span><span class="sxs-lookup"><span data-stu-id="13da1-126">Header</span></span> | <span data-ttu-id="13da1-127">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="13da1-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="13da1-128">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="13da1-128">Library</span></span> | <span data-ttu-id="13da1-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="13da1-129">Kernel32.lib</span></span> |
| <span data-ttu-id="13da1-130">DLL</span><span class="sxs-lookup"><span data-stu-id="13da1-130">DLL</span></span> | <span data-ttu-id="13da1-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="13da1-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="13da1-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="13da1-132">See also</span></span>

[<span data-ttu-id="13da1-133">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="13da1-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="13da1-134">**Konsolen \_ Schriftart \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="13da1-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)