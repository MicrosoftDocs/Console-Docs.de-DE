---
title: SetConsoleTextAttribute-Funktion
description: Legt die Attribute der Zeichen fest, die von der Funktion "Write file" oder der Funktion "Write-Console" auf den Konsolenbildschirm Puffer geschrieben wurden, oder von der Funktion "Read File" oder "Read Console"
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 03925af2668774a36de33bfe6ea5fcdc1b475d5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039318"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="762e0-104">SetConsoleTextAttribute-Funktion</span><span class="sxs-lookup"><span data-stu-id="762e0-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="762e0-105">Legt die Attribute der Zeichen fest, die von der Funktion " [**Write File**](https://msdn.microsoft.com/library/windows/desktop/aa365747) " oder der Funktion " [**Write-Console**](writeconsole.md) " auf den Konsolenbildschirm Puffer geschrieben wurden, oder von der Funktion "read [**File**](https://msdn.microsoft.com/library/windows/desktop/aa365467) " oder "read [**Console**](readconsole.md) "</span><span class="sxs-lookup"><span data-stu-id="762e0-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="762e0-106">Diese Funktion wirkt sich auf Text aus, der nach dem Funktions aufzurufen</span><span class="sxs-lookup"><span data-stu-id="762e0-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="762e0-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="762e0-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="762e0-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="762e0-108">Parameters</span></span>

<span data-ttu-id="762e0-109">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="762e0-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="762e0-110">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="762e0-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="762e0-111">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="762e0-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="762e0-112">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="762e0-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="762e0-113">*wattributes* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="762e0-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="762e0-114">Die [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="762e0-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="762e0-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="762e0-115">Return value</span></span>

<span data-ttu-id="762e0-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="762e0-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="762e0-117">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="762e0-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="762e0-118">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="762e0-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="762e0-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="762e0-119">Remarks</span></span>

<span data-ttu-id="762e0-120">Um die aktuellen Farb Attribute eines Bildschirm Puffers zu bestimmen, müssen Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="762e0-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="762e0-121">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den **[Text Formatierungs](console-virtual-terminal-sequences.md#text-formatting)** Sequenzen.</span><span class="sxs-lookup"><span data-stu-id="762e0-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="762e0-122">_Virtuelle Terminal Sequenzen_ werden für alle neuen und laufenden Entwicklungen empfohlen.</span><span class="sxs-lookup"><span data-stu-id="762e0-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="762e0-123">Beispiele</span><span class="sxs-lookup"><span data-stu-id="762e0-123">Examples</span></span>

<span data-ttu-id="762e0-124">Ein Beispiel finden Sie unter [Verwenden der High-Level Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="762e0-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="762e0-125">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="762e0-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="762e0-126">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="762e0-126">Minimum supported client</span></span> | <span data-ttu-id="762e0-127">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="762e0-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="762e0-128">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="762e0-128">Minimum supported server</span></span> | <span data-ttu-id="762e0-129">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="762e0-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="762e0-130">Header</span><span class="sxs-lookup"><span data-stu-id="762e0-130">Header</span></span> | <span data-ttu-id="762e0-131">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="762e0-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="762e0-132">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="762e0-132">Library</span></span> | <span data-ttu-id="762e0-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="762e0-133">Kernel32.lib</span></span> |
| <span data-ttu-id="762e0-134">DLL</span><span class="sxs-lookup"><span data-stu-id="762e0-134">DLL</span></span> | <span data-ttu-id="762e0-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="762e0-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="762e0-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="762e0-136">See also</span></span>

[<span data-ttu-id="762e0-137">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="762e0-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="762e0-138">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="762e0-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="762e0-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="762e0-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="762e0-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="762e0-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="762e0-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="762e0-141">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="762e0-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="762e0-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="762e0-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="762e0-143">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
