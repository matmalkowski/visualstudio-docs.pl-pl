---
title: "CA1715: Identyfikatory powinny mieć poprawny prefiks | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d8a87359b0a4d1ac45199e4f233a7bf3174ba2bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Identyfikatory powinny mieć poprawny prefiks
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Przerywanie — po w interfejsach.<br /><br /> Bez podziału — gdy na parametry typu ogólnego.|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa interfejsu widoczne na zewnątrz nie rozpoczyna się wielkimi literami "I".  
  
 —lub—  
  
 Nazwa parametru typu ogólnego, na zewnątrz typu lub metody nie rozpoczyna się wielką t ".  
  
## <a name="rule-description"></a>Opis reguły  
 Konwencja nazwy niektórych elementów programowania rozpoczynają się od określonego prefiksu.  
  
 Nazwy interfejsów powinien się rozpoczynać wielkie litery, który następuje "I" innego wielką literę. Ta zasada zgłasza naruszeń dla nazwy interfejsu, takie jak "MyInterface" i "IsolatedInterface".  
  
 Nazwy parametrów typu ogólnego powinien zaczynać się od wielkiej litery 'T' i opcjonalnie może następować innego wielką literę. Ta zasada zgłasza naruszeń dla nazwy parametru typu ogólnego, takie jak "V" i "Type".  
  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień nazwę identyfikatora, aby poprawnie jest prefiksem.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 **W poniższym przykładzie przedstawiono niepoprawnie nazwanego interfejsu.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## <a name="example"></a>Przykład  
 **Poniższy przykład poprawki poprzedniej naruszenie, prefiksu interfejsu z "I".**  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## <a name="example"></a>Przykład  
 **W poniższym przykładzie przedstawiono parametr niepoprawnie nazwanego typu ogólnego.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]  
  
## <a name="example"></a>Przykład  
 **Poniższy przykład poprawki poprzedniej naruszenie, parametru typu ogólnego z 'T prefiksu ".**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1722: Identyfikatory nie powinny mieć niepoprawnego prefiksu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)