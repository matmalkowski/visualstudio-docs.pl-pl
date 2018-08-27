---
title: 'CA1307: Określ StringComparison | Dokumentacja firmy Microsoft'
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
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2c96b8c895106337a8578b6662c0e61830b38f55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902949"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Określ StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1307: Określ StringComparison](https://docs.microsoft.com/visualstudio/code-quality/ca1307-specify-stringcomparison).

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja porównania ciągu używa przeciążenia metody, która nie ustawia <xref:System.StringComparison> parametru.

## <a name="rule-description"></a>Opis reguły
 Wiele ciągów operacje najważniejszych <xref:System.String.Compare%2A> i <xref:System.String.Equals%2A> metod, zapewnienia przeciążenia, które akceptuje <xref:System.StringComparison> wartość wyliczenia jako parametr.

 Zawsze, gdy istnieje tego przyjmuje przeciążenie <xref:System.StringComparison> parametru należy używać zamiast przeciążenia, które nie przyjmuje tego parametru. Poprzez jawne ustawienie tego parametru, kod jest często co wykonane i łatwiejsze w utrzymaniu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić metody porównania ciągu do przeciążenia, które akceptują <xref:System.StringComparison> wyliczenia jako parametr. Na przykład: zmienianie `String.Compare(str1, str2)` do `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy biblioteka lub aplikacja jest przeznaczona dla ograniczone odbiorców lokalnych i w związku z tym nie będzie lokalizowany.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md) [CA1309: Używaj wyliczenia StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)



