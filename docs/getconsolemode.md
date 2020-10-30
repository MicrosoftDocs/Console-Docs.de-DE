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
ms.openlocfilehash: 54667d92509687111cb562f517d488c8adbc2181
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038872"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="81426-104">Getconsolemode-Funktion</span><span class="sxs-lookup"><span data-stu-id="81426-104">GetConsoleMode function</span></span>

<span data-ttu-id="81426-105">Ruft den aktuellen Eingabemodus für den Eingabepuffer einer Konsole oder den aktuellen Ausgabemodus eines Konsolenbildschirm Puffers ab.</span><span class="sxs-lookup"><span data-stu-id="81426-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="81426-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="81426-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a><span data-ttu-id="81426-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="81426-107">Parameters</span></span>

<span data-ttu-id="81426-108">*hconsolehandle* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="81426-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="81426-109">Ein Handle des Konsolen Eingabe Puffers oder des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="81426-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="81426-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="81426-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="81426-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="81426-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="81426-112">*lpmode* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="81426-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="81426-113">Ein Zeiger auf eine Variable, die den aktuellen Modus des angegebenen Puffers empfängt.</span><span class="sxs-lookup"><span data-stu-id="81426-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="81426-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="81426-114">Return value</span></span>

<span data-ttu-id="81426-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="81426-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="81426-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="81426-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="81426-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="81426-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="81426-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="81426-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="81426-119">Um die e/a-Modi einer Konsole zu ändern, müssen Sie die Funktion [**setconsolemode**](setconsolemode.md) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="81426-119">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="81426-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="81426-120">Examples</span></span>

<span data-ttu-id="81426-121">Ein Beispiel finden Sie unter [Lesen von Eingabepuffer Ereignissen](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="81426-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="81426-122">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="81426-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="81426-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="81426-123">Minimum supported client</span></span> | <span data-ttu-id="81426-124">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="81426-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="81426-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="81426-125">Minimum supported server</span></span> | <span data-ttu-id="81426-126">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="81426-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="81426-127">Header</span><span class="sxs-lookup"><span data-stu-id="81426-127">Header</span></span> | <span data-ttu-id="81426-128">Consoleapi. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="81426-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="81426-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="81426-129">Library</span></span> | <span data-ttu-id="81426-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="81426-130">Kernel32.lib</span></span> |
| <span data-ttu-id="81426-131">DLL</span><span class="sxs-lookup"><span data-stu-id="81426-131">DLL</span></span> | <span data-ttu-id="81426-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="81426-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="81426-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="81426-133">See also</span></span>

[<span data-ttu-id="81426-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="81426-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="81426-135">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="81426-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="81426-136">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="81426-136">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="81426-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="81426-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="81426-138">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="81426-138">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="81426-139">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="81426-139">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="81426-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="81426-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="81426-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="81426-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
