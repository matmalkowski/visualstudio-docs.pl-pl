---
title: Automatyczne wstrzymanie funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 281a4cbfb7bb1564af698cf4e745d56207f3e58e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42686787"
---
# <a name="automatic-feature-suspension"></a>Automatyczne wstrzymanie funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [automatyczne wstrzymanie funkcji](https://docs.microsoft.com/visualstudio/code-quality/automatic-feature-suspension).

Jeśli Twoje dostępnej pamięci systemowej kwalifikuje się do 200MB lub mniej, Visual Studio wyświetla następujący komunikat w edytorze kodu.

 ![Tekst alertu zawieszanie pełnej analizy rozwiązania](../code-quality/media/fsa-alert.png "FSA_Alert")

 Gdy program Visual Studio wykryje stan braku pamięci, automatycznie wstrzymuje niektórych zaawansowanych funkcji, aby ułatwić sobie trwały. Gdy ten zaawansowany pojawi się ostrzeżenie dotyczące zawieszenia funkcji, Visual Studio będą nadal działać tak jak poprzednio, ale jego wydajność, spowoduje to pogorszenie nieco.

 W stan braku pamięci mają miejsce następujące zdarzenia:

-   Pełnej analizy rozwiązania dla programu Visual C# i Visual Basic jest wyłączona.

-   [Wyrzucanie elementów bezużytecznych](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) trybu o małych opóźnieniach (GC) dla języka Visual C# i Visual Basic są wyłączone.

-   Visual Studio pamięci podręczne są opróżniane.

## <a name="improve-visual-studio-performance"></a>Poprawa wydajności programu Visual Studio
 Aby uzyskać porady i wskazówki na temat sposobu poprawy wydajności programu Visual Studio podczas zajmowania się warunki małej ilości pamięci lub dużych rozwiązań, zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Pełnej analizy rozwiązania zawieszone
 Domyślnie pełnej analizy rozwiązania jest włączona dla języka Visual Basic i wyłączone dla języka Visual C#. Jednak w stan braku pamięci pełnej analizy rozwiązania jest automatycznie wyłączana dla języka Visual Basic i Visual C#, niezależnie od ich ustawień w oknie dialogowym Opcje. Jednakże, można ponownie włączyć pełnej analizy rozwiązania, wybierając **ponownie włączyć** informacje paska, gdy pojawia się, wybierając przycisk **Włączanie pełnej analizy rozwiązania** pole wyboru w oknie dialogowym Opcje, lub ponowne uruchomienie programu Visual Studio. Okno dialogowe Opcje zawsze wyświetla bieżące rozwiązanie pełną ustawień analizy. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC o małych opóźnieniach wyłączone
 Aby ponownie włączyć tryb o małych opóźnieniach GC, uruchom ponownie program Visual Studio.  Domyślnie program Visual Studio Włącza tryb o małych opóźnieniach GC, zawsze wtedy, gdy są wpisywanie, aby upewnić się, że wpisany tekst nie blokuje żadnych operacji GC. Jednak jeśli stan braku pamięci powoduje, że Visual Studio, aby wyświetlić ostrzeżenie automatyczne zawieszenie, GC o małych opóźnieniach tryb zostanie wyłączony dla tej sesji. Ponowne uruchomienie programu Visual Studio ponownie włączyć domyślne zachowanie GC. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio pamięci podręcznych opróżnione

Wszystkie bufory programu Visual Studio są natychmiast opróżnienia, ale rozpocznie się ponownie wypełnić, jeśli nadal bieżącej sesji rozwoju lub uruchom ponownie program Visual Studio. Pamięci podręczne opróżnionych obejmują pamięci podręczne dla następujących funkcji.

-   Znajdź wszystkie odwołania

-   Przejdź do

-   Dodaj instrukcję Using

Ponadto używane dla operacji programu Visual Studio wewnętrznych pamięci podręcznych również zostaną wyczyszczone.

> [!NOTE]
> Ostrzeżenie dotyczące zawieszenia funkcji automatycznego pojawia się tylko raz na podstawie danego rozwiązania, a nie na podstawie sesji. Oznacza to, że jeśli przełączyć się z języka Visual Basic do Visual C# (lub odwrotnie) i w inny stan braku pamięci, prawdopodobnie uzyskasz innej ostrzeżenie dotyczące zawieszenia funkcji automatycznego.

## <a name="see-also"></a>Zobacz także

- [Porady: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Podstawy dotyczące odzyskiwania pamięci](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)