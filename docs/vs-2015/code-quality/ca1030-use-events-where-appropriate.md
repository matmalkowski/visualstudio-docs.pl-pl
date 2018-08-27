---
title: 'CA1030: Używaj zdarzeń, gdzie jest to odpowiednie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8100aff6c2215d9a5fa031d69fc0ee105e440e3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902915"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Używaj zdarzeń wszędzie, gdzie jest to odpowiednie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1030: Używaj zdarzeń, gdzie jest to odpowiednie](https://docs.microsoft.com/visualstudio/code-quality/ca1030-use-events-where-appropriate).

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Nazwy metody publiczne, protected lub private rozpoczyna się od jednego z następujących czynności:

-   Dodatek

-   RemoveOn

-   Ogień

-   Zgłoś

## <a name="rule-description"></a>Opis reguły
 Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Zdarzenia wykonaj wzorzec projektowy obserwatora lub publikowania i subskrybowania; są one używane podczas zmiany stanu, w jeden obiekt musi zostać przekazany innych obiektów. Jeśli metoda jest wywoływana w odpowiedzi na jasno określoną zmianę stanu, metoda powinna być wywoływany przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę.

 Typowe przykłady zdarzeń znajdują się w aplikacji interfejsu użytkownika, gdy akcja użytkownika, takie jak kliknięcie przycisku powoduje, że segment kodu do wykonania. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Modelu zdarzeń nie jest ograniczona do interfejsów użytkownika; powinno być używane wszędzie muszą komunikować się stan zmieni się na co najmniej jeden obiekt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli metoda jest wywoływana, gdy zmieni się stan obiektu, należy rozważyć zmianę projektu do użycia [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelu zdarzeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli metoda nie działa z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelu zdarzeń.



