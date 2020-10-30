---
title: Fillconsoleoutputcharacter-Funktion
description: Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer, beginnend bei den angegebenen Koordinaten.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8860a1feab39bc83f28a867fa9acc491cc00e4b7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038188"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="d25a7-104">Fillconsoleoutputcharacter-Funktion</span><span class="sxs-lookup"><span data-stu-id="d25a7-104">FillConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d25a7-105">Schreibt ein Zeichen so oft wie angegeben in den Konsolenbildschirm Puffer, beginnend bei den angegebenen Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="d25a7-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

## <a name="syntax"></a><span data-ttu-id="d25a7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d25a7-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="d25a7-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="d25a7-107">Parameters</span></span>

<span data-ttu-id="d25a7-108">*hconsoleoutput* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d25a7-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d25a7-109">Ein Handle für den Bildschirm Puffer der Konsole.</span><span class="sxs-lookup"><span data-stu-id="d25a7-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d25a7-110">Das Handle muss über das **allgemeine \_ Schreib** Zugriffsrecht verfügen.</span><span class="sxs-lookup"><span data-stu-id="d25a7-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="d25a7-111">Weitere Informationen finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="d25a7-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d25a7-112">*ccharacter* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d25a7-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="d25a7-113">Das Zeichen, das in den Konsolenbildschirm Puffer geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="d25a7-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="d25a7-114">*nlength* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d25a7-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="d25a7-115">Die Anzahl der Zeichen Zellen, in die das Zeichen geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="d25a7-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="d25a7-116">*dwschreitecoord* \[ in\]</span><span class="sxs-lookup"><span data-stu-id="d25a7-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="d25a7-117">Eine [**Koord**](coord-str.md) -Struktur, die die Zeichen Koordinaten der ersten Zelle angibt, in die das Zeichen geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="d25a7-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="d25a7-118">*lpnumofcharswritten* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="d25a7-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="d25a7-119">Ein Zeiger auf eine Variable, die die Anzahl der Zeichen empfängt, die tatsächlich in den Konsolenbildschirm Puffer geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="d25a7-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="d25a7-120">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d25a7-120">Return value</span></span>

<span data-ttu-id="d25a7-121">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="d25a7-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d25a7-122">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="d25a7-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d25a7-123">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d25a7-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="d25a7-124">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="d25a7-124">Remarks</span></span>

<span data-ttu-id="d25a7-125">Wenn die Anzahl der Zeichen, die in geschrieben werden sollen, über das Ende der angegebenen Zeile im Konsolenbildschirm Puffer hinausgeht, werden Zeichen in die nächste Zeile geschrieben.</span><span class="sxs-lookup"><span data-stu-id="d25a7-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="d25a7-126">Wenn die Anzahl der Zeichen, in die geschrieben wird, über das Ende des Konsolenbildschirm Puffers hinausgeht, werden die Zeichen bis zum Ende des Bildschirm Puffers der Konsole geschrieben.</span><span class="sxs-lookup"><span data-stu-id="d25a7-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="d25a7-127">Die Attributwerte an den geschriebenen Positionen werden nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="d25a7-127">The attribute values at the positions written are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="d25a7-128">Diese API wird nicht empfohlen und weist keine bestimmte **[virtuelle Terminal](console-virtual-terminal-sequences.md)** Entsprechung auf.</span><span class="sxs-lookup"><span data-stu-id="d25a7-128">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="d25a7-129">Das Ausfüllen des Bereichs außerhalb des Anzeige Fensters wird nicht unterstützt und ist für den Verlaufs Bereich des Terminal reserviert.</span><span class="sxs-lookup"><span data-stu-id="d25a7-129">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="d25a7-130">Das Ausfüllen eines sichtbaren Bereichs mit neuem Text oder einer Farbe erfolgt durch **[das Verschieben des Cursors](console-virtual-terminal-sequences.md#cursor-positioning)** , **[das Festlegen der neuen Attribute](console-virtual-terminal-sequences.md#text-formatting)** , das anschließende Schreiben des gewünschten Texts für diesen Bereich und das Wiederholen von Zeichen, wenn dies für die Länge der Füllungs Ausführung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="d25a7-130">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)** , then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="d25a7-131">Möglicherweise ist eine zusätzliche Cursor Bewegung erforderlich, gefolgt von dem Schreiben des gewünschten Texts zum Ausfüllen eines rechteckigen Bereichs.</span><span class="sxs-lookup"><span data-stu-id="d25a7-131">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="d25a7-132">Es wird erwartet, dass die Client Anwendung ihren eigenen Arbeitsspeicher auf dem Bildschirm hält und den Remote Status nicht Abfragen kann.</span><span class="sxs-lookup"><span data-stu-id="d25a7-132">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="d25a7-133">Weitere Informationen finden Sie in der **[klassischen Konsole im Vergleich](classic-vs-vt.md)** zu der Dokumentation zu virtuellen Terminals.</span><span class="sxs-lookup"><span data-stu-id="d25a7-133">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="d25a7-134">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="d25a7-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d25a7-135">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="d25a7-135">Minimum supported client</span></span> | <span data-ttu-id="d25a7-136">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="d25a7-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d25a7-137">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="d25a7-137">Minimum supported server</span></span> | <span data-ttu-id="d25a7-138">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="d25a7-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d25a7-139">Header</span><span class="sxs-lookup"><span data-stu-id="d25a7-139">Header</span></span> | <span data-ttu-id="d25a7-140">ConsoleApi2. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d25a7-140">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d25a7-141">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="d25a7-141">Library</span></span> | <span data-ttu-id="d25a7-142">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d25a7-142">Kernel32.lib</span></span> |
| <span data-ttu-id="d25a7-143">DLL</span><span class="sxs-lookup"><span data-stu-id="d25a7-143">DLL</span></span> | <span data-ttu-id="d25a7-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d25a7-144">Kernel32.dll</span></span> |
| <span data-ttu-id="d25a7-145">Unicode- und ANSI-Name</span><span class="sxs-lookup"><span data-stu-id="d25a7-145">Unicode and ANSI names</span></span> | <span data-ttu-id="d25a7-146">**Fillconsoleoutputcharakteriw** (Unicode) und **fillconsoleoutputcharakteria** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="d25a7-146">**FillConsoleOutputCharacterW** (Unicode) and **FillConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="d25a7-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d25a7-147">See also</span></span>

[<span data-ttu-id="d25a7-148">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="d25a7-148">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d25a7-149">**Koord**</span><span class="sxs-lookup"><span data-stu-id="d25a7-149">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="d25a7-150">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="d25a7-150">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="d25a7-151">Konsolenausgabe Funktionen auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="d25a7-151">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="d25a7-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="d25a7-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="d25a7-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="d25a7-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="d25a7-154">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="d25a7-154">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
