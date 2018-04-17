---
title: Zawieszenia funkcji automatycznego w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: bf11b7d0723f3ecabf9fc794fb244f48daa95672
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="automatic-feature-suspension"></a>Funkcja automatycznej zawieszenia

Jeśli pamięci dostępnej w systemie znajduje się 200 MB lub mniej, Visual Studio wyświetli następujący komunikat w edytorze kodu:

![Tekst alertu wstrzymywania Pełna analiza rozwiązania](../code-quality/media/fsa_alert.png)

Visual Studio, wykrycie braku pamięci, automatycznie wstrzymuje niektórych zaawansowanych funkcji, aby ułatwić trwały. Visual Studio w dalszym ciągu działać tak jak poprzednio, ale jego wydajność jest ograniczone.

Stan braku pamięci następujące akcje miejsce:

- Pełna analiza rozwiązania dla programu Visual C# i Visual Basic jest wyłączona.

- [Wyrzucanie elementów bezużytecznych](/dotnet/standard/garbage-collection/index) tryb małych opóźnieniach (GC) dla programu Visual C# i Visual Basic jest wyłączona.

- Visual Studio pamięci podręcznych są opróżniane.

## <a name="improve-visual-studio-performance"></a>Poprawianie wydajności programu Visual Studio

Aby uzyskać porady i wskazówki na temat sposobów usprawnienia wydajności programu Visual Studio podczas pracy z rozwiązaniami dużych i ilość pamięci jest mała, zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Pełna analiza rozwiązania zawieszone

Domyślnie Pełna analiza rozwiązania jest włączona dla programu Visual Basic i wyłączone Visual C#. Jednak w stanie małej ilości pamięci, pełną analizę rozwiązania jest automatycznie wyłączana dla języka Visual Basic i Visual C#, niezależnie od ich ustawień w oknie dialogowym Opcje. Jednak można ponownie włączyć pełną analizę rozwiązania, wybierając **ponownie włączyć** przycisk informacji pasek po jego wyświetleniu wybierając **Włącz pełną analizę rozwiązania** pole wyboru w oknie dialogowym Opcje lub przez ponowne uruchomienie programu Visual Studio. Opcje — okno dialogowe zawsze zawiera bieżące rozwiązanie pełne ustawienia analizy. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Wykaz Globalny małych opóźnieniach wyłączone

Aby ponownie włączyć tryb małych opóźnieniach GC, uruchom ponownie program Visual Studio. Domyślnie program Visual Studio pozwala tryb małych opóźnieniach GC miarę wpisywania, aby upewnić się, że wpisane hasło nie blokują żadnych operacji GC. Jednak jeśli niedobór pamięci powoduje, że Visual Studio, aby wyświetlić ostrzeżenie automatyczne zawieszenie, tryb małych opóźnieniach GC jest wyłączone dla tej sesji. Ponownie uruchomić ponownie program Visual Studio umożliwia domyślne zachowanie GC. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio pamięci podręcznych opróżniany

Jeśli kontynuować bieżącej sesji rozwoju lub uruchom ponownie program Visual Studio, wszystkich usług pamięć podręczna programu Visual Studio natychmiast zostały opróżnione, ale rozpocząć ponownie wypełnić. Pamięci podręczne opróżnionych obejmują pamięci podręcznych następujące funkcje:

- Znajdź wszystkie odwołania

- Przejdź do

- Dodawanie Using

Ponadto pamięci podręcznych używane dla operacji wewnętrznych programu Visual Studio również zostaną wyłączone.

> [!NOTE]
> Ostrzeżenie zawieszenia funkcji automatycznego miejsce tylko raz na podstawie na rozwiązanie, a nie na podstawie sesji. Oznacza to, że jeśli przełącznika z języka Visual Basic, Visual C# (lub odwrotnie) i uruchom na inny stan braku pamięci, prawdopodobnie Ci innego ostrzeżenie zawieszenia funkcji automatycznego.

## <a name="see-also"></a>Zobacz także

- [Porady: Włączanie i wyłączanie Pełna analiza rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Podstawy dotyczące odzyskiwania pamięci](/dotnet/standard/garbage-collection/fundamentals)
- [Zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)