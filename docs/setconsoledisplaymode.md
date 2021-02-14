---
title: Setconsoledisplaymode-Funktion
description: Weitere Informationen finden Sie in den Referenzinformationen zur setconsoledisplaymode-Funktion, mit der der Anzeigemodus des angegebenen Konsolenbildschirm Puffers festgelegt wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: af61d897269311ccfa9db336083e898f6d75da80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357700"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="f1818-104">Setconsoledisplaymode-Funktion</span><span class="sxs-lookup"><span data-stu-id="f1818-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f1818-105">Legt den Anzeigemodus des angegebenen Konsolenbildschirm Puffers fest.</span><span class="sxs-lookup"><span data-stu-id="f1818-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1818-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1818-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="f1818-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="f1818-107">Parameters</span></span>

<span data-ttu-id="f1818-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f1818-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f1818-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="f1818-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="f1818-110">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="f1818-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="f1818-111">Der Anzeigemodus der Konsole.</span><span class="sxs-lookup"><span data-stu-id="f1818-111">The display mode of the console.</span></span> <span data-ttu-id="f1818-112">Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f1818-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="f1818-113">Wert</span><span class="sxs-lookup"><span data-stu-id="f1818-113">Value</span></span> | <span data-ttu-id="f1818-114">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="f1818-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="f1818-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="f1818-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="f1818-116">Der Text wird im Vollbildmodus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f1818-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="f1818-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="f1818-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="f1818-118">Der Text wird in einem Konsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f1818-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="f1818-119">*lpnewscreenbufferdimensions* \[ Out, optional\]</span><span class="sxs-lookup"><span data-stu-id="f1818-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="f1818-120">Ein Zeiger auf eine [**Koord**](coord-str.md) -Struktur, die die neuen Abmessungen des Bildschirm Puffers empfängt, in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="f1818-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="f1818-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f1818-121">Return value</span></span>

<span data-ttu-id="f1818-122">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="f1818-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f1818-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="f1818-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f1818-124">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="f1818-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f1818-125">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="f1818-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="f1818-126">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f1818-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f1818-127">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="f1818-127">Minimum supported client</span></span> | <span data-ttu-id="f1818-128">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="f1818-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="f1818-129">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="f1818-129">Minimum supported server</span></span> | <span data-ttu-id="f1818-130">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="f1818-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="f1818-131">Header</span><span class="sxs-lookup"><span data-stu-id="f1818-131">Header</span></span> | <span data-ttu-id="f1818-132">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f1818-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f1818-133">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="f1818-133">Library</span></span> | <span data-ttu-id="f1818-134">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f1818-134">Kernel32.lib</span></span> |
| <span data-ttu-id="f1818-135">DLL</span><span class="sxs-lookup"><span data-stu-id="f1818-135">DLL</span></span> | <span data-ttu-id="f1818-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f1818-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="f1818-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f1818-137">See also</span></span>

[<span data-ttu-id="f1818-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="f1818-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f1818-139">Konsolenmodi</span><span class="sxs-lookup"><span data-stu-id="f1818-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="f1818-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="f1818-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)