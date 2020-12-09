---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037032"
---
Diese Funktion verwendet entweder Unicodezeichen oder 8-Bit-Zeichen aus der aktuellen Codepage der Konsole. Die Codepage der Konsole wird zunächst standardmäßig auf die OEM-Codepage des Systems festgelegt. Um die Codepage der Konsole zu ändern, verwenden Sie die Funktionen [**SetConsoleCP**](../setconsolecp.md) oder [**SetConsoleOutputCP**](../setconsoleoutputcp.md). Ältere Consumer können auch die **chcp** oder **mode con cp select=** -Befehle verwenden, aber sie werden für neue Entwicklungen nicht empfohlen.