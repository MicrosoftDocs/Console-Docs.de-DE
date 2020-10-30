---
title: FOCUS_EVENT_RECORD-Struktur
description: Beschreibt ein Fokus Ereignis in einer Konsolen Eingabe \_ Daten Satzstruktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dc86c1b5b1c42a9d905673da4ea368de76a5fae9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038168"
---
# <a name="focus_event_record-structure"></a>Struktur des Fokus \_ Ereignis \_ Datensatzes

Beschreibt ein Fokus Ereignis in einer Konsolen [**Eingabe \_ Daten Satz**](input-record-str.md) Struktur. Diese Ereignisse werden intern verwendet und sollten ignoriert werden.

## <a name="syntax"></a>Syntax

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## <a name="members"></a>Member

**bsetfocus**  
Reserviert.

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | Wincontypes. h (über WinCon. h, Include Windows. h) |

## <a name="see-also"></a>Weitere Informationen

[**Eingabe \_ Daten Satz**](input-record-str.md)
