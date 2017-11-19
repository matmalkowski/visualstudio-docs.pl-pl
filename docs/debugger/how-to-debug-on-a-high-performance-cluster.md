---
title: "Porady: debugowanie w klastrze wysokiej wydajności | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb07ad37e8522e2a893edbc7fba86e359893b812
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Porady: debugowanie w klastrze o wysokiej wydajności
Debugowanie programu przetwarzanie wieloprocesorowe w klastrze wysokiej wydajności jest podobne do debugowania zwykłego programu na komputerze zdalnym. Istnieje jednak kilka dodatkowych kwestii dotyczących. Wymagania ogólne ustawienia zdalnego, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).  
  
 Podczas debugowania w klastrze wysokiej wydajności, można używać wszystkich [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowania systemu windows i techniki, które są dostępne do zdalnego debugowania. Ponieważ debugowanie zdalne jednak okna konsoli zewnętrznych nie jest dostępna.  
  
 **Wątków** okna i **procesów** okna są szczególnie przydatne w przypadku debugowanie aplikacji równoległych. Aby uzyskać wskazówki dotyczące sposobu używania tych z systemem windows, zobacz [porady: Korzystanie z okna procesów](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) i [wskazówki: debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).  
  
 W poniższych procedurach przedstawiono niektóre techniki, które są szczególnie użyteczne w przypadku debugowania w klastrze wysokiej wydajności.  
  
 Podczas debugowania aplikacji równoległych można ustawić punktu przerwania dla określonego wątku, proces lub komputera. Można to zrobić, tworząc punktu przerwania normalne, a następnie dodanie filtru punktu przerwania.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Aby otworzyć okno dialogowe filtru punktu przerwania  
  
1.  Kliknij prawym przyciskiem myszy symbol punktu przerwania w oknie źródła **dezasemblacji** okna, **stos wywołań** okna, lub **punktów przerwania** okna.  
  
2.  W menu skrótów kliknij **filtru**. Ta opcja może pojawić się u góry poziom lub w podmenu w obszarze **punktów przerwania**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Aby ustawić punkt przerwania na określonym komputerze  
  
1.  Pobierz nazwę komputera z **procesów** okna.  
  
2.  Wybierz punkt przerwania, a następnie otwórz **filtru punktu przerwania** okno dialogowe zgodnie z opisem w poprzedniej procedurze.  
  
3.  W **filtru punktu przerwania** okno dialogowe, wpisz:  
  
     MachineName =*yourmachinename*  
  
     Do utworzenia bardziej złożonych filtrów, możesz łączyć klauzule przy użyciu `&`, operator i `||`, OR operator `!`, operator i nawiasy.  
  
4.  Kliknij przycisk **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Aby ustawić punkt przerwania dla określonego procesu  
  
1.  Pobierz długość nazwy procesu lub przetworzyć numer identyfikacyjny z **procesów** okna.  
  
2.  Wybierz punkt przerwania, a następnie otwórz **filtru punktu przerwania** okno dialogowe jak pierwszej procedury.  
  
3.  W **filtru punktu przerwania** okno dialogowe, wpisz:  
  
     `ProcessName =`  *yourprocessname*  
  
     —lub—  
  
     `ProcessID =`*yourprocessIDnumber*  
  
     Do utworzenia bardziej złożonych filtrów, możesz łączyć klauzule przy użyciu `&`, operator i `||`, OR operator `!`, operator i nawiasy.  
  
4.  Kliknij przycisk **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Aby ustawić punkt przerwania w konkretnym wątkiem  
  
1.  Uzyskać nazwy wątku lub wątku numer identyfikacyjny z **wątków** okna.  
  
2.  Wybierz punkt przerwania, a następnie otwórz **filtru punktu przerwania** okno dialogowe zgodnie z opisem w ramach pierwszej procedury.  
  
3.  W **filtru punktu przerwania** okno dialogowe, wpisz:  
  
     `ThreadName =`*yourthreadname*  
  
     —lub—  
  
     `ThreadID =`*yourthreadIDnumber*  
  
     Do utworzenia bardziej złożonych filtrów, możesz łączyć klauzule przy użyciu `&`, operator i `||`, OR operator `!`, operator i nawiasy.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób utworzyć filtr dla punktu przerwania na komputerze o nazwie `marvin` i wątku o nazwie `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)   
 [Porady: Korzystanie z okna procesów](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Wątków i procesów](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)