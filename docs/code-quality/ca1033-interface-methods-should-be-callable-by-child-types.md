---
title: 'CA1033: Typy potomne powinny móc wywoływać metody interfejsu'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c41b19d9d4a82e25223a9cf7b04034b37c3f45fb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Typy potomne powinny móc wywoływać metody interfejsu
|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie.

## <a name="rule-description"></a>Opis reguły
 Należy wziąć pod uwagę typu podstawowego, który implementuje jawnie metody interfejsu publicznego. Typ, który pochodzi od typu podstawowego mają dostęp do metody interfejsu dziedziczone tylko przez odwołanie do bieżącego wystąpienia (`this` w języku C#) który jest rzutowane na interfejs. Jeśli typ pochodny implementuje (jawnie) ponownie metodę dziedziczony interfejs, Podstawowa implementacja nie są dostępne. Wywołanie przez odwołanie do bieżącego wystąpienia wywoła pochodnej implementacji; Powoduje to rekursji i przepełnienie stosu ostatecznego.

 Ta zasada zgłasza naruszenie dla jawnej implementacji <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> podczas widoczne na zewnątrz `Close()` lub `System.IDisposable.Dispose(Boolean)` jest dostępne metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj nową metodę, która udostępnia te same funkcje i jest widoczna dla typów pochodnych, lub zmień niejawne implementacji. Jeśli na istotne zmiany jest dopuszczalna, alternatywą jest typ zapieczętowany.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli jest widocznej zewnętrznie metodzie, pod warunkiem, która ma te same funkcje, ale inną nazwę niż jawnie implementowana metoda.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu `ViolatingBase`, który narusza regułę i typ, `FixedBase`, który pokazuje poprawkę dotyczącą naruszenie.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Zobacz też
 [Interfejsy](/dotnet/csharp/programming-guide/interfaces/index)