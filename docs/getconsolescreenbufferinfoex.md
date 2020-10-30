---
title: Getconsoleskreenbufferinfoex-Funktion
description: Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 5f4b0f11821b7d5b61c61d4ab8f9774c4a69eec0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037938"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="17753-104">Getconsoleskreenbufferinfoex-Funktion</span><span class="sxs-lookup"><span data-stu-id="17753-104">GetConsoleScreenBufferInfoEx function</span></span>

<span data-ttu-id="17753-105">Ruft erweiterte Informationen zum angegebenen Bildschirm Puffer der Konsole ab.</span><span class="sxs-lookup"><span data-stu-id="17753-105">Retrieves extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="17753-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="17753-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="17753-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="17753-107">Parameters</span></span>

<span data-ttu-id="17753-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="17753-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="17753-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="17753-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="17753-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="17753-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="17753-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="17753-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="17753-112">*lpconsoleskreenbufferinfoex* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="17753-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="17753-113">Eine [**\_ \_ \_ INFOEX-Struktur des Konsolenbildschirm Puffers**](console-screen-buffer-infoex.md) , die die angeforderten Konsolenbildschirm Puffer Informationen empfängt.</span><span class="sxs-lookup"><span data-stu-id="17753-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="17753-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="17753-114">Return value</span></span>

<span data-ttu-id="17753-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="17753-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="17753-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="17753-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="17753-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="17753-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="17753-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="17753-118">Remarks</span></span>

<span data-ttu-id="17753-119">Das Rechteck, das im **srwindow** -Member der [**\_ \_ \_ INFOEX-Struktur der Konsolenbildschirm Puffer**](console-screen-buffer-infoex.md) zurückgegeben wurde, kann geändert und dann an die [**setconsolewindowinfo**](setconsolewindowinfo.md) -Funktion weitergegeben werden, um einen Bildlauf im Fenster des Konsolenbildschirm Puffers durchführen, um die Größe des Fensters oder beides zu ändern.</span><span class="sxs-lookup"><span data-stu-id="17753-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="17753-120">Alle in der INFOEX-Struktur des [**Konsolen \_ Bildschirm \_ Puffers \_**](console-screen-buffer-infoex.md) zurückgegebenen Koordinaten befinden sich in Zeichen Zellen Koordinaten, wobei sich der Ursprung (0, 0) in der oberen linken Ecke des Konsolenbildschirm Puffers befindet.</span><span class="sxs-lookup"><span data-stu-id="17753-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="17753-121">Diese API weist keine Entsprechung für ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** auf.</span><span class="sxs-lookup"><span data-stu-id="17753-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="17753-122">Diese Verwendung ist möglicherweise trotzdem für Anwendungen erforderlich, die versuchen, Spalten, Raster oder die Anzeige zu zeichnen, um die Fenstergröße abzurufen.</span><span class="sxs-lookup"><span data-stu-id="17753-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="17753-123">Dieser Fenster Zustand wird von der TTY/Pty/pseudoconsole außerhalb des normalen streamflows verwaltet und in der Regel als Benutzer Berechtigung betrachtet, die von der Client Anwendung nicht angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="17753-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="17753-124">Updates können für "read [**ConsoleInput**](readconsoleinput.md)" empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="17753-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="17753-125">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="17753-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="17753-126">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="17753-126">Minimum supported client</span></span> | <span data-ttu-id="17753-127">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="17753-127">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="17753-128">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="17753-128">Minimum supported server</span></span> | <span data-ttu-id="17753-129">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="17753-129">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="17753-130">Header</span><span class="sxs-lookup"><span data-stu-id="17753-130">Header</span></span> | <span data-ttu-id="17753-131">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="17753-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="17753-132">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="17753-132">Library</span></span> | <span data-ttu-id="17753-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="17753-133">Kernel32.lib</span></span> |
| <span data-ttu-id="17753-134">DLL</span><span class="sxs-lookup"><span data-stu-id="17753-134">DLL</span></span> | <span data-ttu-id="17753-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="17753-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="17753-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="17753-136">See also</span></span>

[<span data-ttu-id="17753-137">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="17753-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="17753-138">**Konsolen \_ Bildschirm- \_ Puffer \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="17753-138">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="17753-139">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="17753-139">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)
