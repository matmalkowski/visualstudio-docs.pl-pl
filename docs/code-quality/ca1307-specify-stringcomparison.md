---
title: 'CA1307: Określ StringComparison'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dac870bde757d77e1d0025a1b387f54ca928a5f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900858"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Określ StringComparison
|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja porównywania ciągów używa przeciążenie metody, która nie określa <xref:System.StringComparison> parametru.

## <a name="rule-description"></a>Opis reguły
 Ciąg wielu operacji najważniejszych <xref:System.String.Compare%2A> i <xref:System.String.Equals%2A> metod, Udostępnij przeciążenie akceptującego <xref:System.StringComparison> wartość wyliczenia jako parametr.

 Zawsze, gdy istnieje tego przyjmuje <xref:System.StringComparison> parametru powinna być używana zamiast funkcji przeciążenia, które nie wymaga tego parametru. Przez jawne ustawienie tego parametru, kod jest często doprecyzowania dokonane i łatwiejsze w obsłudze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, należy zmienić metod porównania ciągów do przeciążenia, które akceptują <xref:System.StringComparison> wyliczenie jako parametr. Na przykład: Zmień `String.Compare(str1, str2)` do `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy biblioteki lub aplikacja jest przeznaczona dla ograniczonej użytkowników lokalnych i w związku z tym nie będzie lokalizowany.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia globalizacji](../code-quality/globalization-warnings.md) [CA1309: Użyj porządkowego StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)