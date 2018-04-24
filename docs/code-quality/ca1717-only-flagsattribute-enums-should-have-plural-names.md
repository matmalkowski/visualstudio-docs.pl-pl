---
title: 'CA1717: Tylko typy wyliczeniowe FlagsAttribute powinny mieć nazwy w liczbie mnogiej'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eddcdd47a79b925bf6601c25cf1343eacfa60aa0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Tylko typy wyliczeniowe FlagsAttribute powinny mieć nazwy w liczbie mnogiej
|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa wyliczenia widoczne na zewnątrz kończy w liczbie mnogiej programu word i wyliczenia nie jest oznaczony atrybutem <xref:System.FlagsAttribute?displayProperty=fullName> atrybutu.

## <a name="rule-description"></a>Opis reguły
 Konwencje nazewnictwa określają, że nazwę w liczbie mnogiej wyliczania wskazuje jednocześnie określono więcej niż jedną wartość wyliczenia. <xref:System.FlagsAttribute> Kompilatory informuje, że wyliczenia powinny być traktowane jako pole bitowe umożliwiającą Operacje bitowe wyliczenie.

 Jeśli tylko jedna z wartości wyliczenia można określić jednocześnie, nazwa wyliczenia powinna być pojedynczej programu word. Na przykład wyliczenie definiuje dni tygodnia może być przeznaczona do użycia w aplikacji, której można określić wiele dni. To wyliczenie ma <xref:System.FlagsAttribute> i można go wywołać "Dni". Wyliczenie podobne, która umożliwia określenie tylko jednego dnia nie może mieć atrybut — można wywołać "Dzień".

 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Powoduje to skrócenie czasu, jest wymagany, aby dowiedzieć się więcej nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wprowadź nazwę wyliczenia pojedynczej programu word lub Dodaj <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie z tej reguły, jeśli nazwa kończy się w pojedynczej programu word.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1714: Wyliczenia flag powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.FlagsAttribute?displayProperty=fullName> [Projekt wyliczenia](/dotnet/standard/design-guidelines/enum)