---
title: "CA2130: Krytyczne stałe zabezpieczeń powinny być przezroczyste | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ddd6e768f0c5311d6ca8ea19f43f4155f6168b5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Krytyczne stałe zabezpieczeń powinny być przezroczyste
|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Stałe pola lub elementu członkowskiego wyliczenia jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute>.  
  
## <a name="rule-description"></a>Opis reguły  
 Wymuszanie przezroczystości nie jest wymuszane dla wartości stałych, ponieważ kompilatory wbudowują stałe wartości, tak aby nie było wymagane żadne wyszukiwanie w czasie wykonywania. Stałe pola powinny być przezroczyste dla zabezpieczeń, tak aby recenzenci kodu nie zakładali, że przezroczysty kod nie może uzyskać dostępu do stałej.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, usuń atrybut SecurityCritical z pola lub wartość.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach wartości wyliczenia `EnumWithCriticalValues.CriticalEnumValue` i stałą `CriticalConstant` Zgłoś to ostrzeżenie. Aby rozwiązać problemy, Usuń [`SecurityCritical`] dla atrybutu przezroczystego ich zabezpieczeń.  
  
 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]