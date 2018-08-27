---
title: 'CA1703: Ciągi zasobu powinny być zapisane poprawnie | Dokumentacja firmy Microsoft'
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
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fc83d109666c98718b1a4b1196db11a81424c911
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901676"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ciągu zasobu należy zapisywać poprawnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1703: ciągi zasobu powinny być zapisane poprawnie](https://docs.microsoft.com/visualstudio/code-quality/ca1703-resource-strings-should-be-spelled-correctly).

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.

## <a name="rule-description"></a>Opis reguły
 Ta reguła analizuje ciąg zasobu na słowa (tokenizowanie wyrazy złożone) oraz sprawdzając pisownię każdego wyrazu/tokenu. Aby uzyskać informacji na temat analizy algorytmu, zobacz [CA1704: identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Domyślnie używany jest język angielski (en) wersję modułu sprawdzania pisowni.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, użyj kompletne wyrazy, które jest poprawna, lub Dodaj wyrażenie do słownika niestandardowego. Aby uzyskać informacje o sposobie używania słowników niestandardowych, zobacz [CA1704: identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie właściwej słów skrócić czas, który jest wymagany, aby dowiedzieć się, nowe biblioteki oprogramowania.

## <a name="related-rules"></a>Powiązane reguły
 [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)



