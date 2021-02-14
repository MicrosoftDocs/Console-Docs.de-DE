---
title: Getconsolemode-Funktion
description: Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 3f98797b0662dadcf696f76ffda5f42e759bf930
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357280"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="7b3c9-104">Getconsolemode-Funktion</span><span class="sxs-lookup"><span data-stu-id="7b3c9-104">GetConsoleMode function</span></span>

<span data-ttu-id="7b3c9-105">Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="7b3c9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7b3c9-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a><span data-ttu-id="7b3c9-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="7b3c9-107">Parameters</span></span>

<span data-ttu-id="7b3c9-108">*hConsoleHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7b3c9-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="7b3c9-109">Ein Handle des Konsolen Eingabe Puffers oder des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="7b3c9-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="7b3c9-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="7b3c9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="7b3c9-112">*lpmode* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="7b3c9-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="7b3c9-113">Ein Zeiger auf eine Variable, die den aktuellen Modus des angegebenen Puffers empfängt.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="7b3c9-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="7b3c9-114">Return value</span></span>

<span data-ttu-id="7b3c9-115">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7b3c9-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7b3c9-117">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="7b3c9-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="7b3c9-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="7b3c9-119">Um die e/a-Modi einer Konsole zu ändern, müssen Sie die Funktion [**setconsolemode**](setconsolemode.md) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7b3c9-119">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="7b3c9-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7b3c9-120">Examples</span></span>

<span data-ttu-id="7b3c9-121">Ein Beispiel finden Sie unter [Lesen von Eingabepufferereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="7b3c9-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="7b3c9-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="7b3c9-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7b3c9-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="7b3c9-123">Minimum supported client</span></span> | <span data-ttu-id="7b3c9-124">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="7b3c9-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7b3c9-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="7b3c9-125">Minimum supported server</span></span> | <span data-ttu-id="7b3c9-126">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="7b3c9-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7b3c9-127">Header</span><span class="sxs-lookup"><span data-stu-id="7b3c9-127">Header</span></span> | <span data-ttu-id="7b3c9-128">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="7b3c9-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7b3c9-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="7b3c9-129">Library</span></span> | <span data-ttu-id="7b3c9-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="7b3c9-130">Kernel32.lib</span></span> |
| <span data-ttu-id="7b3c9-131">DLL</span><span class="sxs-lookup"><span data-stu-id="7b3c9-131">DLL</span></span> | <span data-ttu-id="7b3c9-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7b3c9-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="7b3c9-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7b3c9-133">See also</span></span>

[<span data-ttu-id="7b3c9-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="7b3c9-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7b3c9-135">Konsolenmodi</span><span class="sxs-lookup"><span data-stu-id="7b3c9-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="7b3c9-136">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="7b3c9-136">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="7b3c9-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="7b3c9-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="7b3c9-138">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="7b3c9-138">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="7b3c9-139">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="7b3c9-139">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="7b3c9-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="7b3c9-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="7b3c9-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="7b3c9-141">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)