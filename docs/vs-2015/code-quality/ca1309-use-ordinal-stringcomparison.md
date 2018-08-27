---
title: 'CA1309: Używaj wyliczenia StringComparison | Dokumentacja firmy Microsoft'
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
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0666b5db2e72c1adcbee3cb5a601b2eb3bf42b46
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902285"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Użyj porządkowego StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1309: Używaj wyliczenia StringComparison](https://docs.microsoft.com/visualstudio/code-quality/ca1309-use-ordinal-stringcomparison).

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia <xref:System.StringComparison> albo parametr **numer** lub **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Opis reguły
 Wiele ciągów operacje najważniejszych <xref:System.String.Compare%2A?displayProperty=fullName> i <xref:System.String.Equals%2A?displayProperty=fullName> metod, teraz dostarczać przeciążenia, które akceptuje <xref:System.StringComparison?displayProperty=fullName> wartość wyliczenia jako parametr.

 Po określeniu jednej **StringComparison.Ordinal** lub **StringComparison.OrdinalIgnoreCase**, jest nielingwistyczna porównywania ciągów. Oznacza to funkcje, które są specyficzne dla języka naturalnego są ignorowane, podczas porównywania decyzji. Oznacza to, decyzje są oparte na jednobajtowych porównania i Ignoruj wielkość liter w wyrazie lub równoważności tabel, które są parametryzowane przez kulturę. W rezultacie przez jawne ustawienie parametru na wartość **StringComparison.Ordinal** lub **StringComparison.OrdinalIgnoreCase**, kod często uzyskuje szybkość, zwiększa poprawność i staje się bardziej niezawodna.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmień metodę porównywania ciągów na przeciążenie, które akceptuje <xref:System.StringComparison?displayProperty=fullName> wyliczenia jako parametr oraz określ **numer** lub **OrdinalIgnoreCase**. Na przykład zmienić `String.Compare(str1, str2)` do `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy do biblioteki lub aplikacji jest przeznaczony dla ograniczonej odbiorców lokalnych lub semantykę bieżącej kultury, które powinny być używane.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md) [CA1307: Określ wyliczenie StringComparison](../code-quality/ca1307-specify-stringcomparison.md)



