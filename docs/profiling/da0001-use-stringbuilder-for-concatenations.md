---
title: 'DA0001: Używaj StringBuilder do konkatenacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 601bb8145ad2e8467e078a3aee95a243236e5433
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Używaj StringBuilder do łączenia
|||  
|-|-|  
|Identyfikator reguły|DA0001|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Pobierania próbek<br /><br /> Oprzyrządowanie|  
|Komunikat|Należy rozważyć użycie StringBuilder do konkatenacji ciągów|  
|Typ komunikatu|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania System.String.Concat są znaczna część danych profilowania. Należy rozważyć użycie <xref:System.Text.StringBuilder> klasy w celu tworzenia ciągów z wieloma segmentami.  
  
## <a name="rule-description"></a>Opis reguły  
 A <xref:System.String> obiektu nie można modyfikować. W związku z tym wszelkie modyfikacje ciąg tworzy nowy obiekt ciągu i wyrzucanie elementów bezużytecznych oryginału. To zachowanie jest takie samo jawnie wywołać String.concat — lub użyj takiego jak ciąg operatory łączenia + lub +=... Może spowodować spadek wydajności programu, jeśli te metody są często nazywane, takich jak dodania znaków do ciągu w ścisłej pętli.  
  
 Klasy StringBuilder jest obiektem modyfikowalne i, w odróżnieniu od typu System.String, większość metod na StringBuilder, które modyfikują wystąpienia tej klasy zwraca odwołanie do tego samego wystąpienia. Można wstawić znaki lub dołączać tekstu do wystąpienia klasy StringBuilder i usuń lub zastąp znaki w wystąpieniu bez konieczności podziału nowe wystąpienie i usunięcie oryginalnego wystąpienia.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) pobierania próbek danych profilu. Znajdź sekcje programu, które wykorzystują najczęstsze ciągów. Użyj klasy StringBuilder do złożonych na ciągach, w tym operacje na ciągach częste łączenia.  
  
 Aby uzyskać więcej informacji na temat pracy z ciągami [operacje na ciągach](http://go.microsoft.com/fwlink/?LinkId=177816) sekcji [rozdział 5 - poprawę wydajności kodu zarządzanego](http://go.microsoft.com/fwlink/?LinkId=177817) w bibliotece Microsoft Patterns and Practices.