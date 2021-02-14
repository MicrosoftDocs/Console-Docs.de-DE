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
ms.openlocfilehash: b08f4b0b628f4d20029b81873b4fc25077a11029
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358560"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="0c976-104">SetConsoleTextAttribute-Funktion</span><span class="sxs-lookup"><span data-stu-id="0c976-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0c976-105">Legt die Attribute der Zeichen fest, die von der Funktion " [**Write File**](/windows/win32/api/fileapi/nf-fileapi-writefile) " oder der Funktion " [**Write-Console**](writeconsole.md) " auf den Konsolenbildschirm Puffer geschrieben wurden, oder von der Funktion "read [**File**](/windows/win32/api/fileapi/nf-fileapi-readfile) " oder "read [**Console**](readconsole.md) "</span><span class="sxs-lookup"><span data-stu-id="0c976-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="0c976-106">Diese Funktion wirkt sich auf Text aus, der nach dem Funktions aufzurufen</span><span class="sxs-lookup"><span data-stu-id="0c976-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c976-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c976-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="0c976-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="0c976-108">Parameters</span></span>

<span data-ttu-id="0c976-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0c976-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0c976-110">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="0c976-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="0c976-111">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="0c976-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="0c976-112">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="0c976-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0c976-113">*wattributes* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="0c976-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="0c976-114">Die [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="0c976-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="0c976-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0c976-115">Return value</span></span>

<span data-ttu-id="0c976-116">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="0c976-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0c976-117">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="0c976-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0c976-118">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="0c976-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0c976-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="0c976-119">Remarks</span></span>

<span data-ttu-id="0c976-120">Um die aktuellen Farb Attribute eines Bildschirm Puffers zu bestimmen, müssen Sie die [**getconsoleskreenbufferinfo**](getconsolescreenbufferinfo.md) -Funktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="0c976-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="0c976-121">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den **[Text Formatierungs](console-virtual-terminal-sequences.md#text-formatting)** Sequenzen.</span><span class="sxs-lookup"><span data-stu-id="0c976-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="0c976-122">_Virtuelle Terminal Sequenzen_ werden für alle neuen und laufenden Entwicklungen empfohlen.</span><span class="sxs-lookup"><span data-stu-id="0c976-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="0c976-123">Beispiele</span><span class="sxs-lookup"><span data-stu-id="0c976-123">Examples</span></span>

<span data-ttu-id="0c976-124">Ein Beispiel finden Sie unter [Verwenden der High-Level Eingabe-und Ausgabefunktionen](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0c976-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0c976-125">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0c976-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0c976-126">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0c976-126">Minimum supported client</span></span> | <span data-ttu-id="0c976-127">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0c976-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0c976-128">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0c976-128">Minimum supported server</span></span> | <span data-ttu-id="0c976-129">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0c976-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0c976-130">Header</span><span class="sxs-lookup"><span data-stu-id="0c976-130">Header</span></span> | <span data-ttu-id="0c976-131">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0c976-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0c976-132">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="0c976-132">Library</span></span> | <span data-ttu-id="0c976-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0c976-133">Kernel32.lib</span></span> |
| <span data-ttu-id="0c976-134">DLL</span><span class="sxs-lookup"><span data-stu-id="0c976-134">DLL</span></span> | <span data-ttu-id="0c976-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0c976-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0c976-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0c976-136">See also</span></span>

[<span data-ttu-id="0c976-137">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="0c976-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0c976-138">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="0c976-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="0c976-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="0c976-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="0c976-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="0c976-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="0c976-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="0c976-141">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="0c976-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="0c976-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="0c976-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="0c976-143">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)