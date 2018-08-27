---
title: 'CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter | Dokumentacja firmy Microsoft'
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
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d60c29b7e6a5cec32b8a694bb0b21d7f85538e01
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902886"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identyfikatory powinny różnić się czymś więcej niż wielkością liter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1708: identyfikatory powinny różnić się przez więcej niż wielkością liter](https://docs.microsoft.com/visualstudio/code-quality/ca1708-identifiers-should-differ-by-more-than-case).

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwy dwa typy, członków lub przestrzeni nazw FQDN parametrów są identyczne, gdy są one konwertowane na małe litery.

## <a name="rule-description"></a>Opis reguły
 Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter. Na przykład [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] to powszechnie używany język bez uwzględniania wielkości liter.

 Ta reguła jest uruchamiana na tylko członków publicznie widoczne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę, która jest unikatowa, gdy jest porównywana do innych identyfikatorów, bez uwzględniania wielkości liter.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Biblioteki mogą nie być użyteczne we wszystkich językach, które znajdują się w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="example-of-a-violation"></a>Przykładem naruszenia
 W poniższym przykładzie pokazano naruszenie tej zasady.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)



