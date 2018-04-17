---
title: 'CA1802: Używaj literałów w odpowiednich przypadkach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8bd2d28b7bc43c1bfa6ce941d7601b956d8f487
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Używaj literałów wszędzie, gdzie jest to odpowiednie
|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Pole jest zadeklarowany jako `static` i `readonly` (`Shared` i `ReadOnly` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) i został zainicjowany z wartością, która jest obliczanie w czasie kompilacji.  
  
## <a name="rule-description"></a>Opis reguły  
 Wartość `static``readonly` pola jest obliczane w czasie wykonywania wywołanego statycznego konstruktora dla typu deklarującego. Jeśli `static``readonly` pole jest inicjowana, gdy jest on zadeklarowany jako i Konstruktor statyczny nie jest zadeklarowany jako jawnie, kompilator emituje Konstruktor statyczny zainicjować pole.  
  
 Wartość `const` pola jest obliczane w czasie kompilacji i przechowywane w metadanych, co zwiększa wydajność środowiska uruchomieniowego w porównaniu z `static``readonly` pola.  
  
 Wartość przypisana do pola docelowego jest obliczanie w czasie kompilacji, zmienić tej deklaracji `const` pola tak, aby wartość jest obliczana w czasie kompilacji zamiast w czasie wykonywania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Zastąp `static` i `readonly` Modyfikatory z `const` modyfikator.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpiecznie pominąć ostrzeżenie od tej reguły lub wyłączyć zasadę, jeśli wydajność nie ma problem.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typu `UseReadOnly`, który narusza regułę i typ, `UseConstant`, odpowiadającej reguły.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]