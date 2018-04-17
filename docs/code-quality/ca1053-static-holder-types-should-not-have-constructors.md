---
title: 'CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0a17b60cd88170a1df2ace72b8a4ee5206fe6d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Typy obsługi statycznej nie powinny mieć konstruktorów
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ publiczny lub publiczny zagnieżdżony deklaruje tylko statyczne elementy członkowskie i ma publiczny lub chroniony konstruktor domyślny.  
  
## <a name="rule-description"></a>Opis reguły  
 Konstruktor jest zbędny, ponieważ wywołanie statycznego elementu członkowskiego nie wymaga wystąpienia tego typu. Ponadto ponieważ typ nie ma elementów członkowskich niestatyczna, tworzenia wystąpienia nie zapewnia dostępu do żadnego z elementów członkowskich typu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Usuń domyślnego konstruktora lub przekształcenie jej w prywatną.  
  
> [!NOTE]
>  Jeśli typ nie definiuje żadnych konstruktorów niektóre kompilatory automatyczne tworzenie publicznego konstruktora domyślnego. Jeśli jest to w przypadku danego typu, Dodaj konstruktora domyślnego prywatne, aby wyeliminować naruszenie.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Obecność konstruktora sugeruje, że typ nie jest typem statycznych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza tę regułę. Zwróć uwagę, że nie jest Brak domyślnego konstruktora kodu źródłowego. Podczas tego kodu jest kompilowany do zestawu, kompilator języka C# zostanie wstawiona domyślnego konstruktora, który będzie naruszają tę regułę. Aby rozwiązać ten problem, należy zadeklarować Konstruktor prywatny.  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]