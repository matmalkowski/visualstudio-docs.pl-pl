---
title: 'CA1047: Nie deklaruj chronionych elementów członkowskich w typach zapieczętowanych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b4a8ec92b79fb7df72ebd1984fc49f3cf4396cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Nie deklaruj chronionych elementów członkowskich w typach zapieczętowanych
|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Jest typem publicznym `sealed` (`NotInheritable` w języku Visual basic) ale deklaruje chronionego elementu członkowskiego lub typu zagnieżdżonego chronionych. Ta zasada nie raportuje naruszenia <xref:System.Object.Finalize%2A> metody, które należy wykonać tego wzorca.  
  
## <a name="rule-description"></a>Opis reguły  
 Chronione elementy członkowskie są zadeklarowane w typach tak, aby typy dziedziczące miały dostęp do elementu członkowskiego i mogły go zastąpić. Zgodnie z definicją nie może dziedziczyć z zapieczętowanego typu, co oznacza, że chroniony metod w typach zapieczętowanych nie można wywołać.  
  
 Kompilator języka C# generuje ostrzeżenie o tym błędzie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, zmień poziom dostępu do elementu członkowskiego jako private, lub typ dziedziczonych.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie typ w jego bieżącym stanie może spowodować problemy dotyczące konserwacji i nie daje żadnych korzyści.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza tę regułę.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]