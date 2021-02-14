---
title: Getconsolefontsize-Funktion
description: Ruft die Größe der Schriftart ab, die vom angegebenen Konsolenbildschirm Puffer verwendet wird.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96086720ee2c4ae787d2b52eee5439d54f081b8e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358340"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="eef48-104">Getconsolefontsize-Funktion</span><span class="sxs-lookup"><span data-stu-id="eef48-104">GetConsoleFontSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="eef48-105">Ruft die Größe der Schriftart ab, die vom angegebenen Konsolenbildschirm Puffer verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="eef48-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="eef48-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="eef48-106">Syntax</span></span>

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## <a name="parameters"></a><span data-ttu-id="eef48-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="eef48-107">Parameters</span></span>

<span data-ttu-id="eef48-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="eef48-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="eef48-109">Ein Handle für den Konsolenbildschirm-Puffer.</span><span class="sxs-lookup"><span data-stu-id="eef48-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="eef48-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="eef48-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="eef48-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="eef48-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="eef48-112">*nschriftart* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="eef48-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="eef48-113">Der Index der Schriftart, deren Größe abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="eef48-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="eef48-114">Dieser Index wird durch Aufrufen der [**getcurrentconsolefont**](getcurrentconsolefont.md) -Funktion abgerufen.</span><span class="sxs-lookup"><span data-stu-id="eef48-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="eef48-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="eef48-115">Return value</span></span>

<span data-ttu-id="eef48-116">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert eine [**coord**](coord-str.md) -Struktur, die die Breite und Höhe jedes Zeichens in der Schriftart in logischen Einheiten enthält.</span><span class="sxs-lookup"><span data-stu-id="eef48-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="eef48-117">Der **X** -Member enthält die Breite, während das **Y** -Element die Höhe enthält.</span><span class="sxs-lookup"><span data-stu-id="eef48-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="eef48-118">Wenn die Funktion fehlschlägt, sind die Breite und die Höhe 0 (null).</span><span class="sxs-lookup"><span data-stu-id="eef48-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="eef48-119">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="eef48-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="eef48-120">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="eef48-120">Remarks</span></span>

<span data-ttu-id="eef48-121">Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0500 sein oder höher.</span><span class="sxs-lookup"><span data-stu-id="eef48-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="eef48-122">Weitere Informationen finden Sie unter [Verwenden der Windows-Header](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="eef48-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="eef48-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="eef48-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="eef48-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="eef48-124">Minimum supported client</span></span> | <span data-ttu-id="eef48-125">Nur Windows XP \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="eef48-125">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="eef48-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="eef48-126">Minimum supported server</span></span> | <span data-ttu-id="eef48-127">Nur Windows Server 2003 \[ -Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="eef48-127">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="eef48-128">Header</span><span class="sxs-lookup"><span data-stu-id="eef48-128">Header</span></span> | <span data-ttu-id="eef48-129">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="eef48-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="eef48-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="eef48-130">Library</span></span> | <span data-ttu-id="eef48-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="eef48-131">Kernel32.lib</span></span> |
| <span data-ttu-id="eef48-132">DLL</span><span class="sxs-lookup"><span data-stu-id="eef48-132">DLL</span></span> | <span data-ttu-id="eef48-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="eef48-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="eef48-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="eef48-134">See also</span></span>

[<span data-ttu-id="eef48-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="eef48-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="eef48-136">Konsolenbildschirmpuffer</span><span class="sxs-lookup"><span data-stu-id="eef48-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="eef48-137">**Koord**</span><span class="sxs-lookup"><span data-stu-id="eef48-137">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="eef48-138">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="eef48-138">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)