---
title: "\"Read consoleoutputcharacter\"-Funktion"
description: Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: fa70841d5dccf3289807d29c67fab86e3b445279
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037722"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="ea729-104">"Read consoleoutputcharacter"-Funktion</span><span class="sxs-lookup"><span data-stu-id="ea729-104">ReadConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ea729-105">Kopiert eine Anzahl von Zeichen aus aufeinander folgenden Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="ea729-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea729-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea729-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

## <a name="parameters"></a><span data-ttu-id="ea729-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="ea729-107">Parameters</span></span>

<span data-ttu-id="ea729-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ea729-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ea729-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="ea729-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ea729-110">Das Handle muss über das **allgemeine \_ Lese** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="ea729-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ea729-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ea729-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ea729-112">*lpcharacter* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="ea729-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="ea729-113">Ein Zeiger auf einen Puffer, der die aus dem Konsolenbildschirm Puffer gelesenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="ea729-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="ea729-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ea729-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="ea729-115">Die Anzahl der zu lesenden Zeichen Zellen des Bildschirm Puffers.</span><span class="sxs-lookup"><span data-stu-id="ea729-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="ea729-116">Die Größe des Puffers, auf den der *lpcharacter* -Parameter verweist, sollte lauten `nLength * sizeof(TCHAR)` .</span><span class="sxs-lookup"><span data-stu-id="ea729-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="ea729-117">*dwumkoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="ea729-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="ea729-118">Die Koordinaten der ersten Zelle im Konsolenbildschirm Puffer, von der in Zeichen gelesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ea729-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="ea729-119">Der **X** -Member der [**coord**](coord-str.md) -Struktur ist die-Spalte, und der **Y** -Member ist die Zeile.</span><span class="sxs-lookup"><span data-stu-id="ea729-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="ea729-120">*lpnumofcharsread* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="ea729-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="ea729-121">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich gelesenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="ea729-121">A pointer to a variable that receives the number of characters actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="ea729-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ea729-122">Return value</span></span>

<span data-ttu-id="ea729-123">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="ea729-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ea729-124">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="ea729-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ea729-125">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="ea729-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="ea729-126">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ea729-126">Remarks</span></span>

<span data-ttu-id="ea729-127">Wenn sich die Anzahl der zu lesenden Zeichen über das Ende der angegebenen Bildschirm Puffer Zeile hinaus erstreckt, werden Zeichen aus der nächsten Zeile gelesen.</span><span class="sxs-lookup"><span data-stu-id="ea729-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="ea729-128">Wenn die Anzahl der zu lesenden Zeichen über das Ende des Konsolenbildschirm Puffers hinausgeht, werden Zeichen bis zum Ende des Konsolenbildschirm Puffers gelesen.</span><span class="sxs-lookup"><span data-stu-id="ea729-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="ea729-129">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="ea729-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ea729-130">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="ea729-130">Minimum supported client</span></span> | <span data-ttu-id="ea729-131">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ea729-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ea729-132">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="ea729-132">Minimum supported server</span></span> | <span data-ttu-id="ea729-133">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="ea729-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ea729-134">Header</span><span class="sxs-lookup"><span data-stu-id="ea729-134">Header</span></span> | <span data-ttu-id="ea729-135">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ea729-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ea729-136">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ea729-136">Library</span></span> | <span data-ttu-id="ea729-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ea729-137">Kernel32.lib</span></span> |
| <span data-ttu-id="ea729-138">DLL</span><span class="sxs-lookup"><span data-stu-id="ea729-138">DLL</span></span> | <span data-ttu-id="ea729-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ea729-139">Kernel32.dll</span></span> |
| <span data-ttu-id="ea729-140">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="ea729-140">Unicode and ANSI names</span></span> | <span data-ttu-id="ea729-141">"Read **consoleoutputcharakteriw** (Unicode)" und "read **consoleoutputcharaka** (ANSI)"</span><span class="sxs-lookup"><span data-stu-id="ea729-141">**ReadConsoleOutputCharacterW** (Unicode) and **ReadConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="ea729-142">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ea729-142">See also</span></span>

[<span data-ttu-id="ea729-143">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="ea729-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ea729-144">**Koord**</span><span class="sxs-lookup"><span data-stu-id="ea729-144">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="ea729-145">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="ea729-145">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="ea729-146">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ea729-146">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="ea729-147">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ea729-147">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="ea729-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ea729-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ea729-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ea729-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="ea729-150">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ea729-150">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="ea729-151">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ea729-151">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="ea729-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ea729-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
