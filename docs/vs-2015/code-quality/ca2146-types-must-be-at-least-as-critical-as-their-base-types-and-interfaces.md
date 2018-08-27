---
title: 'CA2146: Typy muszą być co najmniej tak krytyczne jak ich typy podstawowe i interfejsy | Dokumentacja firmy Microsoft'
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
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 09b6c1ca57582ee17f048220bbb73f7605883df7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901542"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typy muszą być co najmniej tak ważne, jak ich typy podstawowe i interfejsy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2146: typy muszą być co najmniej tak krytyczne jak ich typy podstawowe i interfejsy](https://docs.microsoft.com/visualstudio/code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces).

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Przezroczysty typ pochodzi z typu, który jest oznaczony przy użyciu <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityCriticalAttribute>, lub typu, który jest oznaczony za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu jest tworzony na podstawie typu, który jest oznaczony przy użyciu <xref:System.Security.SecurityCriticalAttribute> atrybutu.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa. Powoduje naruszenie tej zasady przezroczystości poziomu 2 <xref:System.TypeLoadException> przypadku typ pochodny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać problem to naruszenie, należy oznaczyć typu pochodnego lub implementującej atrybutem przejrzystości, który jest co najmniej tak krytyczne jak typem bazowym lub interfejsem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]



