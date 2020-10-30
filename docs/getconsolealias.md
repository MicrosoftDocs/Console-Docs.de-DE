---
title: Getconsolealias-Funktion
description: Ruft den Text für den angegebenen konsolenalias und den Namen der ausführbaren Datei ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 37c441c48c2bb71fc8e590d4f8a80032561f833e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039028"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="94419-104">Getconsolealias-Funktion</span><span class="sxs-lookup"><span data-stu-id="94419-104">GetConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="94419-105">Ruft den Text für den angegebenen konsolenalias und die ausführbare Datei ab.</span><span class="sxs-lookup"><span data-stu-id="94419-105">Retrieves the text for the specified console alias and executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="94419-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="94419-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="94419-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="94419-107">Parameters</span></span>

<span data-ttu-id="94419-108">*lpSource* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="94419-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="94419-109">Der konsolenalias, dessen Text abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="94419-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="94419-110">*lptargetbuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="94419-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="94419-111">Ein Zeiger auf einen Puffer, der den dem Konsolen Alias zugeordneten Text empfängt.</span><span class="sxs-lookup"><span data-stu-id="94419-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="94419-112">*Targetbufferlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="94419-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="94419-113">Die Größe des Puffers, auf den von *lptargetbuffer* verwiesen wird (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="94419-113">The size of the buffer pointed to by *lpTargetBuffer* , in bytes.</span></span>

<span data-ttu-id="94419-114">*lpexename* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="94419-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="94419-115">Der Name der ausführbaren Datei.</span><span class="sxs-lookup"><span data-stu-id="94419-115">The name of the executable file.</span></span>

## <a name="return-value"></a><span data-ttu-id="94419-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="94419-116">Return value</span></span>

<span data-ttu-id="94419-117">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="94419-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="94419-118">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="94419-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="94419-119">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="94419-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="94419-120">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="94419-120">Remarks</span></span>

<span data-ttu-id="94419-121">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="94419-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="94419-122">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="94419-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="94419-123">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="94419-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="94419-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="94419-124">Minimum supported client</span></span> | <span data-ttu-id="94419-125">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="94419-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="94419-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="94419-126">Minimum supported server</span></span> | <span data-ttu-id="94419-127">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="94419-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="94419-128">Header</span><span class="sxs-lookup"><span data-stu-id="94419-128">Header</span></span> | <span data-ttu-id="94419-129">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="94419-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="94419-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="94419-130">Library</span></span> | <span data-ttu-id="94419-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="94419-131">Kernel32.lib</span></span> |
| <span data-ttu-id="94419-132">DLL</span><span class="sxs-lookup"><span data-stu-id="94419-132">DLL</span></span> | <span data-ttu-id="94419-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="94419-133">Kernel32.dll</span></span> |
| <span data-ttu-id="94419-134">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="94419-134">Unicode and ANSI names</span></span> | <span data-ttu-id="94419-135">**Getconsolealiasw** (Unicode) und **getconsolealiasa** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="94419-135">**GetConsoleAliasW** (Unicode) and **GetConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="94419-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="94419-136">See also</span></span>

[<span data-ttu-id="94419-137">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="94419-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="94419-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="94419-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="94419-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="94419-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="94419-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="94419-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="94419-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="94419-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
