---
title: "CA1307: Określ StringComparison | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7087cfe23f7911ec33891a70cd88cf47ee9e4a7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Określ StringComparison
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Kategoria|Microsoft.Globalization|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Operacja porównywania ciągów używa przeciążenie metody, która nie określa <xref:System.StringComparison> parametru.  
  
## <a name="rule-description"></a>Opis reguły  
 Ciąg wielu operacji najważniejszych <xref:System.String.Compare%2A> i <xref:System.String.Equals%2A> metod, Udostępnij przeciążenie akceptującego <xref:System.StringComparison> wartość wyliczenia jako parametr.  
  
 Zawsze, gdy istnieje tego przyjmuje <xref:System.StringComparison> parametru powinna być używana zamiast funkcji przeciążenia, które nie wymaga tego parametru. Przez jawne ustawienie tego parametru, kod jest często doprecyzowania dokonane i łatwiejsze w obsłudze.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, należy zmienić metod porównania ciągów do przeciążenia, które akceptują <xref:System.StringComparison> wyliczenie jako parametr. Na przykład: Zmień `String.Compare(str1, str2)` do `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy biblioteki lub aplikacja jest przeznaczona dla ograniczonej użytkowników lokalnych i w związku z tym nie będzie lokalizowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia globalizacji](../code-quality/globalization-warnings.md)   
 [CA1309: Używaj wyliczenia StringComparison stosującego reguły sortowania oparte na wartości](../code-quality/ca1309-use-ordinal-stringcomparison.md)