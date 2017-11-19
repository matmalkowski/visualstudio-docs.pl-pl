---
title: Funkcja automatycznego zawieszenia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: a2c836364092aa71f40d4d7aa4566b2d12def00e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="automatic-feature-suspension"></a>Funkcja automatycznej zawieszenia
Jeśli pamięci dostępnej w systemie znajduje się 200 MB lub mniej, Visual Studio wyświetli następujący komunikat w edytorze kodu.  
  
 ![Tekst alertu wstrzymywania Pełna analiza rozwiązania](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
 Visual Studio, wykrycie braku pamięci, automatycznie wstrzymuje niektórych zaawansowanych funkcji, aby ułatwić trwały. Gdy to zaawansowane pojawi się ostrzeżenie zawieszenia funkcji, Visual Studio będą w dalszym ciągu działać tak jak poprzednio, ale jego wydajność, można nieco ograniczone.  
  
 Stan braku pamięci są następujące:  
  
-   Pełna analiza rozwiązania dla programu Visual C# i Visual Basic jest wyłączona.  
  
-   [Wyrzucanie elementów bezużytecznych](/dotnet/standard/garbage-collection/index) tryb małych opóźnieniach (GC) dla programu Visual C# i Visual Basic są wyłączone.  
  
-   Visual Studio pamięci podręcznych są opróżniane.  
  
## <a name="improve-visual-studio-performance"></a>Poprawianie wydajności programu Visual Studio  
 Aby uzyskać porady i wskazówki na temat sposobów usprawnienia wydajności programu Visual Studio podczas pracy z rozwiązaniami dużych i ilość pamięci jest mała, zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).  
  
## <a name="full-solution-analysis-suspended"></a>Pełna analiza rozwiązania zawieszone  
 Domyślnie Pełna analiza rozwiązania jest włączona dla programu Visual Basic i wyłączone Visual C#. Jednak w stanie małej ilości pamięci, pełną analizę rozwiązania jest automatycznie wyłączana dla języka Visual Basic i Visual C#, niezależnie od ich ustawień w oknie dialogowym Opcje. Jednak można ponownie włączyć pełną analizę rozwiązania, wybierając **ponownie włączyć** przycisk informacji pasek po jego wyświetleniu wybierając **Włącz pełną analizę rozwiązania** pole wyboru w oknie dialogowym Opcje lub przez ponowne uruchomienie programu Visual Studio. Opcje — okno dialogowe zawsze zawiera bieżące rozwiązanie pełne ustawienia analizy. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).  
  
## <a name="gc-low-latency-disabled"></a>Wykaz Globalny małych opóźnieniach wyłączone  
 Aby ponownie włączyć tryb małych opóźnieniach GC, uruchom ponownie program Visual Studio.  Domyślnie program Visual Studio pozwala tryb małych opóźnieniach GC miarę wpisywania, aby upewnić się, że wpisane hasło nie blokują żadnych operacji GC. Jednak jeśli niedobór pamięci powoduje, że Visual Studio, aby wyświetlić ostrzeżenie automatyczne zawieszenie, tryb małych opóźnieniach GC jest wyłączone dla tej sesji. Ponowne uruchomienie programu Visual Studio ponownie włączyć domyślne zachowanie GC. Aby uzyskać więcej informacji, zobacz [wyliczenie GCLatencyMode](http://msdn.microsoft.com/Library/057757a5-cd62-4d13-8a40-370eb7f47c87).  
  
## <a name="visual-studio-caches-flushed"></a>Visual Studio pamięci podręcznych opróżniany  
 Wszystkich usług pamięć podręczna programu Visual Studio natychmiast zostały opróżnione, ale rozpocznie się ponownie uzupełniana kontynuować bieżącej sesji rozwoju lub uruchom ponownie program Visual Studio. Pamięci podręczne opróżnionych obejmują pamięci podręcznych następujące funkcje.  
  
-   Znajdź wszystkie odwołania  
  
-   Przejdź do  
  
-   Dodawanie Using  
  
 Ponadto pamięci podręcznych używane dla operacji wewnętrznych programu Visual Studio również zostaną wyłączone.  
  
> [!NOTE]
>  Ostrzeżenie zawieszenia funkcji automatycznego miejsce tylko raz na podstawie na rozwiązanie, a nie na podstawie sesji. Oznacza to, że jeśli przełącznika z języka Visual Basic, Visual C# (lub odwrotnie) i uruchom na inny stan braku pamięci, prawdopodobnie Ci innego ostrzeżenie zawieszenia funkcji automatycznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Włączanie i wyłączanie Pełna analiza rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)   
 [Podstawy dotyczące wyrzucania elementów bezużytecznych](/dotnet/standard/garbage-collection/fundamentals)   
 [Zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)