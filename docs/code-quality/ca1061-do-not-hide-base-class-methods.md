---
title: 'CA1061: Nie należy ukrywać metod klasy bazowej'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fc3be40a81d29da27e9a44d72cca4e78b37abbf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Nie należy ukrywać metod klasy bazowej
|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ pochodny deklaruje metody o tej samej nazwie i z taką samą liczbę parametrów jako jeden z jego metod bazowych; co najmniej jeden z parametrów jest podstawowym typem odpowiadającym mu parametrem w metodzie podstawowej; a wszystkie pozostałe parametry mają typy, które są takie same jak wartości odpowiadających im parametrów w metodzie podstawowej.

## <a name="rule-description"></a>Opis reguły
 Metody w typie podstawowym jest ukryty przez metodę o identycznej nazwie w typie pochodnym, gdy parametr podpis Metoda pochodna różni się tylko typy, które są bardziej słabo pochodzące od odpowiednich typów w podpisie parametru metody podstawowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, usuń lub zmień jego nazwę metody, zmienianie podpisu parametr tak, że metoda ukrywa metodę podstawową.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę, która narusza zasady.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]