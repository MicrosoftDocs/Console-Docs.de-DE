---
title: Addconsolealias-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur addconsolealias-Funktion, die einen Konsolen Alias für die angegebene ausführbare Datei definiert.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f2396122e693ab76ddf4e4e0bcdb2d38a2c042b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037552"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="e74f4-104">Addconsolealias-Funktion</span><span class="sxs-lookup"><span data-stu-id="e74f4-104">AddConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e74f4-105">Definiert einen konsolenalias für die angegebene ausführbare Datei.</span><span class="sxs-lookup"><span data-stu-id="e74f4-105">Defines a console alias for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="e74f4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e74f4-106">Syntax</span></span>

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a><span data-ttu-id="e74f4-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="e74f4-107">Parameters</span></span>

<span data-ttu-id="e74f4-108">*Quelle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e74f4-108">*Source* \[in\]</span></span>  
<span data-ttu-id="e74f4-109">Der konsolenalias, der dem durch *target* angegebenen Text zugeordnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e74f4-109">The console alias to be mapped to the text specified by *Target* .</span></span>

<span data-ttu-id="e74f4-110">*Ziel* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e74f4-110">*Target* \[in\]</span></span>  
<span data-ttu-id="e74f4-111">Der Text, der als *Quelle* ersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e74f4-111">The text to be substituted for *Source* .</span></span> <span data-ttu-id="e74f4-112">Wenn dieser Parameter **null** ist, wird der Konsolen Alias entfernt.</span><span class="sxs-lookup"><span data-stu-id="e74f4-112">If this parameter is **NULL** , then the console alias is removed.</span></span>

<span data-ttu-id="e74f4-113">*EXEName* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e74f4-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="e74f4-114">Der Name der ausführbaren Datei, für die der konsolenalias definiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e74f4-114">The name of the executable file for which the console alias is to be defined.</span></span>

## <a name="return-value"></a><span data-ttu-id="e74f4-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e74f4-115">Return value</span></span>

<span data-ttu-id="e74f4-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert " **true** ".</span><span class="sxs-lookup"><span data-stu-id="e74f4-116">If the function succeeds, the return value is **TRUE** .</span></span>

<span data-ttu-id="e74f4-117">Wenn die Funktion fehlschlägt, ist der Rückgabewert **false** .</span><span class="sxs-lookup"><span data-stu-id="e74f4-117">If the function fails, the return value is **FALSE** .</span></span> <span data-ttu-id="e74f4-118">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e74f4-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="e74f4-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="e74f4-119">Remarks</span></span>

<span data-ttu-id="e74f4-120">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="e74f4-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="e74f4-121">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="e74f4-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a><span data-ttu-id="e74f4-122">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e74f4-122">Examples</span></span>

<span data-ttu-id="e74f4-123">Ein Beispiel finden Sie unter [Konsolen Aliase](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="e74f4-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e74f4-124">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="e74f4-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e74f4-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e74f4-125">Minimum supported client</span></span> | <span data-ttu-id="e74f4-126">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e74f4-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e74f4-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e74f4-127">Minimum supported server</span></span> | <span data-ttu-id="e74f4-128">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e74f4-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e74f4-129">Header</span><span class="sxs-lookup"><span data-stu-id="e74f4-129">Header</span></span> | <span data-ttu-id="e74f4-130">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e74f4-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e74f4-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e74f4-131">Library</span></span> | <span data-ttu-id="e74f4-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e74f4-132">Kernel32.lib</span></span> |
| <span data-ttu-id="e74f4-133">DLL</span><span class="sxs-lookup"><span data-stu-id="e74f4-133">DLL</span></span> | <span data-ttu-id="e74f4-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e74f4-134">Kernel32.dll</span></span> |
| <span data-ttu-id="e74f4-135">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="e74f4-135">Unicode and ANSI names</span></span> | <span data-ttu-id="e74f4-136">**Addconsolealiasw** (Unicode) und **addconsolealiasa** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="e74f4-136">**AddConsoleAliasW** (Unicode) and **AddConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e74f4-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e74f4-137">See also</span></span>

[<span data-ttu-id="e74f4-138">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="e74f4-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="e74f4-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e74f4-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e74f4-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="e74f4-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="e74f4-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="e74f4-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="e74f4-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="e74f4-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
