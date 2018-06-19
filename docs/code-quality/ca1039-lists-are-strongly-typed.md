---
title: 'CA1039: Listy są silnie typizowane'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70bc0065957321894c53726790b73b432dfdea6f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901043"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listy są silnie typizowane
|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczne lub chronione typ implementuje <xref:System.Collections.IList?displayProperty=fullName> , ale nie zapewnia silnie typizowane metody dla co najmniej jednego z następujących czynności:

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>Opis reguły
 Ta zasada wymaga <xref:System.Collections.IList> implementacje zapewnienie silnie typizowane elementy członkowskie, dzięki czemu użytkownicy nie są wymagane do rzutowania argumentów <xref:System.Object?displayProperty=fullName> wpisz przy korzystaniu z funkcji dostępnych za pośrednictwem interfejsu. <xref:System.Collections.IList> Interfejs jest implementowany przez kolekcje obiektów, które mogą być udostępniane przez indeks. Ta zasada przyjęto założenie, że typ, który zawiera <xref:System.Collections.IList> robi to zarządzanie kolekcję wystąpień typu, który jest mocniejszy niż element <xref:System.Object>.

 <xref:System.Collections.IList> implementuje <xref:System.Collections.ICollection?displayProperty=fullName> i <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejsów. W przypadku zastosowania <xref:System.Collections.IList>, musisz podać wymagane elementy jednoznacznie <xref:System.Collections.ICollection>. Jeśli rozszerzenie obiektów w kolekcji <xref:System.ValueType?displayProperty=fullName>, należy podać element jednoznacznie dla <xref:System.Collections.IEnumerable.GetEnumerator%2A> w celu uniknięcia spadek wydajności który jest spowodowany przez opakowanie; nie jest to wymagane w przypadku obiektów kolekcji typu odwołania.

 Do wykonania tej reguły, implementować członków interfejsu a jawnie przy użyciu nazw w formie InterfaceName.InterfaceMemberName, takich jak <xref:System.Collections.IList.Add%2A>. Elementy członkowskie interfejsu jawnego Użyj typów danych, które są zadeklarowane w interfejsie. Implementowanie jednoznacznie elementów przy użyciu nazwy elementu członkowskiego interfejsu, takich jak `Add`. Deklarowanie silnie typizowane elementy członkowskie jako public i deklarować parametrów i zwracają wartości były silnego typu, który jest zarządzany przez kolekcję. Silne typy Zastąp słabszych typów, takich jak <xref:System.Object> i <xref:System.Array> który został zadeklarowany w interfejsie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, jawne Implementowanie <xref:System.Collections.IList> elementy członkowskie i jednoznacznie alternatywę dla elementów członkowskich, które zostały wymienione wcześniej. Kod, który implementuje poprawnie <xref:System.Collections.IList> interfejsu i udostępnia wymaganych silnie typizowane elementy członkowskie, zobacz poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Podczas implementowania nowej kolekcji opartej na obiektach takie jak listy połączonej, gdzie typów rozszerzających Nowa kolekcja określić silnego typu, Pomiń ostrzeżenie od tej reguły. Te typy powinny są zgodne z tą regułą i ujawniać silnie typizowane elementy członkowskie.

## <a name="example"></a>Przykład
 W poniższym przykładzie typ `YourType` rozszerza <xref:System.Collections.CollectionBase?displayProperty=fullName>, jak wszystkie kolekcje silnie typizowane. Należy pamiętać, że <xref:System.Collections.CollectionBase> zawiera jawną implementację elementu <xref:System.Collections.IList> interfejsu. W związku z tym musisz tylko podać silnie typizowane elementy <xref:System.Collections.IList> i <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.IList?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>