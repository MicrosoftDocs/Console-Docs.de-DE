---
title: Getconsoledisplaymode-Funktion
description: Siehe Referenzinformationen zur getconsoledisplaymode-Funktion, die den Anzeigemodus der aktuellen Konsole abruft.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b9ec78dc6fe5d7baa1a9af64010fd577f101c47
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358350"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="58b70-104">Getconsoledisplaymode-Funktion</span><span class="sxs-lookup"><span data-stu-id="58b70-104">GetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="58b70-105">Ruft den Anzeigemodus der aktuellen Konsole ab.</span><span class="sxs-lookup"><span data-stu-id="58b70-105">Retrieves the display mode of the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="58b70-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="58b70-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a><span data-ttu-id="58b70-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="58b70-107">Parameters</span></span>

<span data-ttu-id="58b70-108">*lpmodeflags* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="58b70-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="58b70-109">Der Anzeigemodus der Konsole.</span><span class="sxs-lookup"><span data-stu-id="58b70-109">The display mode of the console.</span></span> <span data-ttu-id="58b70-110">Dieser Parameter kann einen oder mehrere der folgenden Werte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="58b70-110">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="58b70-111">Wert</span><span class="sxs-lookup"><span data-stu-id="58b70-111">Value</span></span> | <span data-ttu-id="58b70-112">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="58b70-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="58b70-113">**CONSOLE_FULLSCREEN** 1</span><span class="sxs-lookup"><span data-stu-id="58b70-113">**CONSOLE_FULLSCREEN** 1</span></span> | <span data-ttu-id="58b70-114">Voll Bild Konsole.</span><span class="sxs-lookup"><span data-stu-id="58b70-114">Full-screen console.</span></span> <span data-ttu-id="58b70-115">Die Konsole befindet sich in diesem Modus, sobald das Fenster maximiert ist.</span><span class="sxs-lookup"><span data-stu-id="58b70-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="58b70-116">An diesem Punkt kann der Übergang zum Vollbildmodus weiterhin fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="58b70-116">At this point, the transition to full-screen mode can still fail.</span></span> |
| <span data-ttu-id="58b70-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span><span class="sxs-lookup"><span data-stu-id="58b70-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span></span> | <span data-ttu-id="58b70-118">Voll Bild Konsole, die direkt mit der Video Hardware kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="58b70-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="58b70-119">Dieser Modus wird festgelegt, nachdem sich die Konsole im **CONSOLE_FULLSCREEN** Modus befindet, um anzugeben, dass der Übergang zum Vollbildmodus abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="58b70-119">This mode is set after the console is in **CONSOLE_FULLSCREEN** mode to indicate that the transition to full-screen mode has completed.</span></span> |

> [!NOTE]
> <span data-ttu-id="58b70-120">Der Übergang zu einem 100%-Hardware Modus für den Vollbildmodus wurde in Windows Vista mit der Neuplatzierung des Grafik Stapels zu [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model)entfernt.</span><span class="sxs-lookup"><span data-stu-id="58b70-120">The transition to a 100% full screen video hardware mode was removed in Windows Vista with the replatforming of the graphics stack to [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span></span> <span data-ttu-id="58b70-121">Bei späteren Versionen von Windows ist der Höchstwert, der sich ergibt, **CONSOLE_FULLSCREEN** ein fragebess Fenster, das den Vollbildmodus darstellt, aber nicht die exklusive Kontrolle über die Hardware darstellt.</span><span class="sxs-lookup"><span data-stu-id="58b70-121">On later versions of Windows, the maximum resulting state is **CONSOLE_FULLSCREEN** representing a frameless window that appears full screen but isn't in exclusive control of the hardware.</span></span>

## <a name="return-value"></a><span data-ttu-id="58b70-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="58b70-122">Return value</span></span>

<span data-ttu-id="58b70-123">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="58b70-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="58b70-124">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="58b70-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="58b70-125">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="58b70-125">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="58b70-126">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="58b70-126">Remarks</span></span>

<span data-ttu-id="58b70-127">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="58b70-127">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="58b70-128">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="58b70-128">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="58b70-129">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="58b70-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="58b70-130">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="58b70-130">Minimum supported client</span></span> | <span data-ttu-id="58b70-131">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="58b70-131">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="58b70-132">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="58b70-132">Minimum supported server</span></span> | <span data-ttu-id="58b70-133">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="58b70-133">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="58b70-134">Header</span><span class="sxs-lookup"><span data-stu-id="58b70-134">Header</span></span> | <span data-ttu-id="58b70-135">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="58b70-135">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="58b70-136">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="58b70-136">Library</span></span> | <span data-ttu-id="58b70-137">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="58b70-137">Kernel32.lib</span></span> |
| <span data-ttu-id="58b70-138">DLL</span><span class="sxs-lookup"><span data-stu-id="58b70-138">DLL</span></span> | <span data-ttu-id="58b70-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="58b70-139">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="58b70-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="58b70-140">See also</span></span>

[<span data-ttu-id="58b70-141">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="58b70-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="58b70-142">Konsolenmodi</span><span class="sxs-lookup"><span data-stu-id="58b70-142">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="58b70-143">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="58b70-143">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)