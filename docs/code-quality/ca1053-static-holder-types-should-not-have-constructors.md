---
title: "CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d482c715e3f93df5fb26f0c88c6b0665b3dee506
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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