---
title: Schreibconsoleoutputcharacter-Funktion
description: Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 462ebfaed09a5c18fa9a075227a5568a789685bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037208"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="be874-104">Schreibconsoleoutputcharacter-Funktion</span><span class="sxs-lookup"><span data-stu-id="be874-104">WriteConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="be874-105">Kopiert eine Anzahl von Zeichen in aufeinander folgende Zellen eines Konsolenbildschirm Puffers, beginnend an einem angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="be874-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="be874-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="be874-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="be874-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="be874-107">Parameters</span></span>

<span data-ttu-id="be874-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="be874-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="be874-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="be874-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="be874-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="be874-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="be874-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="be874-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="be874-112">*lpcharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="be874-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="be874-113">Die Zeichen, die in den Konsolenbildschirm Puffer geschrieben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="be874-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="be874-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="be874-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="be874-115">Die Anzahl der zu schreibenden Zeichen.</span><span class="sxs-lookup"><span data-stu-id="be874-115">The number of characters to be written.</span></span>

<span data-ttu-id="be874-116">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="be874-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="be874-117">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle im Konsolenbildschirm Puffer angibt, in die Zeichen geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="be874-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="be874-118">*lpnumofcharswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="be874-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="be874-119">Ein Zeiger auf eine Variable, die die Anzahl der tatsächlich geschriebenen Zeichen empfängt.</span><span class="sxs-lookup"><span data-stu-id="be874-119">A pointer to a variable that receives the number of characters actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="be874-120">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="be874-120">Return value</span></span>

<span data-ttu-id="be874-121">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="be874-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="be874-122">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="be874-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="be874-123">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="be874-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="be874-124">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="be874-124">Remarks</span></span>

<span data-ttu-id="be874-125">Wenn die Anzahl der Zeichen, in die geschrieben werden soll, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Zeichen in die nächste Zeile geschrieben.</span><span class="sxs-lookup"><span data-stu-id="be874-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="be874-126">Wenn die Anzahl der Zeichen, in die geschrieben werden soll, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden Zeichen bis zum Ende des Bildschirm Puffers der Konsole geschrieben.</span><span class="sxs-lookup"><span data-stu-id="be874-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="be874-127">Die Attributwerte an den Positionen, die in geschrieben werden, werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="be874-127">The attribute values at the positions written to are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="be874-128">Diese API verfügt über ein **[virtuelles Terminal](console-virtual-terminal-sequences.md)** Äquivalent in den Positions Sequenzen für **[Textformatierung](console-virtual-terminal-sequences.md#text-formatting)** und **[Cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="be874-128">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="be874-129">Bewegen Sie den Cursor an den einzufügenden Speicherort, wenden Sie die gewünschte Formatierung an, und schreiben Sie Text, um ihn auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="be874-129">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="be874-130">Es gibt keine Entsprechung für das Ausgeben von Text in einem Bereich, ohne auch die aktive Farb Formatierung anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="be874-130">There is no equivalent to emit text to an area without also applying the active color formatting.</span></span> <span data-ttu-id="be874-131">Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus, bei denen die jeweilige Client Anwendung ihren eigenen gezeichneten Zustand zur weiteren Bearbeitung merken soll.</span><span class="sxs-lookup"><span data-stu-id="be874-131">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="be874-132">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="be874-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="be874-133">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="be874-133">Minimum supported client</span></span> | <span data-ttu-id="be874-134">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="be874-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="be874-135">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="be874-135">Minimum supported server</span></span> | <span data-ttu-id="be874-136">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="be874-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="be874-137">Header</span><span class="sxs-lookup"><span data-stu-id="be874-137">Header</span></span> | <span data-ttu-id="be874-138">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="be874-138">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="be874-139">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="be874-139">Library</span></span> | <span data-ttu-id="be874-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="be874-140">Kernel32.lib</span></span> |
| <span data-ttu-id="be874-141">DLL</span><span class="sxs-lookup"><span data-stu-id="be874-141">DLL</span></span> | <span data-ttu-id="be874-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="be874-142">Kernel32.dll</span></span> |
| <span data-ttu-id="be874-143">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="be874-143">Unicode and ANSI names</span></span> | <span data-ttu-id="be874-144">" **Schreibconsoleoutputcharakteriw** (Unicode)" und " **Write Message consoleoutputcharakteria** (ANSI)"</span><span class="sxs-lookup"><span data-stu-id="be874-144">**WriteConsoleOutputCharacterW** (Unicode) and **WriteConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="be874-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="be874-145">See also</span></span>

[<span data-ttu-id="be874-146">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="be874-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="be874-147">**Koord**</span><span class="sxs-lookup"><span data-stu-id="be874-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="be874-148">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="be874-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="be874-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="be874-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="be874-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="be874-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="be874-151">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="be874-151">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="be874-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="be874-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="be874-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="be874-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="be874-154">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="be874-154">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="be874-155">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="be874-155">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)
