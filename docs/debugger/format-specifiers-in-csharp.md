---
title: Format Specyfikatory w debugerze (C#) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: fee9e4c355c83ae44cf6147084c95a3b213bce5a
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Specyfikatory formatu w C# w debugerze programu Visual Studio
Można zmienić format wyświetlania wartości w **czujki** okna używanie specyfikatorów formatu. Umożliwia także specyfikatory formatu w **Immediate** okna, **polecenia** okna w [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints), a nawet w systemie windows źródła. Jeśli zostanie wstrzymana na wyrażeniu w oknach, wyniki będą wyświetlane w etykietki danych. Etykietki danych będzie odzwierciedlać specyfikator formatu wyświetlania etykietek danych.  
  
 Aby użyć specyfikatora formatu, wpisz wyrażenie rozdzielanych przecinkami. Po przecinku Dodaj odpowiednie specyfikator.  
  
## <a name="using-format-specifiers"></a>Używanie specyfikatorów formatu  
 Jeśli masz następujący kod:  
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Dodaj `my_var1` zmienną do okna czujki (podczas debugowania, **debugowania > Windows > czujki > Obejrzyj 1**) i ustawić szesnastkowy (w **czujki** okna, kliknij prawym przyciskiem myszy zmienną i Wybierz **wyświetlacz**). Teraz **czujki** okna pokazuje, że zawiera on wartość 0x0065. Aby zobaczyć tę wartość, wyrażony jako dziesiętną liczbą całkowitą, a nie szesnastkową liczby całkowitej w kolumnie Nazwa po nazwie zmiennej, Dodaj specyfikator formatu dziesiętnego: **, d**. Wartość kolumny są obecnie wyświetlane wartości dziesiętnej 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Specyfikatory formatu  
 W poniższej tabeli przedstawiono C# rozpoznawanie specyfikatorów formatu przez debuger.  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wyświetla|  
|---------------|------------|--------------------------|--------------|  
|ac|Wymuszenie obliczenia wyrażenia. Może to być przydatne, jeśli niejawne obliczanie właściwości i niejawne wywołania funkcji jest wyłączona.|Komunikat "niejawne Obliczanie funkcji zostało wyłączone przez użytkownika"|\<wartość >|  
|d|dziesiętną liczbą całkowitą|0x0065|101|  
|dynamic|Wyświetla określony obiekt przy użyciu widoku dynamicznego|Wyświetla wszystkie elementy członkowskie obiektu, w tym widoku dynamicznego|Wyświetla widok dynamiczny|  
|h|Szesnastkowa liczba całkowita|61541|0x0000F065|  
|nq|Ciąg zawierający nie oferty|"Mój ciągu"|Moje ciągu|  
|hidden|Wyświetla wszystkie publiczne i niepubliczne elementy członkowskie|Wyświetla publiczne elementy członkowskie|Wyświetla wszystkie elementy członkowskie|  
|nieprzetworzone|Wyświetla elementu wyświetlaną w węźle elementu raw. Prawidłowy na tylko obiekty serwera proxy.|Słownik\<T >|Pierwotny widok słownika\<T >|  
|wyniki|Używany ze zmienną typu, który implementuje interfejs IEnumerable lub IEnumerable\<T >, zazwyczaj wynikiem wyrażenia zapytania. Wyświetla tylko elementy członkowskie, które zawierają wyniku zapytania.|Wyświetla wszystkie elementy członkowskie.|Wyświetla elementy Członkowskie spełniają warunki zapytania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Oglądanie i QuickWatch systemu Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Automatyczne i ustawień regionalnych systemu Windows](../debugger/autos-and-locals-windows.md)
