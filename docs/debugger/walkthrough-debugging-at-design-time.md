---
title: "Wskazówki: Debugowanie w czasie projektowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5869279a7bafb11368b7fb232e6ca68ca7d98478
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-at-design-time"></a>Wskazówki: debugowanie w czasie projektowania
Można użyć programu Visual Studio **Immediate** okno, aby wykonać funkcji lub procedury, gdy aplikacja nie jest uruchomiona. Jeśli funkcja lub procedura zawiera punkt przerwania, Visual Studio spowoduje przerwanie wykonywania we właściwym momencie. Następnie można okna debugera Sprawdź swój stan programu. Ta funkcja jest nazywana debugowanie w czasie projektowania.  
  
 W poniższej procedurze wyjaśniono, jak można użyć tej funkcji.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Trafienie punktów przerwania w oknie bezpośrednim  
  
1.  Wklej następujący kod w aplikacji konsoli języka Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Ustaw punkt przerwania w wierszu, `s="Add BreakPoint Here"`.  
  
3.  Wpisz następujące polecenie w **Immediate** okno:`?MyFunction<enter>`  
  
4.  Sprawdź, czy punkt przerwania został trafiony i że stosu wywołań są prawidłowe.  
  
5.  Na **debugowania** menu, kliknij przycisk **Kontynuuj**i upewnij się, że jesteś nadal w trybie projektowania.  
  
6.  Wpisz następujące polecenie w **Immediate** okno:`?MyFunction<enter>`  
  
7.  Wpisz następujące polecenie w **Immediate** okno:`?MySub<enter>`  
  
8.  Sprawdź, czy trafiony punkt przerwania i sprawdź wartość statyczna zmienna `i` w **zmiennych lokalnych** okna. Powinien mieć wartość 3.  
  
9. Sprawdź, czy stos wywołań jest dokładne.  
  
10. Na **debugowania** menu, kliknij przycisk **Kontynuuj**i upewnij się, że jesteś nadal w trybie projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)