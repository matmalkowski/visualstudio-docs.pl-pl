---
title: 'CA2204: Literały powinny być napisane poprawnie'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f86658978a105c1fa4f3c4602b5c838f4c80726
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literały powinny być napisane poprawnie

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Literał ciągu jest przekazywany jako argument parametru Lokalizowalny lub do zlokalizowania właściwości, a ciąg zawiera co najmniej jeden słowa, które nie są rozpoznawane przez moduł sprawdzania pisowni biblioteki.

## <a name="rule-description"></a>Opis reguły

Ta reguła sprawdza ciąg literału, który jest przekazywany jako wartość parametru lub właściwości, gdy dla jednego lub więcej z następujących przypadków ma wartość true:

- <xref:System.ComponentModel.LocalizableAttribute> Atrybut parametru lub właściwość jest ustawiona na true.

- Nazwa parametru lub właściwości zawiera "Text", "Komunikat" lub "Podpis".

- Nazwa zmiennej ciągu, który jest przekazywany do <xref:System.Console.Write%2A> lub <xref:System.Console.WriteLine> metoda jest "value" lub "format".

Ta reguła umożliwia przekształcanie ciągów literałów w wyrazy, tokenizację wyrazy złożone i sprawdzając pisownię każdego wyrazu lub token. Uzyskać informacji o algorytmie analizy, zobacz [CA1704: identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Język

Moduł sprawdzania pisowni obecnie sprawdza tylko względem słowniki kulturę opartą na języku angielskim. Kultura projektu w pliku projektu można zmienić, dodając **CodeAnalysisCulture** elementu.

Na przykład:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Jeśli ustawisz kultury na inny niż kulturę opartą na język angielski, to reguł analizy kodu dyskretnie jest wyłączona.

## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń

Aby rozwiązać naruszenie tej reguły, Popraw pisownię wyrazu, lub Dodaj ten wyraz do słownika niestandardowego. Aby uzyskać informacje o sposobie używania niestandardowych słowników, zobacz [porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie zapisanych wyrazów skrócić czas nauki wymagane dla nowej biblioteki oprogramowania.

## <a name="related-rules"></a>Powiązanych reguł

- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)