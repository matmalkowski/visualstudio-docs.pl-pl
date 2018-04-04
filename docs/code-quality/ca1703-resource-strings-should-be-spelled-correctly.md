---
title: 'CA1703: Ciągów zasobów powinna być poprawna | Dokumentacja firmy Microsoft'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1227849992cf91a208563020583b19af48b13d42
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ciągu zasobu należy zapisywać poprawnie

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.

## <a name="rule-description"></a>Opis reguły

Ta zasada analizowania ciągu zasobu w wyrazy (tokenizację wyrazy złożone) i sprawdzając pisownię każdego wyrazu/tokenu. Uzyskać informacji o algorytmie analizy, zobacz [CA1704: identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń

Aby rozwiązać naruszenie tej reguły, użyj pełnej słowa, które jest poprawna lub dodać wyraz do słownika. Aby uzyskać informacje o sposobie używania niestandardowych słowników, zobacz [CA1704: identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Zmień język słownika

Domyślnie używana wersja angielski (en) przez moduł sprawdzania pisowni. Jeśli chcesz zmienić język sprawdzania pisowni, możesz to zrobić, dodając jedną z następujących atrybutów do Twojej *AssemblyInfo.cs* lub *AssemblyInfo.vb* pliku:

- Użyj <xref:System.Reflection.AssemblyCultureAttribute> do określenia kultury, jeśli w zestawie satelickim zasobów.
- Użyj <xref:System.Resources.NeutralResourcesLanguageAttribute> do określenia *kultury neutralnej* Twojego zestawu, jeśli zasoby są w tym samym zestawie co kodu.

> [!IMPORTANT]
> Jeśli ustawisz kultury na inny niż kulturę opartą na język angielski, to reguł analizy kodu dyskretnie jest wyłączona.

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie zapisanych słowa skrócić czas, który jest wymagany, aby dowiedzieć się nowe biblioteki oprogramowania.

## <a name="related-rules"></a>Powiązanych reguł

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)