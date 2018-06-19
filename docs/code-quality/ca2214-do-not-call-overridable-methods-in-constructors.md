---
title: 'CA2214: Nie należy wywoływać nadpisywalnych metod w konstruktorach'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: b5ebcd4164f9db28d4cb1f150ee3a4bb21b21cde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920114"
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

 **Wywoływanie podstawowej ctor. ** 
 **Pochodnych DoSomething jest nazywany - zainicjować? Nie**
**telefonicznej pochodnych ctor.**