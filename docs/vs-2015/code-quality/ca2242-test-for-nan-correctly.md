---
title: 'CA2242: Poprawnie Testuj NaN | Dokumentacja firmy Microsoft'
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
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcbfd5e5bd52be2919835cbe5bdfb06119f2a688
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902348"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testuj poprawnie pod kątem NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2242: poprawnie Testuj NaN](https://docs.microsoft.com/visualstudio/code-quality/ca2242-test-for-nan-correctly).

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wyrażenie sprawdza czy wartość <xref:System.Single.NaN?displayProperty=fullName> lub <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Double.NaN?displayProperty=fullName>, który reprezentuje nie nieliczbowych, wyniki podczas operacji arytmetycznej jest niezdefiniowana. Dowolne wyrażenie, który umożliwia sprawdzenie równość wartości i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `false`. Dowolne wyrażenie, który umożliwia sprawdzenie nierówności pomiędzy wartość i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, a także dokładnie określić, czy wartość reprezentuje <xref:System.Double.NaN?displayProperty=fullName>, użyj <xref:System.Single.IsNaN%2A?displayProperty=fullName> lub <xref:System.Double.IsNaN%2A?displayProperty=fullName> do testowania wartości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano dwa wyrażenia, które niepoprawnie testowanie czy wartość <xref:System.Double.NaN?displayProperty=fullName> i wyrażenie, które korzysta z poprawnie <xref:System.Double.IsNaN%2A?displayProperty=fullName> do testowania wartości.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]



