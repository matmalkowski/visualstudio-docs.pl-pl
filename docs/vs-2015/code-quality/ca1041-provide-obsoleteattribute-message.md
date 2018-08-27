---
title: 'CA1041: Zapewnianie wiadomości ObsoleteAttribute | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 298f6d3cbfc8b71443fe9e8e9733e5729963cea8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902946"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Zapewnianie wiadomości ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1041: komunikat ObsoleteAttribute zapewniają](https://docs.microsoft.com/visualstudio/code-quality/ca1041-provide-obsoleteattribute-message).

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ lub element członkowski jest oznaczony za pomocą <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybut, który nie ma jej <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> określona właściwość.

## <a name="rule-description"></a>Opis reguły
 <xref:System.ObsoleteAttribute> Służy do oznaczania przestarzałe biblioteki typów i elementów członkowskich. Konsumenci biblioteki należy unikać użycia dowolnego typu lub elementu członkowskiego, który jest oznaczony jako przestarzały. Jest to spowodowane może nie być obsługiwany i po pewnym czasie zostaną usunięte z nowszymi wersjami biblioteki. Gdy typ lub element członkowski oznaczony za pomocą <xref:System.ObsoleteAttribute> jest kompilowany <xref:System.ObsoleteAttribute.Message%2A> właściwość atrybutu jest wyświetlana. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. Informacje te obejmują zazwyczaj ile przestarzałego typu lub elementu członkowskiego, które będą obsługiwane przez projektantów biblioteki i zastąpienie preferowany do użycia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać `message` parametr <xref:System.ObsoleteAttribute> konstruktora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, ponieważ <xref:System.ObsoleteAttribute.Message%2A> dostarcza krytycznych informacji na temat przestarzałego typu lub składowej.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano przestarzałą składową, która ma poprawnie zadeklarowane <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.ObsoleteAttribute?displayProperty=fullName>



