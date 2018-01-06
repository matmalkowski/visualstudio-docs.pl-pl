---
title: 'CA1505: Unikaj kodu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5abaaba67d3390e36c4ad792d7b95bf41be80c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Unikaj kodu niemożliwego w utrzymaniu
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|Kategoria|Microsoft.Maintainability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ lub metoda ma niską wartość indeksu konserwacji.  
  
## <a name="rule-description"></a>Opis reguły  
 Indeks łatwości utrzymania jest obliczana przy użyciu następujących metryk: wierszy kodu, program woluminu i złożoność cyklomatyczną. Program wolumin jest miarą trudności zrozumienia typu lub metody, która jest oparta na liczbie operatory i argumenty w kodzie. Złożoność Cyklomatyczną jest miarą strukturalnych złożoność typu lub metody. Dowiedz się więcej o metryk kodu [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Indeks łatwości utrzymania niski wskazuje, że typ lub metoda jest prawdopodobnie trudne w utrzymaniu i będzie odpowiednimi kandydatami do.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić to naruszenie, zmodyfikowanie typu lub metody i spróbuj podzielić go na mniejsze i bardziej ukierunkowaną typach lub metodach.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Wyklucz to ostrzeżenie, gdy typ lub metoda jest nadal łatwy w obsłudze, niezależnie od jego duży rozmiar lub typ lub metoda nie może zostać podzielony.  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia dotyczące utrzymania](../code-quality/maintainability-warnings.md)   
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)