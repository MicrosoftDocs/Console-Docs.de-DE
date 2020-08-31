---
title: Bildschirm wird gelöscht
description: Löschen des Bildschirms der Windows-Konsole mithilfe der Systemfunktion oder Programm gesteuertes Verwenden von öffentlichen API-Funktionen.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: Konsolen-, Zeichenmodusanwendungen, Befehlszeilen Anwendungen, Terminalanwendungen, Konsolen-API
MS-HAID:
- '\_win32\_clearing\_the\_screen'
- base.clearing\_the\_screen
- consoles.clearing\_the\_screen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2097cc53-13b9-4f29-9d2c-feea56a27cb8
ms.openlocfilehash: fd2a407e56d6b0fe00db59c5f783cb13546119f6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060202"
---
# <a name="clearing-the-screen"></a>Bildschirm wird gelöscht


Es gibt zwei Möglichkeiten, den Bildschirm in einer Konsolenanwendung zu löschen.

## <a name="span-idexample_1spanspan-idexample_1spanspan-idexample_1spanexample-1"></a><span id="Example_1"></span><span id="example_1"></span><span id="EXAMPLE_1"></span>Beispiel 1


Die erste Methode besteht darin, die C-Lauf Zeit **System** Funktion zu verwenden. Die **System** Funktion Ruft den vom Befehls Interpreter bereitgestellten **CLS** -Befehl auf, um den Bildschirm zu löschen.

```C
#include <stdlib.h>

int main( void )
{
    system("cls");
    return 0;
}
```

## <a name="span-idexample_2spanspan-idexample_2spanspan-idexample_2spanexample-2"></a><span id="Example_2"></span><span id="example_2"></span><span id="EXAMPLE_2"></span>Beispiel 2


Die zweite Methode besteht darin, eine Funktion zu schreiben, um den Bildschirm mithilfe der [**fillconsoleoutputcharacter**](fillconsoleoutputcharacter.md) -und [**fillconsoleoutputattribute**](fillconsoleoutputattribute.md) -Funktionen Programm gesteuert zu löschen. Der folgende Beispielcode veranschaulicht diese Vorgehensweise.

```C
#include <windows.h>

void cls( HANDLE hConsole )
{
   COORD coordScreen = { 0, 0 };    // home for the cursor 
   DWORD cCharsWritten;
   CONSOLE_SCREEN_BUFFER_INFO csbi; 
   DWORD dwConSize;

// Get the number of character cells in the current buffer. 

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   dwConSize = csbi.dwSize.X * csbi.dwSize.Y;

   // Fill the entire screen with blanks.

   if( !FillConsoleOutputCharacter( hConsole,        // Handle to console screen buffer 
                                    (TCHAR) ' ',     // Character to write to the buffer
                                    dwConSize,       // Number of cells to write 
                                    coordScreen,     // Coordinates of first cell 
                                    &cCharsWritten ))// Receive number of characters written
   {
      return;
   }

   // Get the current text attribute.

   if( !GetConsoleScreenBufferInfo( hConsole, &csbi ))
   {
      return;
   }

   // Set the buffer's attributes accordingly.

   if( !FillConsoleOutputAttribute( hConsole,         // Handle to console screen buffer 
                                    csbi.wAttributes, // Character attributes to use
                                    dwConSize,        // Number of cells to set attribute 
                                    coordScreen,      // Coordinates of first cell 
                                    &cCharsWritten )) // Receive number of characters written
   {
      return;
   }

   // Put the cursor at its home coordinates.

   SetConsoleCursorPosition( hConsole, coordScreen );
}

int main( void )
{
    HANDLE hStdout;

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    cls(hStdout);
    
    return 0;
}
```

 

 




