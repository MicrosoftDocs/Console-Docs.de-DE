---
title: Getconsoleprocesslist-Funktion
description: Siehe Referenzinformationen zur getconsoleprocesslist-Funktion, die eine Liste der Prozesse abruft, die an die aktuelle Konsole angefügt sind.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsole, Zeichenmodusanwendungen, Befehlszeilenanwendungen, Terminalanwendungen, Konsolen-API
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bfc16edccb2f1be2b22c81992800d8f62d86cf4f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037982"
---
# <a name="getconsoleprocesslist-function"></a>Getconsoleprocesslist-Funktion

Ruft eine Liste der Prozesse ab, die an die aktuelle Konsole angefügt sind.

## <a name="syntax"></a>Syntax

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## <a name="parameters"></a>Parameter

*lpdwprocesslist* \[ vorgenommen\]  
Ein Zeiger auf einen Puffer, der bei erfolgreicher Ausführung ein Array von Prozess Bezeichners empfängt. Dies muss ein gültiger Puffer sein und darf nicht sein `NULL` . Der Puffer muss über Speicherplatz verfügen, um mindestens eine zurückgegebene Prozess-ID zu erhalten.

*dwprocesscount* \[ in\]  
Die maximale Anzahl von Prozess bezeichern, die im *lpdwprocesslist* -Puffer gespeichert werden können. Dieser Wert muss größer als 0 sein.

## <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, ist der Rückgabewert kleiner oder gleich *dwprocesscount* und stellt die Anzahl der Prozess-IDs dar, die im *lpdwprocesslist* -Puffer gespeichert werden.

Wenn der Puffer zu klein ist, um alle gültigen Prozess-IDs aufzunehmen, ist der Rückgabewert die erforderliche Anzahl von Array Elementen. Die Funktion hat keine Bezeichner im Puffer gespeichert. Verwenden Sie in dieser Situation den Rückgabewert, um einen Puffer zuzuordnen, der groß genug ist, um die gesamte Liste zu speichern und die Funktion erneut aufzurufen.

Wenn der Rückgabewert 0 (null) ist, ist bei der Funktion ein Fehler aufgetreten, da jeder Konsole mindestens ein Prozess zugeordnet ist. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Wenn eine `NULL` Prozessliste bereitgestellt wurde oder die Prozess Anzahl 0 war, gibt der-Befehl 0 zurück und `GetLastError` gibt zurück `ERROR_INVALID_PARAMETER` . Geben Sie einen Puffer mit mindestens einem-Element an, um diese Funktion aufzurufen. Weisen Sie einen größeren Puffer zu, und wiederholen Sie den Vorgang, wenn der Rückgabecode größer als die Länge des bereitgestellten Puffers ist.

## <a name="remarks"></a>Bemerkungen

Um eine Anwendung zu kompilieren, die diese Funktion verwendet, definieren Sie **\_ Win32 \_ Winnt** als 0x0501 oder höher. Weitere Informationen finden Sie unter [Verwenden der Windows-Header](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## <a name="requirements"></a>Requirements (Anforderungen)

| &nbsp; | &nbsp; |
|-|-|
| Unterstützte Mindestversion (Client) | Nur Windows XP \[ -Desktop-Apps\] |
| Unterstützte Mindestversion (Server) | Nur Windows Server 2003 \[ -Desktop-Apps\] |
| Header | ConsoleApi3. h (über WinCon. h, Include Windows. h) |
| Bibliothek | Kernel32. lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>Weitere Informationen

[**AttachConsole**](attachconsole.md)

[Konsolenfunktionen](console-functions.md)
