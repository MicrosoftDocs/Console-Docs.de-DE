---
title: Getconsolecursorinfo-Funktion
description: Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c920e5dd279a23b07702fa12b80da4245561548f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358450"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="d7bfd-104">Getconsolecursorinfo-Funktion</span><span class="sxs-lookup"><span data-stu-id="d7bfd-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d7bfd-105">Ruft Informationen über die Größe und die Sichtbarkeit des Cursors für den angegebenen Konsolenbildschirm Puffer ab.</span><span class="sxs-lookup"><span data-stu-id="d7bfd-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7bfd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7bfd-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="d7bfd-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="d7bfd-107">Parameters</span></span>

<span data-ttu-id="d7bfd-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d7bfd-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d7bfd-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="d7bfd-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d7bfd-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="d7bfd-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d7bfd-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d7bfd-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d7bfd-112">*lpconsolecursorinfo* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="d7bfd-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="d7bfd-113">Ein Zeiger auf eine [**Konsolen \_ Cursor \_ Info**](console-cursor-info-str.md) -Struktur, die Informationen über den Cursor der Konsole empfängt.</span><span class="sxs-lookup"><span data-stu-id="d7bfd-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="d7bfd-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d7bfd-114">Return value</span></span>

<span data-ttu-id="d7bfd-115">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="d7bfd-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d7bfd-116">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="d7bfd-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d7bfd-117">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="d7bfd-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d7bfd-118">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="d7bfd-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="d7bfd-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d7bfd-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d7bfd-120">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="d7bfd-120">Minimum supported client</span></span> | <span data-ttu-id="d7bfd-121">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="d7bfd-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d7bfd-122">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="d7bfd-122">Minimum supported server</span></span> | <span data-ttu-id="d7bfd-123">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="d7bfd-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d7bfd-124">Header</span><span class="sxs-lookup"><span data-stu-id="d7bfd-124">Header</span></span> | <span data-ttu-id="d7bfd-125">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d7bfd-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d7bfd-126">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d7bfd-126">Library</span></span> | <span data-ttu-id="d7bfd-127">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d7bfd-127">Kernel32.lib</span></span> |
| <span data-ttu-id="d7bfd-128">DLL</span><span class="sxs-lookup"><span data-stu-id="d7bfd-128">DLL</span></span> | <span data-ttu-id="d7bfd-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d7bfd-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d7bfd-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d7bfd-130">See also</span></span>

[<span data-ttu-id="d7bfd-131">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="d7bfd-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d7bfd-132">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="d7bfd-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="d7bfd-133">**Konsolen \_ Cursor \_ Informationen**</span><span class="sxs-lookup"><span data-stu-id="d7bfd-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="d7bfd-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="d7bfd-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)