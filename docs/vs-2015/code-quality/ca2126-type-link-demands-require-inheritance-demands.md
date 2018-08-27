---
title: 'CA2126: Typ żądań konsolidacji wymaga żądań dziedziczenia | Dokumentacja firmy Microsoft'
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
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f482350517858fffc74600c3743a22192aa6a49
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901909"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Typ żądań konsolidacji wymaga żądań dziedziczenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2126: typ żądań konsolidacji wymaga żądań dziedziczenia](https://docs.microsoft.com/visualstudio/code-quality/ca2126-type-link-demands-require-inheritance-demands).

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Niezamknięty typ publiczny jest chroniony za pomocą zapotrzebowania na łącza ma metodę, którą można przesłonić, a typ ani metoda nie jest chroniony za pomocą żądania dziedziczenia.

## <a name="rule-description"></a>Opis reguły
 Zapotrzebowania na łącza na metodę lub jego typ deklarujący wymaga bezpośredniego obiektu wywołującego metody ma określone uprawnienie. Żądania dziedziczenia metody wymaga przesłanianie metody ma określone uprawnienie. Żądania dziedziczenia w danym typie wymaga Klasa pochodna ma określone uprawnienie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, bezpiecznego typu lub metody za pomocą żądania dziedziczenia dla danego uprawnienia zapotrzebowania na łącza.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2108: Przejrzyj zabezpieczenia deklaratywne typów wartości](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Inheritancedemand](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [Link zapotrzebowanie](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [żądania](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)



