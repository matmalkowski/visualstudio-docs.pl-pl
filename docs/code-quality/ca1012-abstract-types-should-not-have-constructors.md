---
title: "CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords: CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 394621874110ccae04837a991e66e2773700c33f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów
|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Publiczny typ jest abstrakcyjny i ma konstruktora publicznego.  
  
## <a name="rule-description"></a>Opis reguły  
 Konstruktory dla typów abstrakcyjnych mogą być wywoływane tylko przez typy pochodne. Ze względu na to, że publiczne konstruktory tworzą wystąpienia typu, a nie można utworzyć wystąpienia typu abstrakcyjnego, publiczny konstruktor typu abstrakcyjnego został niepoprawnie zaprojektowany.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, ustalić Konstruktor chroniony lub nie deklaruj typu jako abstrakcyjny.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Typ abstrakcyjny ma on publicznego konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład zawierający typ ogólny, który narusza tę regułę.  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład poprawki naruszenie poprzedniej poprzez zmianę dostępności konstruktora z `public` do `protected`.  
  
 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]