---
title: "CA1823: Unikaj nieużywanych pól prywatnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f4be67d74c3b0b01092d43d70c3c37a776def14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Unikaj nieużywanych pól prywatnych
|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Ta reguła jest zgłaszany, gdy pole prywatne w kodzie istnieje, ale nie jest używany przez wszystkie ścieżki kodu.  
  
## <a name="rule-description"></a>Opis reguły  
 Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń to pole lub Dodaj kod, który korzysta z niego.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1812: Unikaj wewnętrznych klas bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)