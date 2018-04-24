---
title: 'CA1058: Typy nie powinny rozszerzać pewnych typów bazowych'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bd3461cae62f1d4b23f5afa22b0af67c78d41fc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy nie powinny rozszerzać pewnych typów bazowych
|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz rozszerza niektóre typy podstawowe. Obecnie ta zasada zgłasza typów wyprowadzonych z następujących typów:

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.Xml.XmlDocument?displayProperty=fullName>

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.Queue?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Aby uzyskać [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji 1 zalecono pochodzi nowych wyjątków z <xref:System.ApplicationException>. Zalecenie została zmieniona i nowych wyjątków powinien pochodzić od <xref:System.Exception?displayProperty=fullName> lub jednej z jego podklas w <xref:System> przestrzeni nazw.

 Nie należy tworzyć podklasą <xref:System.Xml.XmlDocument> Jeśli chcesz utworzyć widok źródłowego obiektu modelu lub źródła danych XML.

### <a name="non-generic-collections"></a>Kolekcje inny niż ogólny
 Użyj i/lub rozszerzyć kolekcje ogólne, jeśli to możliwe. Kolekcje nieogólnego w kodzie, nie zostanie rozszerzony, chyba że zostały wydane wcześniej.

 **Przykłady niepoprawne użycie**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Przykłady użycia poprawne**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, pochodzić typ z innym typem bazowym lub ogólnej kolekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia od tej reguły dla naruszeń o <xref:System.ApplicationException>. Można bezpiecznie pominąć ostrzeżenie od tej reguły dla naruszeń o <xref:System.Xml.XmlDocument>. Jest bezpieczne pominąć ostrzeżenie o kolekcja nierodzajową, jeśli kod został udostępniony wcześniej.