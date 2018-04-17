---
title: 'CA2214: Nie należy wywoływać nadpisywalnych metod w konstruktorach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c9df9acf8c04e85b16c1f3b5d964938a21f168b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nie należy wywoływać nadpisywalnych metod w konstruktorach
|||  
|-|-|  
|TypeName|DoNotCallOverridableMethodsInConstructors|  
|CheckId|CA2214|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Konstruktor typu niezapieczętowany wywołuje metody wirtualnej zdefiniowanej w klasie.  
  
## <a name="rule-description"></a>Opis reguły  
 Gdy wywoływana jest metoda wirtualna, rzeczywisty typ, który wykonuje metodę nie jest zaznaczone do czasu wykonywania. Konstruktor wywołuje metody wirtualnej, jest to możliwe, że Konstruktor wywołuje metodę wystąpienie nie zostało wykonane.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, nie należy wywoływać metody wirtualne typu z konstruktorów typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Konstruktor powinien przeprojektowany tak, aby wyeliminować wywołanie metody wirtualnej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje efekt naruszenie tej reguły. Aplikacja testowa tworzy wystąpienie `DerivedType`, co powoduje, że jej klasa podstawowa (`BadlyConstructedType`) konstruktora do wykonania. `BadlyConstructedType`firmy Konstruktor niepoprawnie wywołuje metodę wirtualną `DoSomething`. Jak pokazano na dane wyjściowe, `DerivedType.DoSomething()` wykonuje i jest więc przed `DerivedType`tego konstruktora.  
  
 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Wywoływanie podstawowej ctor.**  
**Pochodne DoSomething jest nazywany — zainicjować? Brak**  
**Wywołania pochodzące ctor.**