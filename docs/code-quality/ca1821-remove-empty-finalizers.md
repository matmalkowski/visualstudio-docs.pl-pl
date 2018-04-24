---
title: 'CA1821: Usuń puste finalizatory'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccd6ca16dc8a4ca2ce2f2883958ed82fa1c4b3ba
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Usuń puste finalizatory
|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ implementuje finalizator, który jest pusty, wymaga tylko finalizator typu podstawowego lub wywołuje tylko warunkowo emitowane metody.

## <a name="rule-description"></a>Opis reguły
 Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Moduł zbierający elementy bezużyteczne uruchomi finalizatora przed zbiera obiektu. Oznacza to, że dwie kolekcje będzie wymagany do zbierania obiektu. Pusty finalizator wiąże się to dodany narzut bez żadnych korzyści.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Usuń finalizator puste. Jeśli finalizator jest wymagana do debugowania, ujmij całą finalizator w `#if DEBUG / #endif` dyrektywy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj wiadomości z tej reguły. Nie można wstrzymać finalizację spadku wydajności i zapewnia nie korzyści.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono pusty finalizator, który powinien zostać usunięty, finalizatora, który powinien być ujęty w `#if DEBUG / #endif` dyrektywy i finalizatora, który używa `#if DEBUG / #endif` dyrektywy poprawnie.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]