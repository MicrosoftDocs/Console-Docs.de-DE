---
title: Setcurrentconsolefontex-Funktion
description: Siehe Referenzinformationen zur setcurrentconsolefontex-Funktion, mit der erweiterte Informationen über die aktuelle Konsolen Schriftart festgelegt werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 87bd942c0d739932ccb51e0af3e47e6fdb29f4da
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358520"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="ad39c-104">Setcurrentconsolefontex-Funktion</span><span class="sxs-lookup"><span data-stu-id="ad39c-104">SetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ad39c-105">Legt erweiterte Informationen über die aktuelle Konsolen Schriftart fest.</span><span class="sxs-lookup"><span data-stu-id="ad39c-105">Sets extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad39c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad39c-106">Syntax</span></span>

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="ad39c-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="ad39c-107">Parameters</span></span>

<span data-ttu-id="ad39c-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ad39c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ad39c-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="ad39c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ad39c-110">Das Handle muss das Zugriffsrecht **GENERIC\_WRITE** besitzen.</span><span class="sxs-lookup"><span data-stu-id="ad39c-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="ad39c-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ad39c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ad39c-112">*bmaximumwindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ad39c-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="ad39c-113">Wenn dieser Parameter auf **true** festgelegt ist, werden für die maximale Fenstergröße Schriftart Informationen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ad39c-113">If this parameter is **TRUE**, font information is set for the maximum window size.</span></span> <span data-ttu-id="ad39c-114">Wenn dieser Parameter auf **false** festgelegt ist, werden für die aktuelle Fenstergröße Schriftart Informationen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ad39c-114">If this parameter is **FALSE**, font information is set for the current window size.</span></span>

<span data-ttu-id="ad39c-115">*lpconsolecurrentfontex* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ad39c-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="ad39c-116">Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md) -Struktur, die die Schriftart Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="ad39c-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="ad39c-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ad39c-117">Return value</span></span>

<span data-ttu-id="ad39c-118">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="ad39c-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ad39c-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="ad39c-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ad39c-120">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="ad39c-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="ad39c-121">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ad39c-121">Remarks</span></span>

<span data-ttu-id="ad39c-122">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="ad39c-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="ad39c-123">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="ad39c-123">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="ad39c-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ad39c-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ad39c-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ad39c-125">Minimum supported client</span></span> | <span data-ttu-id="ad39c-126">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ad39c-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="ad39c-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ad39c-127">Minimum supported server</span></span> | <span data-ttu-id="ad39c-128">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ad39c-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="ad39c-129">Header</span><span class="sxs-lookup"><span data-stu-id="ad39c-129">Header</span></span> | <span data-ttu-id="ad39c-130">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ad39c-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ad39c-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ad39c-131">Library</span></span> | <span data-ttu-id="ad39c-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ad39c-132">Kernel32.lib</span></span> |
| <span data-ttu-id="ad39c-133">DLL</span><span class="sxs-lookup"><span data-stu-id="ad39c-133">DLL</span></span> | <span data-ttu-id="ad39c-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ad39c-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ad39c-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ad39c-135">See also</span></span>

[<span data-ttu-id="ad39c-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ad39c-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ad39c-137">**Konsolen \_ Schriftart \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="ad39c-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)