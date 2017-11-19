---
title: "CA2137: Jawne metody muszą zawierać tylko weryfikowalne IL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 70a7574e0379c8e4b8dc9a888185efceb480fad4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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