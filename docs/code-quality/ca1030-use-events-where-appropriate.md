---
title: "CA1030: Używaj zdarzeń wszędzie, gdzie jest to odpowiednie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c07aac3780abc10dd3995b21b5c9636607166f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Używaj zdarzeń wszędzie, gdzie jest to odpowiednie
|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa metody publicznych, chronionych lub prywatnych rozpoczyna się od jednego z następujących:  
  
-   Dodatek  
  
-   RemoveOn  
  
-   Fire  
  
-   Zgłoś  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Wzorzec projektowy obserwatora lub publikowania / subskrypcji; wykonaj zdarzenia są one używane podczas zmiany stanu w jeden obiekt musi zostać przekazany inne obiekty. Jeśli metoda jest wywoływana w odpowiedzi na zmianę stanu jasno określone, metoda powinna być wywoływana przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę.  
  
 Typowe przykłady zdarzeń znajdują się w aplikacji interfejsu użytkownika, gdy akcja użytkownika, takie jak kliknięcie przycisku powoduje segment kodu do wykonania. [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Model zdarzeń nie jest ograniczona do interfejsów użytkownika; należy używać, gdziekolwiek muszą komunikować się stan zmieni się na co najmniej jeden obiekt.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Jeśli metoda jest wywoływana po zmianie stanu obiektu, należy rozważyć zmianę projektu do użycia [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modelu zdarzeń.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej reguły, jeśli metoda nie działa z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] model zdarzeń.