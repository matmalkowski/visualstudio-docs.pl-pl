---
title: 'CA2126: Typ żądań konsolidacji wymaga żądań dziedziczenia'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3143bb7508af1fcb0a946ce7e3a3f0a8697b204
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Typ żądań konsolidacji wymaga żądań dziedziczenia
|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczny typ niezapieczętowany jest chroniony z żądanie łącza ma metodę możliwym do zastąpienia, a typ ani metoda nie jest chroniony za pomocą żądanie dziedziczenia.

## <a name="rule-description"></a>Opis reguły
 Linkdemand, metody lub jej typ deklarujący wymaga bezpośredniego obiektu wywołującego metody mają określone uprawnienie. Żądanie dziedziczenia dla metody wymaga Zastępowanie metody mają określone uprawnienie. Żądanie dziedziczenia typu wymaga Klasa pochodna ma określone uprawnienie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, bezpieczny typ lub metoda o żądanie dziedziczenia dla danego uprawnienia linkdemand.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typu, który narusza zasady.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA2108: Przejrzyj zabezpieczenia deklaratywne typów wartości](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines) [Link wymagań](/dotnet/framework/misc/link-demands)
