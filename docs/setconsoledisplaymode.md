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
ms.openlocfilehash: 52d7e50d7ced5615cb296c0590876e4604057e42
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039388"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="26054-104">Setconsoledisplaymode-Funktion</span><span class="sxs-lookup"><span data-stu-id="26054-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="26054-105">Legt den Anzeigemodus des angegebenen Konsolenbildschirm Puffers fest.</span><span class="sxs-lookup"><span data-stu-id="26054-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="26054-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="26054-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="26054-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="26054-107">Parameters</span></span>

<span data-ttu-id="26054-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="26054-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="26054-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="26054-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="26054-110">*dwFlags* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="26054-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="26054-111">Der Anzeigemodus der Konsole.</span><span class="sxs-lookup"><span data-stu-id="26054-111">The display mode of the console.</span></span> <span data-ttu-id="26054-112">Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="26054-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="26054-113">Wert</span><span class="sxs-lookup"><span data-stu-id="26054-113">Value</span></span> | <span data-ttu-id="26054-114">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="26054-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="26054-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="26054-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="26054-116">Der Text wird im Vollbildmodus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="26054-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="26054-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="26054-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="26054-118">Der Text wird in einem Konsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="26054-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="26054-119">*lpnewscreenbufferdimensions* \[ Out, optional\]</span><span class="sxs-lookup"><span data-stu-id="26054-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="26054-120">Ein Zeiger auf eine [**Koord**](coord-str.md) -Struktur, die die neuen Abmessungen des Bildschirm Puffers empfängt, in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="26054-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="26054-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="26054-121">Return value</span></span>

<span data-ttu-id="26054-122">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="26054-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="26054-123">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="26054-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="26054-124">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="26054-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="26054-125">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="26054-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="26054-126">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="26054-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="26054-127">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="26054-127">Minimum supported client</span></span> | <span data-ttu-id="26054-128">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="26054-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="26054-129">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="26054-129">Minimum supported server</span></span> | <span data-ttu-id="26054-130">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="26054-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="26054-131">Header</span><span class="sxs-lookup"><span data-stu-id="26054-131">Header</span></span> | <span data-ttu-id="26054-132">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="26054-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="26054-133">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="26054-133">Library</span></span> | <span data-ttu-id="26054-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="26054-134">Kernel32.lib</span></span> |
| <span data-ttu-id="26054-135">DLL</span><span class="sxs-lookup"><span data-stu-id="26054-135">DLL</span></span> | <span data-ttu-id="26054-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="26054-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="26054-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="26054-137">See also</span></span>

[<span data-ttu-id="26054-138">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="26054-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="26054-139">Konsolen Modi</span><span class="sxs-lookup"><span data-stu-id="26054-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="26054-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="26054-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)
