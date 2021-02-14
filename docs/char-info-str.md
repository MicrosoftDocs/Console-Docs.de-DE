---
title: CHAR_INFO Struktur
description: Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an. Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357850"
---
# `CHAR\_INFO structure`

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="53e10-105">Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an.</span><span class="sxs-lookup"><span data-stu-id="53e10-105">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="53e10-106">Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="53e10-106">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="53e10-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="53e10-107">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="53e10-108">Member</span><span class="sxs-lookup"><span data-stu-id="53e10-108">Members</span></span>

<span data-ttu-id="53e10-109">**Char**</span><span class="sxs-lookup"><span data-stu-id="53e10-109">**Char**</span></span>  
<span data-ttu-id="53e10-110">Eine Union der folgenden Member.</span><span class="sxs-lookup"><span data-stu-id="53e10-110">A union of the following members.</span></span>

<span data-ttu-id="53e10-111">**Unicodechar**</span><span class="sxs-lookup"><span data-stu-id="53e10-111">**UnicodeChar**</span></span>  
<span data-ttu-id="53e10-112">Unicode-Zeichen einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="53e10-112">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="53e10-113">**Asciichar**</span><span class="sxs-lookup"><span data-stu-id="53e10-113">**AsciiChar**</span></span>  
<span data-ttu-id="53e10-114">ANSI-Zeichen einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="53e10-114">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="53e10-115">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="53e10-115">**Attributes**</span></span>  
<span data-ttu-id="53e10-116">Die Zeichen Attribute.</span><span class="sxs-lookup"><span data-stu-id="53e10-116">The character attributes.</span></span> <span data-ttu-id="53e10-117">Dieser Member kann NULL oder eine beliebige Kombination der folgenden Werte sein.</span><span class="sxs-lookup"><span data-stu-id="53e10-117">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="53e10-118">Wert</span><span class="sxs-lookup"><span data-stu-id="53e10-118">Value</span></span> | <span data-ttu-id="53e10-119">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="53e10-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="53e10-120">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="53e10-120">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="53e10-121">Die Textfarbe enthält Blau.</span><span class="sxs-lookup"><span data-stu-id="53e10-121">Text color contains blue.</span></span> |
| <span data-ttu-id="53e10-122">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="53e10-122">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="53e10-123">Die Textfarbe enthält Grün.</span><span class="sxs-lookup"><span data-stu-id="53e10-123">Text color contains green.</span></span> |
| <span data-ttu-id="53e10-124">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="53e10-124">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="53e10-125">Die Textfarbe enthält Rot.</span><span class="sxs-lookup"><span data-stu-id="53e10-125">Text color contains red.</span></span> |
| <span data-ttu-id="53e10-126">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="53e10-126">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="53e10-127">Die Textfarbe wird verstärkt.</span><span class="sxs-lookup"><span data-stu-id="53e10-127">Text color is intensified.</span></span> |
| <span data-ttu-id="53e10-128">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="53e10-128">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="53e10-129">Die Hintergrundfarbe enthält Blau.</span><span class="sxs-lookup"><span data-stu-id="53e10-129">Background color contains blue.</span></span> |
| <span data-ttu-id="53e10-130">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="53e10-130">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="53e10-131">Die Hintergrundfarbe enthält Grün.</span><span class="sxs-lookup"><span data-stu-id="53e10-131">Background color contains green.</span></span> |
| <span data-ttu-id="53e10-132">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="53e10-132">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="53e10-133">Die Hintergrundfarbe enthält Rot.</span><span class="sxs-lookup"><span data-stu-id="53e10-133">Background color contains red.</span></span> |
| <span data-ttu-id="53e10-134">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="53e10-134">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="53e10-135">Die Hintergrundfarbe wird verstärkt.</span><span class="sxs-lookup"><span data-stu-id="53e10-135">Background color is intensified.</span></span> |
| <span data-ttu-id="53e10-136">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="53e10-136">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="53e10-137">Führendes Byte.</span><span class="sxs-lookup"><span data-stu-id="53e10-137">Leading byte.</span></span> |
| <span data-ttu-id="53e10-138">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="53e10-138">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="53e10-139">Schließendes Byte.</span><span class="sxs-lookup"><span data-stu-id="53e10-139">Trailing byte.</span></span> |
| <span data-ttu-id="53e10-140">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="53e10-140">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="53e10-141">Oben horizontal.</span><span class="sxs-lookup"><span data-stu-id="53e10-141">Top horizontal.</span></span> |
| <span data-ttu-id="53e10-142">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="53e10-142">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="53e10-143">Links vertikal.</span><span class="sxs-lookup"><span data-stu-id="53e10-143">Left vertical.</span></span> |
| <span data-ttu-id="53e10-144">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="53e10-144">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="53e10-145">Rechts vertikal.</span><span class="sxs-lookup"><span data-stu-id="53e10-145">Right vertical.</span></span> |
| <span data-ttu-id="53e10-146">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="53e10-146">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="53e10-147">Umgekehrtes Vordergrund-und Hintergrund Attribut.</span><span class="sxs-lookup"><span data-stu-id="53e10-147">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="53e10-148">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="53e10-148">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="53e10-149">Unterstrich.</span><span class="sxs-lookup"><span data-stu-id="53e10-149">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="53e10-150">Beispiele</span><span class="sxs-lookup"><span data-stu-id="53e10-150">Examples</span></span>

<span data-ttu-id="53e10-151">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="53e10-151">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="53e10-152">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="53e10-152">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="53e10-153">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="53e10-153">Minimum supported client</span></span> | <span data-ttu-id="53e10-154">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="53e10-154">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="53e10-155">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="53e10-155">Minimum supported server</span></span> | <span data-ttu-id="53e10-156">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="53e10-156">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="53e10-157">Header</span><span class="sxs-lookup"><span data-stu-id="53e10-157">Header</span></span> | <span data-ttu-id="53e10-158">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="53e10-158">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="53e10-159">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="53e10-159">See also</span></span>

[<span data-ttu-id="53e10-160">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="53e10-160">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="53e10-161">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="53e10-161">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="53e10-162">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="53e10-162">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
