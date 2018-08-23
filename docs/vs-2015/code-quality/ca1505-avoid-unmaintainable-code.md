---
title: 'CA1505: Unikaj kodu trudnego w utrzymaniu | Dokumentacja firmy Microsoft'
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
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 158b833acc2405335ba76f29163837925bd25ebc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684076"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Unikaj kodu niemożliwego w utrzymaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1505: Unikaj kodu trudnego w utrzymaniu](https://docs.microsoft.com/visualstudio/code-quality/ca1505-avoid-unmaintainable-code).  
  
Element TypeName | AvoidUnmantainableCode |  
| CheckId | CA1505 |  
| Kategoria | Microsoft.Maintainability|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Typ lub metoda ma niską wartość indeksu konserwacji.  
  
## <a name="rule-description"></a>Opis reguły  
 Indeks łatwości utrzymania jest obliczana przy użyciu następujących metryk: wiersze kodu, program woluminu i złożoność cykliczną. Program wolumin jest miarą trudności wiedzę na temat typu lub metody, która opiera się na liczbie operatorów i argumentów operacji w kodzie. Złożoność Cyklomatyczna jest miarą strukturalnych złożoność tego typu lub metody. Dowiedz się więcej na temat metryk kodu [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i jest dobrym kandydatem do przeprojektowania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać problem to naruszenie, zmodyfikowanie typu lub metody i spróbuj podzielić ją na mniejsze i bardziej ukierunkowaną typów ani metod.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Wyklucz to ostrzeżenie, gdy typ lub metoda jest nadal uważana za łatwego w utrzymaniu, niezależnie od jego duży rozmiar lub typie lub metodzie nie można podzielić.  
  
## <a name="see-also"></a>Zobacz też  
 [Utrzymanie — ostrzeżenia](../code-quality/maintainability-warnings.md)   
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



