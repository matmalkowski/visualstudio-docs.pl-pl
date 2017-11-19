---
title: "Porady: Wymuszanie kodu za pomocą zasad analizy kodu zaewidencjonowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d9697c7d6a216c08e34eb19287d22a76d67a55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Porady: wymuszanie kodu za pomocą zasad ewidencjonowania analizy kodu
Deweloperzy mogą używać narzędzia metryki kodu do mierzenia stopnia złożoności i łatwości konserwacji ich kodu, ale nie można ich wywołać metryki kodu jako część zasad ewidencjonowania. Jednakże zespołu można włączyć reguły analizy kodu Sprawdź zgodność ich kodu ze standardami metryki kodu i wymuszania reguł za pomocą zasad ewidencjonowania. Aby uzyskać więcej informacji na temat metryki kodu, zobacz [wartości metryk kodów](../code-quality/code-metrics-values.md).  
  
 Deweloperzy można włączyć głębokość dziedziczenia, klasa sprzężenia, indeks łatwości utrzymania i złożoności wymuszanie kodu za za pomocą zasad ewidencjonowania analizy kodu. Wszystkie cztery te zasady znajdują się w kategorii "Utrzymanie reguły" w edytorze zasad analizy kodu.  
  
 Administratorzy wersji kontrolować dla [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] można dodawać reguł utrzymanie analizy kodu do wymagań zasad ewidencjonowania. Te zaewidencjonowania zasady wymagają deweloperom przeprowadzanie analizy kodu, w oparciu o zmiany te reguły przed zainicjowaniem ewidencjonowania.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Aby otworzyć Edytor zasad analizy kodu  
  
1.  W **Team Explorer**, kliknij prawym przyciskiem myszy projektu zespołowego, kliknij przycisk **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.  
  
     **Kontroli źródła** zostanie wyświetlone okno dialogowe.  
  
2.  Na **zasad ewidencjonowania** , a następnie kliknij pozycję **Dodaj**.  
  
     **Dodaj zasady ewidencjonowania** zostanie wyświetlone okno dialogowe.  
  
3.  W **zasad ewidencjonowania** listy, wybierz **analizy kodu** pole wyboru, a następnie kliknij przycisk **OK**.  
  
     **Edytor zasad analizy kodu** zostanie wyświetlone okno dialogowe.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Aby włączyć reguły utrzymanie analizy kodu  
  
1.  W **Edytor zasad analizy kodu** okna dialogowego, w obszarze **ustawienia reguły**, rozwiń węzeł **reguły utrzymanie** węzła.  
  
2.  Zaznacz pola wyboru dla następujących reguł:  
  
    -   Głębokość dziedziczenia: **CA1501 AvoidExcessiveInheritance** — próg: ostrzeżenie na więcej niż 5 poziomach głębokości  
  
    -   Złożoność: **CA1502 AvoidExcessiveComplexity** — próg: ostrzeżenie w więcej niż 25  
  
    -   Indeks łatwości utrzymania: **CA1505 AvoidUnmaintainableCode** — próg: ostrzeżenie na mniej niż 20  
  
    -   Sprzężenia klas: **CA1506 AvoidExcessiveClassCoupling** — próg: ostrzeżenie w więcej niż 80 dla klasy i ponad 30 metody  
  
    -   Ponadto naruszenie reguły, aby zapobiec kompilacji, wybierz **traktuje ostrzeżenie jako błąd** pole wyboru obok opis reguły.  
  
3.  Kliknij przycisk **OK**. Nowe zasady ewidencjonowania dotyczy teraz przyszłych zaewidencjonowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wartości metryk kodów](../code-quality/code-metrics-values.md)   
 [Tworzenie i używanie zasad ewidencjonowania analizy kodu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)