---
title: "CA1041: Zapewnianie wiadomości ObsoleteAttribute | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d6c0ac4d5972e06768306be51a92e93da763ce0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Zapewnianie wiadomości ObsoleteAttribute
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ lub element członkowski jest oznaczony przy użyciu <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybut, który nie ma jej <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> określona właściwość.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.ObsoleteAttribute>Służy do oznaczania przestarzałe biblioteki typów i członków. Konsumenci biblioteki należy unikać użycia dowolnego typu lub elementu członkowskiego, który jest oznaczony jako przestarzały. Jest tak, ponieważ nie może być obsługiwany i po pewnym czasie zostaną usunięte z nowszej wersji biblioteki. Gdy typ lub element członkowski oznaczony za pomocą <xref:System.ObsoleteAttribute> jest kompilowana <xref:System.ObsoleteAttribute.Message%2A> właściwości atrybutu jest wyświetlany. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. Informacje te obejmują zazwyczaj jak długo przestarzałego typu lub elementu członkowskiego, które będą obsługiwane przez projektantów biblioteki i zastąpienia preferowany do użycia.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj `message` parametr <xref:System.ObsoleteAttribute> konstruktora.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły, ponieważ <xref:System.ObsoleteAttribute.Message%2A> właściwość zawiera najważniejsze informacje o przestarzałego typu lub elementu członkowskiego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono przestarzały element członkowski, który ma poprawnie zadeklarowane <xref:System.ObsoleteAttribute>.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>