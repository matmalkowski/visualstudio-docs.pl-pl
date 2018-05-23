---
title: 'CA1032: Implementowanie standardowych konstruktorów wyjątków'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6cd6922cae5e2d182a279e2d1637a19f8572468
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementowanie standardowych konstruktorów wyjątków

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Rozszerza typ <xref:System.Exception?displayProperty=fullName> , ale nie zadeklarować wszystkie wymagane konstruktorów.

## <a name="rule-description"></a>Opis reguły

Typy wyjątków musi implementować następujące trzy konstruktory:

- NewException() publiczne

- NewException(string) publiczne

- publiczny NewException (ciąg, wyjątków)

Ponadto, jeśli używasz starszej wersji programu FxCop statycznej analizy kodu jako przeciwieństwie do [analizatorów FxCop na podstawie Roslyn](../code-quality/roslyn-analyzers-overview.md), brak konstruktora czwarty generuje również naruszenie:

- NewException chroniona lub prywatnej (SerializationInfo, StreamingContext)

Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. Na przykład konstruktora, który ma podpis `NewException(string, Exception)` służy do tworzenia wyjątki, które są spowodowane przez inne wyjątki. Bez tego konstruktora nie można utworzyć i throw wystąpienia niestandardowego wyjątku, który zawiera wewnętrzny wyjątek (zagnieżdżonych), czyli w takiej sytuacji należy wykonać, jakie kodu zarządzanego.

Pierwszy konstruktorów wyjątków trzy są publicznie udostępniane przez Konwencję. Konstruktor czwarty jest chroniona w niezapieczętowanych klas i prywatny w klasie zapieczętowanej. Aby uzyskać więcej informacji, zobacz [CA2229: zaimplementować konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń

Aby naprawić naruszenie tej reguły, Dodaj brakujące konstruktory wyjątek i upewnij się, że poprawne ułatwień dostępu.

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy naruszenie jest spowodowany przy użyciu poziomu dostępu różnych dla konstruktorów publicznych. Ponadto jest poprawny w celu pominięcia ostrzeżenia dla `NewException(SerializationInfo, StreamingContext)` konstruktora, jeśli tworzysz przenośnej biblioteki klas (PCL).

## <a name="example"></a>Przykład

Poniższy przykład zawiera typ wyjątku, który narusza tę regułę i typ wyjątku, który jest poprawnie zaimplementowana.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Zobacz także

[CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)