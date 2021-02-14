---
title: Getnumofconfiguration Manager-Funktion
description: Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4a2f936ac778b13985aa0c1d237c59e9f993d995
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358850"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="0d88f-104">Getnumofconfiguration Manager-Funktion</span><span class="sxs-lookup"><span data-stu-id="0d88f-104">GetNumberOfConsoleMouseButtons function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0d88f-105">Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0d88f-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d88f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d88f-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a><span data-ttu-id="0d88f-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="0d88f-107">Parameters</span></span>

<span data-ttu-id="0d88f-108">*lpnumofmoulbuttons* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="0d88f-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="0d88f-109">Ein Zeiger auf eine Variable, die die Anzahl der Maustasten empfängt.</span><span class="sxs-lookup"><span data-stu-id="0d88f-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d88f-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0d88f-110">Return value</span></span>

<span data-ttu-id="0d88f-111">Wenn die Funktion erfolgreich ist, ist der Rückgabewert ungleich Null.</span><span class="sxs-lookup"><span data-stu-id="0d88f-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0d88f-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="0d88f-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0d88f-113">Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf.</span><span class="sxs-lookup"><span data-stu-id="0d88f-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0d88f-114">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="0d88f-114">Remarks</span></span>

<span data-ttu-id="0d88f-115">Wenn eine Konsole eine Mauseingabe empfängt, wird eine [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur, die eine [**\_ \_ Daten Satzstruktur des Maus Ereignisses**](mouse-event-record-str.md) enthält, in den Eingabepuffer der Konsole eingefügt.</span><span class="sxs-lookup"><span data-stu-id="0d88f-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="0d88f-116">Der **dwbuttonstate** -Member des **Maus \_ Ereignis \_ Datensatzes** weist ein Bit auf, das den Zustand der einzelnen Maustasten angibt.</span><span class="sxs-lookup"><span data-stu-id="0d88f-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="0d88f-117">Das Bit ist 1, wenn die Schaltfläche nicht gedrückt ist, und 0, wenn die Schaltfläche aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="0d88f-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="0d88f-118">Um die Anzahl der wichtigen Bits zu ermitteln, verwenden Sie **getnumofansolemousebuttons**.</span><span class="sxs-lookup"><span data-stu-id="0d88f-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

> [!TIP]
> <span data-ttu-id="0d88f-119">Diese API wird nicht empfohlen und verfügt nicht über ein entsprechendes **[virtuelles Terminal](console-virtual-terminal-sequences.md)** .</span><span class="sxs-lookup"><span data-stu-id="0d88f-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="0d88f-120">Diese Entscheidung richtet die Windows-Plattform absichtlich mit anderen Betriebssystemen aus.</span><span class="sxs-lookup"><span data-stu-id="0d88f-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="0d88f-121">Dieser Status ist nur für den lokalen Benutzer-, Sitzungs-und Berechtigungs Kontext relevant.</span><span class="sxs-lookup"><span data-stu-id="0d88f-121">This state is only relevant to the local user, session, and privilege context.</span></span> <span data-ttu-id="0d88f-122">Anwendungen, die Remoting über plattformübergreifende Hilfsprogramme und Transporte wie ssh verwenden, funktionieren möglicherweise nicht wie erwartet, wenn Sie diese API verwenden.</span><span class="sxs-lookup"><span data-stu-id="0d88f-122">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d88f-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0d88f-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0d88f-124">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="0d88f-124">Minimum supported client</span></span> | <span data-ttu-id="0d88f-125">Windows 2000 Professional \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0d88f-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0d88f-126">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="0d88f-126">Minimum supported server</span></span> | <span data-ttu-id="0d88f-127">Windows 2000 Server \[nur Desktop-Apps\]</span><span class="sxs-lookup"><span data-stu-id="0d88f-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0d88f-128">Header</span><span class="sxs-lookup"><span data-stu-id="0d88f-128">Header</span></span> | <span data-ttu-id="0d88f-129">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0d88f-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0d88f-130">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="0d88f-130">Library</span></span> | <span data-ttu-id="0d88f-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0d88f-131">Kernel32.lib</span></span> |
| <span data-ttu-id="0d88f-132">DLL</span><span class="sxs-lookup"><span data-stu-id="0d88f-132">DLL</span></span> | <span data-ttu-id="0d88f-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0d88f-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0d88f-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0d88f-134">See also</span></span>

[<span data-ttu-id="0d88f-135">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="0d88f-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0d88f-136">Konsoleneingabepuffer</span><span class="sxs-lookup"><span data-stu-id="0d88f-136">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="0d88f-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="0d88f-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="0d88f-138">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="0d88f-138">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="0d88f-139">**\_Ereignis \_ Daten Satz für Maus**</span><span class="sxs-lookup"><span data-stu-id="0d88f-139">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)