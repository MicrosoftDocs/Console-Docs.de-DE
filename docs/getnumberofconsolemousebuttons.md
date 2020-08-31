---
title: Getnumofconfiguration Manager-Funktion
description: Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
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
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060443"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="34071-104">Getnumofconfiguration Manager-Funktion</span><span class="sxs-lookup"><span data-stu-id="34071-104">GetNumberOfConsoleMouseButtons function</span></span>


<span data-ttu-id="34071-105">Ruft die Anzahl der Schaltflächen auf der Maus ab, die von der aktuellen Konsole verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="34071-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="34071-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="34071-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a><span data-ttu-id="34071-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="34071-107">Parameters</span></span>
----------

<span data-ttu-id="34071-108">*lpnumofmoulbuttons* \[ vorgenommen\]</span><span class="sxs-lookup"><span data-stu-id="34071-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="34071-109">Ein Zeiger auf eine Variable, die die Anzahl der Maustasten empfängt.</span><span class="sxs-lookup"><span data-stu-id="34071-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

<a name="return-value"></a><span data-ttu-id="34071-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="34071-110">Return value</span></span>
------------

<span data-ttu-id="34071-111">Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ungleich 0 (null).</span><span class="sxs-lookup"><span data-stu-id="34071-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="34071-112">Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null.</span><span class="sxs-lookup"><span data-stu-id="34071-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="34071-113">Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="34071-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="34071-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="34071-114">Remarks</span></span>
-------

<span data-ttu-id="34071-115">Wenn eine Konsole eine Mauseingabe empfängt, wird eine [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur, die eine [\*\* \_ \_ Daten Satzstruktur des Maus Ereignisses\*\*](mouse-event-record-str.md) enthält, in den Eingabepuffer der Konsole eingefügt.</span><span class="sxs-lookup"><span data-stu-id="34071-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="34071-116">Der **dwbuttonstate** -Member des **Maus \_ Ereignis \_ Datensatzes** weist ein Bit auf, das den Zustand der einzelnen Maustasten angibt.</span><span class="sxs-lookup"><span data-stu-id="34071-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="34071-117">Das Bit ist 1, wenn die Schaltfläche nicht gedrückt ist, und 0, wenn die Schaltfläche aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="34071-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="34071-118">Um die Anzahl der wichtigen Bits zu ermitteln, verwenden Sie **getnumofansolemousebuttons**.</span><span class="sxs-lookup"><span data-stu-id="34071-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

<a name="requirements"></a><span data-ttu-id="34071-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="34071-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="34071-120">Unterstützte Mindestversion (Client)</span><span class="sxs-lookup"><span data-stu-id="34071-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="34071-121">Windows 2000 Professional [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="34071-121">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="34071-122">Unterstützte Mindestversion (Server)</span><span class="sxs-lookup"><span data-stu-id="34071-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="34071-123">Windows 2000 Server [nur Desktop-Apps]</span><span class="sxs-lookup"><span data-stu-id="34071-123">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="34071-124">Header</span><span class="sxs-lookup"><span data-stu-id="34071-124">Header</span></span></p></td>
<td><span data-ttu-id="34071-125">ConsoleApi3. h (über WinCon. h, Include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="34071-125">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="34071-126">Bibliothek</span><span class="sxs-lookup"><span data-stu-id="34071-126">Library</span></span></p></td>
<td><span data-ttu-id="34071-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="34071-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="34071-128">DLL</span><span class="sxs-lookup"><span data-stu-id="34071-128">DLL</span></span></p></td>
<td><span data-ttu-id="34071-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="34071-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="34071-130"><span id="see_also"></span>Siehe auch</span><span class="sxs-lookup"><span data-stu-id="34071-130"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="34071-131">Konsolenfunktionen</span><span class="sxs-lookup"><span data-stu-id="34071-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="34071-132">Konsolen Eingabepuffer</span><span class="sxs-lookup"><span data-stu-id="34071-132">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="34071-133">**Read ConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="34071-133">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="34071-134">**Eingabe \_ Daten Satz**</span><span class="sxs-lookup"><span data-stu-id="34071-134">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="34071-135">**\_Ereignis \_ Daten Satz für Maus**</span><span class="sxs-lookup"><span data-stu-id="34071-135">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

 

 




