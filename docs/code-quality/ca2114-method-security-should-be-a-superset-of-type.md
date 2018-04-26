---
title: 'CA2114: Metody zabezpieczeń powinny być nadzbiorem typu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d2fc6fb60dd837dd93de1db2758ee0e2c216850
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Metody zabezpieczeń powinny być nadzbiorem typu
|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Zabezpieczenia deklaracyjne ma typ ma jeden z jego metody zabezpieczenia deklaratywne dla tego samego działania zabezpieczeń i akcji zabezpieczeń nie jest [Linkdemand](/dotnet/framework/misc/link-demands), i sprawdzana przez typ uprawnienia nie są podzbiorem uprawnienia sprawdzony przez metodę.

## <a name="rule-description"></a>Opis reguły
 Metoda nie powinna mieć zarówno metoda poziomie typu i zabezpieczenia deklaratywne dla tego samego działania. Sprawdza dwie nie są połączone; dotyczy tylko żądanie na poziomie metody. Na przykład, jeśli typem wymaga uprawnień `X`, i jedną z metod wymaga uprawnień `Y`, kod nie musi mieć uprawnienie `X` można wykonać metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Sprawdź swój kod, aby upewnić się, że obie akcje są wymagane. Jeśli wymagane są obie akcje, upewnij się, że poziom metody akcji zawiera zabezpieczeń ustawionych na poziomie typu. Na przykład, jeśli z danym typem wymaga uprawnień `X`, a jej metodę musi również zażądać uprawnień `Y`, metoda jawnie należy zażądać `X` i `Y`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli metoda nie wymaga zabezpieczeń określone przez typ. Jednak to nie jest scenariusz zwykłej i może wskazywać na potrzebę przeglądu zachować ostrożność podczas projektowania.

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto uprawnienia środowiska, aby zademonstrować zagrożenia naruszenie tej reguły. W tym przykładzie kodu aplikacji tworzy wystąpienia typu zabezpieczonych przed odmową uprawnień wymaganych przez ten typ. W przypadku zagrożenia rzeczywistych aplikacji wymaga innym sposobem uzyskania wystąpienia obiektu.

 W poniższym przykładzie zapotrzebowanie biblioteki uprawnienie dla typu zapisu i uprawnienia do metody odczytu.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example"></a>Przykład
 Poniższy kod aplikacji przedstawia luki w zabezpieczeniach biblioteki przez wywołanie metody, nawet jeśli nie spełnia wymagania zabezpieczeń na poziomie typu.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

 W tym przykładzie tworzy następujące dane wyjściowe.

 **[Wszystkie uprawnienia] Informacje osobiste: 6/16/1964 12:00:00 AM**
 **[nie uprawnień do zapisu (wymagany przez typ)] informacje osobiste: 6/16/1964 12:00:00 AM**
 **[do odczytu (uprawnień wymagany przez metodę)] nie może uzyskać dostępu do danych osobowych: żądanie nie powiodło się.**
## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines) [Link zapotrzebowanie](/dotnet/framework/misc/link-demands) [dane i modelowanie](/dotnet/framework/data/index)