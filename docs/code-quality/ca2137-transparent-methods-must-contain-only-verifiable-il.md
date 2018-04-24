---
title: 'CA2137: Jawne metody muszą zawierać tylko weryfikowalne IL'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647240903ab2ada2e8fb319dca967a346a84b4cb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Jawne metody muszą zawierać tylko weryfikowalne IL
|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda zawiera nieweryfikowalny kod lub zwraca typ przez odwołanie.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana podczas próby wykonywania przez kod przezroczysty pod względem zabezpieczeń nieweryfikowalnego MSIL (Microsoft Intermediate Language). Jednak reguła nie zawiera pełnej weryfikacji IL i używa heurystyki do wykrywania większości naruszeń weryfikacji MSIL.

 Aby mieć pewność, że kod zawiera tylko weryfikowalne MSIL, uruchom [Peverify.exe (narzędzie PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) na używanego zestawu. Uruchom PEVerify z **/ przezroczysty** opcję, która ogranicza dane wyjściowe do tylko niemożliwy przezroczysty metod, które mogłyby spowodować błąd. Jeśli / nie jest używana opcja przezroczysty, PEVerify sprawdza także krytycznych metod, które mogą zawierać kod niemożliwy do zweryfikowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, oznacz metodę z <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu lub Usuń kod niemożliwy do zweryfikowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Metoda w tym przykładzie zweryfikowanie kodu i powinien być oznaczony przez <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]