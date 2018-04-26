---
title: 'CA1822: Oznacz elementy członkowskie jako statyczne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: 498a3638a02891683aff1b343431418d1a82bab0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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