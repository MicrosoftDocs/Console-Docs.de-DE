---
title: Funktion "kreateconsoleskreenbuffer"
description: Die Funktion "kreateconsoleskreenbuffer" erstellt einen Bildschirm Puffer für die Windows-Konsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0b8f5b33233f49167c67a47f33e5a95b8864f7bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039132"
---
# <a name="createconsolescreenbuffer-function"></a>Funktion "kreateconsoleskreenbuffer"

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Erstellt einen Konsolenbildschirm Puffer.

## <a name="syntax"></a>Syntax

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a>Parameter

*dwDesiredAccess* \[ in\]  
Der Zugriff auf den Konsolenbildschirm Puffer. Eine Liste der Zugriffsrechte finden Sie unter [Sicherheit und Zugriffsrechte für die Konsolen Puffer](console-buffer-security-and-access-rights.md).

*dwsharemode* \[ in\]  
Dieser Parameter kann NULL sein, um anzugeben, dass der Puffer nicht freigegeben werden kann, oder es kann sich um einen oder mehrere der folgenden Werte handeln.

| Wert | Bedeutung |
|-|-|
| **FILE_SHARE_READ** 0x00000001 | Andere geöffnete Vorgänge können auf dem Konsolenbildschirm Puffer für den Lesezugriff ausgeführt werden. |
| **FILE_SHARE_WRITE** 0x00000002 | Andere geöffnete Vorgänge können auf dem Konsolenbildschirm Puffer für Schreibzugriffe ausgeführt werden. |

*lpsecurityattribute* \[ in, optional\]  
Ein Zeiger auf eine Struktur von [**Sicherheits \_ Attributen**](https://msdn.microsoft.com/library/windows/desktop/aa379560) , die bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann. Wenn *lpsecurityattribute* **null** ist, kann das Handle nicht geerbt werden. Der **lpsecuritydescriptor** -Member der-Struktur gibt eine Sicherheits Beschreibung für den neuen Konsolenbildschirm Puffer an. Wenn *lpsecurityattribute* **null** ist, erhält der Konsolenbildschirm Puffer eine Standard Sicherheits Beschreibung. Die ACLs in der Standard Sicherheits Beschreibung eines Konsolenbildschirm Puffers stammen aus dem primären Token oder dem Identitätswechsel Token des Erstellers.

*dwFlags* \[ in\]  
Der Typ des zu erstellenden Konsolenbildschirm Puffers. Der einzige unterstützte Bildschirm Puffertyp ist der **Konsolen \_ TextMode- \_ Puffer** .

*lpscreenbufferdata*  
Bleiben muss **null** sein.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert ein Handle für den neuen Konsolenbildschirm Puffer.

Wenn die Funktion fehlschlägt, ist der Rückgabewert ein **ungültiger \_ handle- \_ Wert** . Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Bemerkungen

Eine Konsole kann über mehrere Bildschirm Puffer verfügen, aber nur einen aktiven Bildschirm Puffer. Der Zugriff auf inaktive Bildschirm Puffer ist für Lese-und Schreibvorgänge möglich, es wird jedoch nur der aktive Bildschirm Puffer angezeigt. Verwenden Sie die Funktion [**setconsoleactiveskreenbuffer**](setconsoleactivescreenbuffer.md) , damit der neue Bildschirm den Puffer für den aktiven Bildschirm puffert.

Der neu erstellte Bildschirm Puffer kopiert einige Eigenschaften aus dem Puffer des aktiven Bildschirms, wenn diese Funktion aufgerufen wird. Das Verhalten sieht wie folgt aus:

- `Font` -kopiert aus dem aktiven Bildschirm Puffer
- `Display Window Size` -kopiert aus dem aktiven Bildschirm Puffer
- `Buffer Size` -Übereinstimmung mit `Display Window Size` ( **nicht** kopiert)
- `Default Attributes` (Farben)-aus aktivem Bildschirm Puffer kopiert
- `Default Popup Attributes` (Farben)-aus aktivem Bildschirm Puffer kopiert

Der aufrufenden Prozess kann das zurückgegebene Handle in jeder Funktion verwenden, die ein Handle für einen Konsolenbildschirm Puffer erfordert, je nach den Einschränkungen des Zugriffs, der durch den *dwDesiredAccess* -Parameter angegeben wird.

Der aufrufenden Prozess kann die [**duplikatandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) -Funktion verwenden, um ein doppeltes Bildschirm Puffer Handle zu erstellen, das über einen anderen Zugriff oder eine andere Vererbbarkeit als das ursprüngliche Handle verfügt. **Duplikatandle** kann jedoch nicht zum Erstellen eines Duplikats verwendet werden, das für einen anderen Prozess gültig ist (außer durch Vererbung).

Verwenden Sie die [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) -Funktion, um das Bildschirm Puffer Handle der Konsole zu schließen.

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a>Beispiele

Ein Beispiel finden Sie unter [Lesen und Schreiben von Zeichen-und Attribut Blöcken](reading-and-writing-blocks-of-characters-and-attributes.md).

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows 2000 Professional \[ Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows 2000 \[ -Server Desktop-Apps\] |
| Header | ConsoleApi2. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[Konsolenfunktionen](console-functions.md)

[Konsolenbildschirmpuffer](console-screen-buffers.md)

[**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[**Duplialisiehandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**Sicherheits \_ Attribute**](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)
