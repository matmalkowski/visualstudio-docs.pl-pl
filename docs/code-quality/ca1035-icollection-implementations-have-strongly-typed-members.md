---
title: "CA1035: Implementacje ICollection mają silnie typizowane elementy członkowskie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a3e595046442092c11b068b6df6fde2a9a56e705
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementacje ICollection mają silnie typizowane elementy członkowskie
|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Implementuje typu publiczne lub chronione <xref:System.Collections.ICollection?displayProperty=fullName> , ale nie udostępnia silnie typizowane metody <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Silnie typizowaną wersję <xref:System.Collections.ICollection.CopyTo%2A> zaakceptować dwóch parametrów i nie może mieć <xref:System.Array?displayProperty=fullName> lub tablicę <xref:System.Object?displayProperty=fullName> jako swój pierwszy parametr.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada wymaga <xref:System.Collections.ICollection> implementacje zapewnienie silnie typizowane elementy członkowskie, dzięki czemu użytkownicy nie są wymagane do rzutowania argumentów <xref:System.Object> wpisz przy korzystaniu z funkcji dostępnych za pośrednictwem interfejsu. Ta zasada przyjęto założenie, że typ, który zawiera <xref:System.Collections.ICollection> ma tak, aby zarządzać kolekcję wystąpień typu, który jest mocniejszy niż element <xref:System.Object>.  
  
 <xref:System.Collections.ICollection>implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejsu. Jeśli rozszerzenie obiektów w kolekcji <xref:System.ValueType?displayProperty=fullName>, należy podać element jednoznacznie dla <xref:System.Collections.IEnumerable.GetEnumerator%2A> w celu uniknięcia spadek wydajności, który jest spowodowany przez opakowanie. Nie jest to wymagane w przypadku obiektów kolekcji typu odwołania.  
  
 Aby zaimplementować silnie typizowaną wersję elementu członkowskiego interfejsu, implementować członków interfejsu a jawnie przy użyciu nazw w formie `InterfaceName.InterfaceMemberName`, takich jak <xref:System.Collections.ICollection.CopyTo%2A>. Elementy członkowskie interfejsu jawnego Użyj typów danych, które są zadeklarowane w interfejsie. Implementowanie jednoznacznie elementów przy użyciu nazwy elementu członkowskiego interfejsu, takich jak <xref:System.Collections.ICollection.CopyTo%2A>. Deklarowanie silnie typizowane elementy członkowskie jako public i deklarować parametrów i zwracają wartości były silnego typu, który jest zarządzany przez kolekcję. Silne typy Zastąp słabszych typów, takich jak <xref:System.Object> i <xref:System.Array> który został zadeklarowany w interfejsie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, implementuje element członkowski interfejsu jawnie (Zadeklaruj ją jako <xref:System.Collections.ICollection.CopyTo%2A>). Dodaj publiczny jednoznacznie elementu członkowskiego, zadeklarowany jako `CopyTo`, i podjąć silnie typizowaną tablicę jako swój pierwszy parametr.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Ostrzeżenie od tej zasady należy pominąć, jeśli wdrożenie nowej kolekcji opartej na obiektach takich jak drzewo binarne, gdzie typów rozszerzających Nowa kolekcja określić silnego typu. Te typy powinny są zgodne z tą regułą i ujawniać silnie typizowane elementy członkowskie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano poprawne sposób implementowania <xref:System.Collections.ICollection>.  
  
 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>