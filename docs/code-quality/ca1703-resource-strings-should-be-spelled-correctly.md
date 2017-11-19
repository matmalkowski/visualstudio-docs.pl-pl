---
title: "CA1703: Ciągów zasobów powinna być poprawna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c7828aa218933208408a285510e998921d6f032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ciągu zasobu należy zapisywać poprawnie
|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada analizowania ciągu zasobu w wyrazy (tokenizację wyrazy złożone) i sprawdzając pisownię każdego wyrazu/tokenu. Uzyskać informacji o algorytmie analizy, zobacz [CA1704: identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Domyślnie używana wersja angielski (en) przez moduł sprawdzania pisowni.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, użyj pełnej słowa, które jest poprawna lub dodać wyraz do słownika. Aby uzyskać informacje o sposobie używania niestandardowych słowników, zobacz [CA1704: identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie zapisanych słowa skrócić czas, który jest wymagany, aby dowiedzieć się nowe biblioteki oprogramowania.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704: Identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: Literały powinny być napisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)