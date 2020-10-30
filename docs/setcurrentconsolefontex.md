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
ms.openlocfilehash: 1ba89b90a0362261aafbe5ac6462224b3c0172dc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037052"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="041dd-104">Setcurrentconsolefontex-Funktion</span><span class="sxs-lookup"><span data-stu-id="041dd-104">SetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="041dd-105">Legt erweiterte Informationen über die aktuelle Konsolen Schriftart fest.</span><span class="sxs-lookup"><span data-stu-id="041dd-105">Sets extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="041dd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="041dd-106">Syntax</span></span>

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="041dd-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="041dd-107">Parameters</span></span>

<span data-ttu-id="041dd-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="041dd-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="041dd-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="041dd-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="041dd-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="041dd-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="041dd-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="041dd-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="041dd-112">*bmaximumwindow* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="041dd-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="041dd-113">Wenn dieser Parameter auf **true** festgelegt ist, werden für die maximale Fenstergröße Schriftart Informationen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="041dd-113">If this parameter is **TRUE** , font information is set for the maximum window size.</span></span> <span data-ttu-id="041dd-114">Wenn dieser Parameter auf **false** festgelegt ist, werden für die aktuelle Fenstergröße Schriftart Informationen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="041dd-114">If this parameter is **FALSE** , font information is set for the current window size.</span></span>

<span data-ttu-id="041dd-115">*lpconsolecurrentfontex* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="041dd-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="041dd-116">Ein Zeiger auf eine [**Konsolen \_ Schriftart \_ INFOEX**](console-font-infoex.md) -Struktur, die die Schriftart Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="041dd-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="041dd-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="041dd-117">Return value</span></span>

<span data-ttu-id="041dd-118">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="041dd-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="041dd-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="041dd-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="041dd-120">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="041dd-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="041dd-121">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="041dd-121">Remarks</span></span>

<span data-ttu-id="041dd-122">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="041dd-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="041dd-123">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="041dd-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="041dd-124">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="041dd-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="041dd-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="041dd-125">Minimum supported client</span></span> | <span data-ttu-id="041dd-126">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="041dd-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="041dd-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="041dd-127">Minimum supported server</span></span> | <span data-ttu-id="041dd-128">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="041dd-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="041dd-129">Header</span><span class="sxs-lookup"><span data-stu-id="041dd-129">Header</span></span> | <span data-ttu-id="041dd-130">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="041dd-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="041dd-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="041dd-131">Library</span></span> | <span data-ttu-id="041dd-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="041dd-132">Kernel32.lib</span></span> |
| <span data-ttu-id="041dd-133">DLL</span><span class="sxs-lookup"><span data-stu-id="041dd-133">DLL</span></span> | <span data-ttu-id="041dd-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="041dd-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="041dd-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="041dd-135">See also</span></span>

[<span data-ttu-id="041dd-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="041dd-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="041dd-137">**Konsolen \_ Schriftart \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="041dd-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)
