---
title: Getconsolealiasexes-Funktion
description: Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0e818c8ecee8ac777f7cc3cf2394d8846bebd034
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038078"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="19cf2-104">Getconsolealiasexes-Funktion</span><span class="sxs-lookup"><span data-stu-id="19cf2-104">GetConsoleAliasExes function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="19cf2-105">Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.</span><span class="sxs-lookup"><span data-stu-id="19cf2-105">Retrieves the names of all executable files with console aliases defined.</span></span>

## <a name="syntax"></a><span data-ttu-id="19cf2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="19cf2-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a><span data-ttu-id="19cf2-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="19cf2-107">Parameters</span></span>

<span data-ttu-id="19cf2-108">*lpexenamebuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="19cf2-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="19cf2-109">Ein Zeiger auf einen Puffer, der die Namen der ausführbaren Dateien empfängt.</span><span class="sxs-lookup"><span data-stu-id="19cf2-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="19cf2-110">*Exenamebufferlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="19cf2-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="19cf2-111">Die Größe des Puffers, auf den *lpexenamebuffer* zeigt (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="19cf2-111">The size of the buffer pointed to by *lpExeNameBuffer* , in bytes.</span></span>

## <a name="return-value"></a><span data-ttu-id="19cf2-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="19cf2-112">Return value</span></span>

<span data-ttu-id="19cf2-113">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="19cf2-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="19cf2-114">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="19cf2-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="19cf2-115">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="19cf2-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="19cf2-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="19cf2-116">Remarks</span></span>

<span data-ttu-id="19cf2-117">Verwenden Sie die [**getconsolealiasexeslength**](getconsolealiasexeslength.md) -Funktion, um die erforderliche Größe für den *lpexenamebuffer* -Puffer zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="19cf2-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="19cf2-118">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="19cf2-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="19cf2-119">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="19cf2-119">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="19cf2-120">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="19cf2-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="19cf2-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="19cf2-121">Minimum supported client</span></span> | <span data-ttu-id="19cf2-122">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="19cf2-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="19cf2-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="19cf2-123">Minimum supported server</span></span> | <span data-ttu-id="19cf2-124">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="19cf2-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="19cf2-125">Header</span><span class="sxs-lookup"><span data-stu-id="19cf2-125">Header</span></span> | <span data-ttu-id="19cf2-126">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="19cf2-126">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="19cf2-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="19cf2-127">Library</span></span> | <span data-ttu-id="19cf2-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="19cf2-128">Kernel32.lib</span></span> |
| <span data-ttu-id="19cf2-129">DLL</span><span class="sxs-lookup"><span data-stu-id="19cf2-129">DLL</span></span> | <span data-ttu-id="19cf2-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="19cf2-130">Kernel32.dll</span></span> |
| <span data-ttu-id="19cf2-131">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="19cf2-131">Unicode and ANSI names</span></span> | <span data-ttu-id="19cf2-132">**Getconsolealiasexesw** (Unicode) und **getconsolealiasexesa** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="19cf2-132">**GetConsoleAliasExesW** (Unicode) and **GetConsoleAliasExesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="19cf2-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="19cf2-133">See also</span></span>

[<span data-ttu-id="19cf2-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="19cf2-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="19cf2-135">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="19cf2-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="19cf2-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="19cf2-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="19cf2-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="19cf2-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="19cf2-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="19cf2-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="19cf2-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="19cf2-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)
