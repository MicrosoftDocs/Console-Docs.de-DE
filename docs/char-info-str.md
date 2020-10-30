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
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037378"
---
# <a name="char_info-structure"></a><span data-ttu-id="6e797-105">Char \_ Info-Struktur</span><span class="sxs-lookup"><span data-stu-id="6e797-105">CHAR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="6e797-106">Gibt ein Unicode-oder ANSI-Zeichen und seine Attribute an.</span><span class="sxs-lookup"><span data-stu-id="6e797-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="6e797-107">Diese Struktur wird von Konsolenfunktionen verwendet, um aus einem Konsolenbildschirm Puffer zu lesen und in diesen zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="6e797-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e797-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e797-108">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="6e797-109">Member</span><span class="sxs-lookup"><span data-stu-id="6e797-109">Members</span></span>

<span data-ttu-id="6e797-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="6e797-110">**Char**</span></span>  
<span data-ttu-id="6e797-111">Eine Union der folgenden Member.</span><span class="sxs-lookup"><span data-stu-id="6e797-111">A union of the following members.</span></span>

<span data-ttu-id="6e797-112">**Unicodechar**</span><span class="sxs-lookup"><span data-stu-id="6e797-112">**UnicodeChar**</span></span>  
<span data-ttu-id="6e797-113">Unicode-Zeichen einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="6e797-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="6e797-114">**Asciichar**</span><span class="sxs-lookup"><span data-stu-id="6e797-114">**AsciiChar**</span></span>  
<span data-ttu-id="6e797-115">ANSI-Zeichen einer Bildschirm Puffer-Zeichen Zelle.</span><span class="sxs-lookup"><span data-stu-id="6e797-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="6e797-116">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="6e797-116">**Attributes**</span></span>  
<span data-ttu-id="6e797-117">Die Zeichen Attribute.</span><span class="sxs-lookup"><span data-stu-id="6e797-117">The character attributes.</span></span> <span data-ttu-id="6e797-118">Dieser Member kann NULL oder eine beliebige Kombination der folgenden Werte sein.</span><span class="sxs-lookup"><span data-stu-id="6e797-118">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="6e797-119">Wert</span><span class="sxs-lookup"><span data-stu-id="6e797-119">Value</span></span> | <span data-ttu-id="6e797-120">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="6e797-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="6e797-121">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="6e797-121">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="6e797-122">Textfarbe enthält blau.</span><span class="sxs-lookup"><span data-stu-id="6e797-122">Text color contains blue.</span></span> |
| <span data-ttu-id="6e797-123">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="6e797-123">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="6e797-124">Textfarbe enthält grün.</span><span class="sxs-lookup"><span data-stu-id="6e797-124">Text color contains green.</span></span> |
| <span data-ttu-id="6e797-125">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="6e797-125">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="6e797-126">Textfarbe enthält rot.</span><span class="sxs-lookup"><span data-stu-id="6e797-126">Text color contains red.</span></span> |
| <span data-ttu-id="6e797-127">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="6e797-127">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="6e797-128">Die Textfarbe wird verstärkt.</span><span class="sxs-lookup"><span data-stu-id="6e797-128">Text color is intensified.</span></span> |
| <span data-ttu-id="6e797-129">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="6e797-129">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="6e797-130">Hintergrundfarbe enthält blau.</span><span class="sxs-lookup"><span data-stu-id="6e797-130">Background color contains blue.</span></span> |
| <span data-ttu-id="6e797-131">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="6e797-131">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="6e797-132">Hintergrundfarbe enthält grün.</span><span class="sxs-lookup"><span data-stu-id="6e797-132">Background color contains green.</span></span> |
| <span data-ttu-id="6e797-133">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="6e797-133">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="6e797-134">Die Hintergrundfarbe enthält rot.</span><span class="sxs-lookup"><span data-stu-id="6e797-134">Background color contains red.</span></span> |
| <span data-ttu-id="6e797-135">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="6e797-135">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="6e797-136">Die Hintergrundfarbe wird verstärkt.</span><span class="sxs-lookup"><span data-stu-id="6e797-136">Background color is intensified.</span></span> |
| <span data-ttu-id="6e797-137">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="6e797-137">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="6e797-138">Führendes Byte.</span><span class="sxs-lookup"><span data-stu-id="6e797-138">Leading byte.</span></span> |
| <span data-ttu-id="6e797-139">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="6e797-139">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="6e797-140">Nachfolgendes Byte.</span><span class="sxs-lookup"><span data-stu-id="6e797-140">Trailing byte.</span></span> |
| <span data-ttu-id="6e797-141">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="6e797-141">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="6e797-142">Obere horizontale.</span><span class="sxs-lookup"><span data-stu-id="6e797-142">Top horizontal.</span></span> |
| <span data-ttu-id="6e797-143">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="6e797-143">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="6e797-144">Links vertikal.</span><span class="sxs-lookup"><span data-stu-id="6e797-144">Left vertical.</span></span> |
| <span data-ttu-id="6e797-145">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="6e797-145">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="6e797-146">Rechts vertikal.</span><span class="sxs-lookup"><span data-stu-id="6e797-146">Right vertical.</span></span> |
| <span data-ttu-id="6e797-147">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="6e797-147">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="6e797-148">Umgekehrtes Vordergrund-und Hintergrund Attribut.</span><span class="sxs-lookup"><span data-stu-id="6e797-148">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="6e797-149">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="6e797-149">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="6e797-150">Unterstrich.</span><span class="sxs-lookup"><span data-stu-id="6e797-150">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="6e797-151">Beispiele</span><span class="sxs-lookup"><span data-stu-id="6e797-151">Examples</span></span>

<span data-ttu-id="6e797-152">Ein Beispiel finden Sie unter [Scrollen des Inhalts eines Bildschirm Puffers](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="6e797-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6e797-153">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="6e797-153">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6e797-154">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="6e797-154">Minimum supported client</span></span> | <span data-ttu-id="6e797-155">Nur Windows 2000 Professional \[ Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6e797-155">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6e797-156">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="6e797-156">Minimum supported server</span></span> | <span data-ttu-id="6e797-157">Nur Windows 2000 \[ -Server Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="6e797-157">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6e797-158">Header</span><span class="sxs-lookup"><span data-stu-id="6e797-158">Header</span></span> | <span data-ttu-id="6e797-159">WinCon. h (Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6e797-159">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="6e797-160">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6e797-160">See also</span></span>

[<span data-ttu-id="6e797-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="6e797-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="6e797-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="6e797-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="6e797-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="6e797-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
