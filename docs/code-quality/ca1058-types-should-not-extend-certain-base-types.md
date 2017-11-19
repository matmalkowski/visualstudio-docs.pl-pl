---
title: "CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45cddd908c53d129a230b998c6dad03196a31c49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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