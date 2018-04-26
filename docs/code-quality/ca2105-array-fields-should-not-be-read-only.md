---
title: 'CA2105: Pola tablicy nie powinny być tylko do odczytu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91a97983a8760d7f5df04fe6e5b0a56a782a11ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Pola tablicy nie powinny być tylko do odczytu
|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Pola publiczne lub chronione zawierające tablicy jest zadeklarowany jako tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 Po zastosowaniu `readonly` (`ReadOnly` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) nie można zmienić modyfikator do pola, które zawiera tablicę pole do odwoływania się do innej tablicy. Można jednak zmienić elementy tablicy, które są przechowywane w polu tylko do odczytu. Kod, który sprawia, że decyzje i wykonuje operacje, które są oparte na elementach tablicy tylko do odczytu, który jest publicznie dostępny może zawierać luki w zabezpieczeniach kończona.

 Należy pamiętać, że również posiadające pole publiczne narusza reguły projektowania [CA1051: nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić luki w zabezpieczeniach, który jest identyfikowany przez tę regułę, nie należy polegać na zawartość tablicy tylko do odczytu, który jest publicznie dostępny. Zdecydowanie zaleca się korzystanie z jednej z następujących procedur:

-   Zastąp tablicy silnie typizowaną kolekcją, nie można jej zmienić. Aby uzyskać więcej informacji, zobacz <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

-   Zastąp pole publiczne za pomocą metody, która zwróci klon tablicy prywatnej. Ponieważ kod nie korzystają z klonu, istnieje niebezpieczeństwo Jeśli elementy zostaną zmodyfikowane.

 W przypadku wybrania drugiej metody, nie zamieniaj pole z właściwością; właściwości zwracające tablice negatywnie wpłynąć na wydajność. Aby uzyskać więcej informacji, zobacz [CA1819: właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wyłączenie ostrzeżenie od tej reguły jest zalecane. Prawie nie scenariusze wystąpić, gdy zawartość pola tylko do odczytu nie są ważne. Jeśli jest to w przypadku danego scenariusza, Usuń `readonly` modyfikator zamiast z wyłączeniem wiadomości.

## <a name="example"></a>Przykład
 W tym przykładzie przedstawiono zagrożenia naruszenie tej reguły. Pierwsza część przedstawiono przykład biblioteki, która ma typ `MyClassWithReadOnlyArrayField`, która zawiera dwa pola (`grades` i `privateGrades`), które nie są bezpieczne. Pole `grades` jest publiczna i w związku z tym narażony na ataki każdego obiektu wywołującego. Pole `privateGrades` jest prywatny, ale jest nadal podatne, ponieważ jest zwracany do wywoływania przez `GetPrivateGrades` metody. `securePrivateGrades` Pole jest widoczne w bezpieczny sposób za `GetSecurePrivateGrades` metody. Jest zadeklarowany jako prywatny, aby stosować dobre projektowania rozwiązania. Druga część zawiera kod, który zmienia wartości przechowywane w `grades` i `privateGrades` elementów członkowskich.

 Biblioteka klas przykład pojawia się w następującym przykładzie.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example"></a>Przykład
 W poniższym kodzie użyto biblioteki klas przykład ilustrujący problemy z zabezpieczeniami tablicy tylko do odczytu.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

 Dane wyjściowe w tym przykładzie jest:

 **Przed naruszeniem: klas: 90, 90, 90 stopni prywatnych: 90, 90, 90 Secure klas, 90, 90, 90**
**po naruszeniu: klas: 90, 555, 90 stopni prywatnych: 90, 555, 90 Secure klas, 90, 90, 90**
## <a name="see-also"></a>Zobacz też
 <xref:System.Array?displayProperty=fullName><xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>