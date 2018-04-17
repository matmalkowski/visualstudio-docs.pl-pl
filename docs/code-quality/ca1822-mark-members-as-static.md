---
title: 'CA1822: Oznacz elementy członkowskie jako statyczne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7524db68b984155a8a03f1f0cb1cce0373b382a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Oznacz elementy członkowskie jako statyczne
|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Dzielenie non - Jeśli element członkowski nie jest widoczny spoza zestawu, niezależnie od tego, zmiany wprowadzone. Bez podziału — element członkowski w przypadku zmiany tylko do elementu członkowskiego wystąpienia z `this` — słowo kluczowe.<br /><br /> Przerywanie — Jeśli zmienisz element członkowski z elementu członkowskiego wystąpienia statyczny element członkowski i widoczny spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski, który nie dostępu do danych wystąpienia nie jest oznaczony jako statyczne (Shared w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Opis reguły  
 Elementy członkowskie, które nie uzyskują dostęp do wystąpienia danych lub wywołanie metody wystąpienia może być oznaczony jako statyczne (Shared w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. Emitowanie miejsc wywołania niewirtualne uniemożliwi sprawdzenie w czasie wykonywania dla każdego wywołania, który sprawia, że bieżący wskaźnik obiektu jest różna od null. Można to osiągnąć są bardziej wydajne mierzalnych dla wrażliwych wydajność kodu. W niektórych przypadkach błąd dostępu do bieżącego wystąpienia obiektu reprezentuje problem poprawności.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Oznacz element członkowski jako statyczny (lub Shared w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) lub użyj parametru "this" / "Me" w metodzie body, w razie potrzeby.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły dla uprzednio wysłane kodu, dla którego poprawkę byłoby na istotne zmiany.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)