---
title: Setconsoleskreenbufferinfoex-Funktion
description: Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer auf den angegebenen Puffer fest.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4a83c91a60a26d8e962efdf10b127e97beb70a7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039348"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="e37cf-104">Setconsoleskreenbufferinfoex-Funktion</span><span class="sxs-lookup"><span data-stu-id="e37cf-104">SetConsoleScreenBufferInfoEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e37cf-105">Legt erweiterte Informationen zum angegebenen Konsolenbildschirm Puffer fest.</span><span class="sxs-lookup"><span data-stu-id="e37cf-105">Sets extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="e37cf-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e37cf-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="e37cf-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="e37cf-107">Parameters</span></span>

<span data-ttu-id="e37cf-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e37cf-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e37cf-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="e37cf-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="e37cf-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="e37cf-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="e37cf-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="e37cf-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e37cf-112">*lpconsoleskreenbufferinfoex* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="e37cf-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="e37cf-113">Eine [**\_ \_ \_ INFOEX-Struktur des Konsolenbildschirm Puffers**](console-screen-buffer-infoex.md) , die die Bildschirm Puffer Informationen der Konsole enthält.</span><span class="sxs-lookup"><span data-stu-id="e37cf-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="e37cf-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e37cf-114">Return value</span></span>

<span data-ttu-id="e37cf-115">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="e37cf-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e37cf-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="e37cf-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e37cf-117">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e37cf-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="e37cf-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="e37cf-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="e37cf-119">Diese API verfügt über ein teilweises **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="e37cf-119">This API has a partial **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="e37cf-120">**[Cursor Positions Puffer](console-virtual-terminal-sequences.md#cursor-positioning)** -und **[Text Attribute](console-virtual-terminal-sequences.md#text-formatting)** weisen bestimmte Sequenz Entsprechungen auf.</span><span class="sxs-lookup"><span data-stu-id="e37cf-120">**[Cursor positioning buffer](console-virtual-terminal-sequences.md#cursor-positioning)** and **[text attributes](console-virtual-terminal-sequences.md#text-formatting)** have specific sequence equivalents.</span></span> <span data-ttu-id="e37cf-121">Die Farbtabelle ist nicht konfigurierbar, aber **[Erweiterte Farben](console-virtual-terminal-sequences.md#extended-colors)** sind über die normal verfügbaren **[Funktionen über Konsolenfunktionen](console-functions.md)** hinaus verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e37cf-121">The color table is not configurable, but **[extended colors](console-virtual-terminal-sequences.md#extended-colors)** are available beyond what is normally available through **[console functions](console-functions.md)** .</span></span> <span data-ttu-id="e37cf-122">Popup Attribute haben keine Entsprechung, da Popup Menüs für die Befehlszeilen-Client Anwendung in der **virtuellen Terminal** Welt zuständig sind.</span><span class="sxs-lookup"><span data-stu-id="e37cf-122">Popup attributes have no equivalent as popup menus are the responsibility of the command-line client application in the **virtual terminal** world.</span></span> <span data-ttu-id="e37cf-123">Zum Schluss werden die Größe des Fensters und der voll Bild Status als Berechtigungen betrachtet, die sich im Besitz des Benutzers in der **virtuellen Terminal** Welt befinden und keine äquivalente Reihenfolge aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e37cf-123">Finally, the size of the window and the full screen status are considered privileges owned by the user in the **virtual terminal** world and have no equivalent sequence.</span></span>

## <a name="requirements"></a><span data-ttu-id="e37cf-124">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="e37cf-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e37cf-125">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="e37cf-125">Minimum supported client</span></span> | <span data-ttu-id="e37cf-126">Nur Windows Vista \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e37cf-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="e37cf-127">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="e37cf-127">Minimum supported server</span></span> | <span data-ttu-id="e37cf-128">Nur Windows Server 2008 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="e37cf-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e37cf-129">Header</span><span class="sxs-lookup"><span data-stu-id="e37cf-129">Header</span></span> | <span data-ttu-id="e37cf-130">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e37cf-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e37cf-131">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="e37cf-131">Library</span></span> | <span data-ttu-id="e37cf-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e37cf-132">Kernel32.lib</span></span> |
| <span data-ttu-id="e37cf-133">DLL</span><span class="sxs-lookup"><span data-stu-id="e37cf-133">DLL</span></span> | <span data-ttu-id="e37cf-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e37cf-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e37cf-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e37cf-135">See also</span></span>

[<span data-ttu-id="e37cf-136">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="e37cf-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e37cf-137">**Konsolen \_ Bildschirm- \_ Puffer \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="e37cf-137">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="e37cf-138">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="e37cf-138">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)
