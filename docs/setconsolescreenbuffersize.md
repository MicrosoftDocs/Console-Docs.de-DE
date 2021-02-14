---
title: Setconsoleskreenbuffersize-Funktion
description: Weitere Informationen finden Sie unter Referenzinformationen zur Funktion "setconsoleskreenbuffersize", die die Größe des angegebenen Konsolenbildschirm Puffers ändert.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 66c8eee2b3c4cd50e74ac17404dd30c571e47f96
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357580"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="6b222-104">Setconsoleskreenbuffersize-Funktion</span><span class="sxs-lookup"><span data-stu-id="6b222-104">SetConsoleScreenBufferSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="6b222-105">Ändert die Größe des angegebenen Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="6b222-105">Changes the size of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b222-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b222-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a><span data-ttu-id="6b222-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="6b222-107">Parameters</span></span>

<span data-ttu-id="6b222-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6b222-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6b222-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="6b222-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="6b222-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="6b222-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6b222-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="6b222-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6b222-112">*dwSize* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6b222-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="6b222-113">Eine [**Koord**](coord-str.md) -Struktur, die die neue Größe des Konsolenbildschirm Puffers in Zeichen Zeilen und-Spalten angibt.</span><span class="sxs-lookup"><span data-stu-id="6b222-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="6b222-114">Die angegebene Breite und Höhe darf nicht kleiner sein als die Breite und Höhe des Fensters des Konsolenbildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="6b222-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="6b222-115">Die angegebenen Dimensionen dürfen auch nicht kleiner als die vom System zulässige Mindestgröße sein.</span><span class="sxs-lookup"><span data-stu-id="6b222-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="6b222-116">Dieses Minimum hängt von der aktuellen Schriftgröße für die Konsole (vom Benutzer ausgewählt) und den von der [**GetSystemMetrics**](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) -Funktion zurückgegebenen **SM- \_ cxMin** -und **SM- \_ Cymin** -Werten ab.</span><span class="sxs-lookup"><span data-stu-id="6b222-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="6b222-117">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="6b222-117">Return value</span></span>

<span data-ttu-id="6b222-118">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="6b222-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6b222-119">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="6b222-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6b222-120">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="6b222-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="6b222-121">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="6b222-121">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="6b222-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="6b222-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6b222-123">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="6b222-123">Minimum supported client</span></span> | <span data-ttu-id="6b222-124">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6b222-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6b222-125">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="6b222-125">Minimum supported server</span></span> | <span data-ttu-id="6b222-126">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6b222-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6b222-127">Header</span><span class="sxs-lookup"><span data-stu-id="6b222-127">Header</span></span> | <span data-ttu-id="6b222-128">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6b222-128">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6b222-129">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="6b222-129">Library</span></span> | <span data-ttu-id="6b222-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="6b222-130">Kernel32.lib</span></span> |
| <span data-ttu-id="6b222-131">DLL</span><span class="sxs-lookup"><span data-stu-id="6b222-131">DLL</span></span> | <span data-ttu-id="6b222-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6b222-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="6b222-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6b222-133">See also</span></span>

[<span data-ttu-id="6b222-134">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="6b222-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6b222-135">Konsoleneingabepuffer</span><span class="sxs-lookup"><span data-stu-id="6b222-135">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="6b222-136">**Koord**</span><span class="sxs-lookup"><span data-stu-id="6b222-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="6b222-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="6b222-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="6b222-138">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="6b222-138">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)