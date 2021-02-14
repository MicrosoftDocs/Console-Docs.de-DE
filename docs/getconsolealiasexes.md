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
ms.openlocfilehash: 1a97df0c22f084389e9bd6df1c4a2e8863090b45
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357493"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="82140-104">Getconsolealiasexes-Funktion</span><span class="sxs-lookup"><span data-stu-id="82140-104">GetConsoleAliasExes function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="82140-105">Ruft die Namen aller ausführbaren Dateien mit definierten Konsolen Aliasen ab.</span><span class="sxs-lookup"><span data-stu-id="82140-105">Retrieves the names of all executable files with console aliases defined.</span></span>

## <a name="syntax"></a><span data-ttu-id="82140-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="82140-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a><span data-ttu-id="82140-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="82140-107">Parameters</span></span>

<span data-ttu-id="82140-108">*lpexenamebuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="82140-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="82140-109">Ein Zeiger auf einen Puffer, der die Namen der ausführbaren Dateien empfängt.</span><span class="sxs-lookup"><span data-stu-id="82140-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="82140-110">*Exenamebufferlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="82140-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="82140-111">Die Größe des Puffers, auf den *lpexenamebuffer* zeigt (in Bytes).</span><span class="sxs-lookup"><span data-stu-id="82140-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

## <a name="return-value"></a><span data-ttu-id="82140-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="82140-112">Return value</span></span>

<span data-ttu-id="82140-113">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="82140-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="82140-114">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="82140-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="82140-115">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="82140-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="82140-116">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="82140-116">Remarks</span></span>

<span data-ttu-id="82140-117">Verwenden Sie die [**getconsolealiasexeslength**](getconsolealiasexeslength.md) -Funktion, um die erforderliche Größe für den *lpexenamebuffer* -Puffer zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="82140-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="82140-118">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher.</span><span class="sxs-lookup"><span data-stu-id="82140-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="82140-119">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="82140-119">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="82140-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="82140-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="82140-121">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="82140-121">Minimum supported client</span></span> | <span data-ttu-id="82140-122">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="82140-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="82140-123">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="82140-123">Minimum supported server</span></span> | <span data-ttu-id="82140-124">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="82140-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="82140-125">Header</span><span class="sxs-lookup"><span data-stu-id="82140-125">Header</span></span> | <span data-ttu-id="82140-126">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="82140-126">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="82140-127">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="82140-127">Library</span></span> | <span data-ttu-id="82140-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="82140-128">Kernel32.lib</span></span> |
| <span data-ttu-id="82140-129">DLL</span><span class="sxs-lookup"><span data-stu-id="82140-129">DLL</span></span> | <span data-ttu-id="82140-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="82140-130">Kernel32.dll</span></span> |
| <span data-ttu-id="82140-131">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="82140-131">Unicode and ANSI names</span></span> | <span data-ttu-id="82140-132">**Getconsolealiasexesw** (Unicode) und **getconsolealiasexesa** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="82140-132">**GetConsoleAliasExesW** (Unicode) and **GetConsoleAliasExesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="82140-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="82140-133">See also</span></span>

[<span data-ttu-id="82140-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="82140-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="82140-135">Konsolenaliase</span><span class="sxs-lookup"><span data-stu-id="82140-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="82140-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="82140-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="82140-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="82140-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="82140-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="82140-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="82140-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="82140-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)