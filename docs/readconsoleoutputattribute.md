---
title: Leserconsoleoutputattribute-Funktion
description: Kopiert eine angegebene Anzahl von Zeichen Attributen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f64e39b7b68e24e6c2aa7e9704c285bbbbc234f0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039508"
---
# <a name="readconsoleoutputattribute-function"></a><span data-ttu-id="018cb-104">Leserconsoleoutputattribute-Funktion</span><span class="sxs-lookup"><span data-stu-id="018cb-104">ReadConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="018cb-105">Kopiert eine angegebene Anzahl von Zeichen Attributen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="018cb-105">Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="018cb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="018cb-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a><span data-ttu-id="018cb-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="018cb-107">Parameters</span></span>

<span data-ttu-id="018cb-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="018cb-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="018cb-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="018cb-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="018cb-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="018cb-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="018cb-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="018cb-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="018cb-112">*lpattribute* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="018cb-112">*lpAttribute* \[out\]</span></span>  
<span data-ttu-id="018cb-113">Ein Zeiger auf einen Puffer, der die Attribute empfängt, die vom Konsolenbildschirm Puffer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="018cb-113">A pointer to a buffer that receives the attributes being used by the console screen buffer.</span></span>

<span data-ttu-id="018cb-114">Weitere Informationen finden Sie unter [Zeichen Attribute](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="018cb-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="018cb-115">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="018cb-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="018cb-116">Die Anzahl der zu lesenden Zeichen Zellen des Bildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="018cb-116">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="018cb-117">Die Größe des Puffers, auf den der *lpattribute* -Parameter verweist, sollte lauten `nLength * sizeof(WORD)` .</span><span class="sxs-lookup"><span data-stu-id="018cb-117">The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.</span></span>

<span data-ttu-id="018cb-118">*dwumkoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="018cb-118">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="018cb-119">Die Koordinaten der ersten Zelle im Konsolenbildschirm Puffer, von der in Zeichen gelesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="018cb-119">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="018cb-120">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.</span><span class="sxs-lookup"><span data-stu-id="018cb-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="018cb-121">*lpnumofattrsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="018cb-121">*lpNumberOfAttrsRead* \[out\]</span></span>  
<span data-ttu-id="018cb-122">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Attribute empfängt.</span><span class="sxs-lookup"><span data-stu-id="018cb-122">A pointer to a variable that receives the number of attributes actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="018cb-123">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="018cb-123">Return value</span></span>

<span data-ttu-id="018cb-124">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="018cb-124">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="018cb-125">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="018cb-125">If the function fails, the return value is zero.</span></span> <span data-ttu-id="018cb-126">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="018cb-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="018cb-127">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="018cb-127">Remarks</span></span>

<span data-ttu-id="018cb-128">Wenn sich die Anzahl der zu lesenden Attribute über das Ende der angegebenen Bildschirm Puffer Zeile hinaus erstreckt, werden Attribute aus der nächsten Zeile gelesen.</span><span class="sxs-lookup"><span data-stu-id="018cb-128">If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row.</span></span> <span data-ttu-id="018cb-129">Wenn die Anzahl der zu lesenden Attribute über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Attribute bis zum Ende des Konsolenbildschirm Puffers gelesen.</span><span class="sxs-lookup"><span data-stu-id="018cb-129">If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="018cb-130">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="018cb-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="018cb-131">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="018cb-131">Minimum supported client</span></span> | <span data-ttu-id="018cb-132">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="018cb-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="018cb-133">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="018cb-133">Minimum supported server</span></span> | <span data-ttu-id="018cb-134">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="018cb-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="018cb-135">Header</span><span class="sxs-lookup"><span data-stu-id="018cb-135">Header</span></span> | <span data-ttu-id="018cb-136">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="018cb-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="018cb-137">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="018cb-137">Library</span></span> | <span data-ttu-id="018cb-138">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="018cb-138">Kernel32.lib</span></span> |
| <span data-ttu-id="018cb-139">DLL</span><span class="sxs-lookup"><span data-stu-id="018cb-139">DLL</span></span> | <span data-ttu-id="018cb-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="018cb-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="018cb-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="018cb-141">See also</span></span>

[<span data-ttu-id="018cb-142">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="018cb-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="018cb-143">**Koord**</span><span class="sxs-lookup"><span data-stu-id="018cb-143">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="018cb-144">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="018cb-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="018cb-145">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="018cb-145">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="018cb-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="018cb-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="018cb-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="018cb-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="018cb-148">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="018cb-148">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="018cb-149">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="018cb-149">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
