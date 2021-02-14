---
title: Funktion "Peer-ConsoleInput"
description: Liest Daten aus dem angegebenen Konsolen Eingabepuffer, ohne Sie aus dem Puffer zu entfernen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 8ae6bb36007ede4015c91dfd4fe2a8ba8c898465
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358310"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="6bf3f-104">Funktion "Peer-ConsoleInput"</span><span class="sxs-lookup"><span data-stu-id="6bf3f-104">PeekConsoleInput function</span></span>

<span data-ttu-id="6bf3f-105">Liest Daten aus dem angegebenen Konsolen Eingabepuffer, ohne Sie aus dem Puffer zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="6bf3f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6bf3f-106">Syntax</span></span>

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="6bf3f-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="6bf3f-107">Parameters</span></span>

<span data-ttu-id="6bf3f-108">*hconsoleinput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6bf3f-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="6bf3f-109">Ein Handle für den Konsolen Eingabepuffer.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-109">A handle to the console input buffer.</span></span> <span data-ttu-id="6bf3f-110">Das Handle muss über das Zugriffsrecht **GENERIC\_READ** verfügen.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6bf3f-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für Konsolenpuffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="6bf3f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6bf3f-112">*lpBuffer* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="6bf3f-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="6bf3f-113">Ein Zeiger auf ein Array von [**Eingabedaten \_ Satz**](input-record-str.md) Strukturen, die die Eingabepuffer Daten empfangen.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="6bf3f-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="6bf3f-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="6bf3f-115">Die Größe des Arrays, auf das durch den *lpBuffer* -Parameter in Array Elementen verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="6bf3f-116">*lpnumofeventsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="6bf3f-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="6bf3f-117">Ein Zeiger auf eine Variable, die die Anzahl der gelesenen Eingabedaten Sätze empfängt.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="6bf3f-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="6bf3f-118">Return value</span></span>

<span data-ttu-id="6bf3f-119">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6bf3f-120">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6bf3f-121">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="6bf3f-122">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="6bf3f-122">Remarks</span></span>

<span data-ttu-id="6bf3f-123">Wenn die Anzahl der angeforderten Datensätze die Anzahl der Datensätze überschreitet, die im Puffer verfügbar sind, wird die verfügbare Zahl gelesen.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="6bf3f-124">Wenn keine Daten verfügbar sind, gibt die Funktion sofort zurück.</span><span class="sxs-lookup"><span data-stu-id="6bf3f-124">If no data is available, the function returns immediately.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="requirements"></a><span data-ttu-id="6bf3f-125">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="6bf3f-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6bf3f-126">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="6bf3f-126">Minimum supported client</span></span> | <span data-ttu-id="6bf3f-127">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6bf3f-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6bf3f-128">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="6bf3f-128">Minimum supported server</span></span> | <span data-ttu-id="6bf3f-129">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6bf3f-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6bf3f-130">Header</span><span class="sxs-lookup"><span data-stu-id="6bf3f-130">Header</span></span> | <span data-ttu-id="6bf3f-131">ConsoleApi.h (über WinCon.h, Windows.h einschließen)</span><span class="sxs-lookup"><span data-stu-id="6bf3f-131">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="6bf3f-132">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="6bf3f-132">Library</span></span> | <span data-ttu-id="6bf3f-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="6bf3f-133">Kernel32.lib</span></span> |
| <span data-ttu-id="6bf3f-134">DLL</span><span class="sxs-lookup"><span data-stu-id="6bf3f-134">DLL</span></span> | <span data-ttu-id="6bf3f-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6bf3f-135">Kernel32.dll</span></span> |
| <span data-ttu-id="6bf3f-136">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="6bf3f-136">Unicode and ANSI names</span></span> | <span data-ttu-id="6bf3f-137">" **Peer** " (Unicode) und " **ppconsoleinputa** " (ANSI)</span><span class="sxs-lookup"><span data-stu-id="6bf3f-137">**PeekConsoleInputW** (Unicode) and **PeekConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="6bf3f-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6bf3f-138">See also</span></span>

[<span data-ttu-id="6bf3f-139">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="6bf3f-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6bf3f-140">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="6bf3f-140">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="6bf3f-141">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="6bf3f-141">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="6bf3f-142">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="6bf3f-142">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="6bf3f-143">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="6bf3f-143">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="6bf3f-144">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="6bf3f-144">**INPUT\_RECORD**</span></span>](input-record-str.md)