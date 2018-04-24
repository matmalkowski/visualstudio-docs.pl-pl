---
title: 'CA1504: Przegląd mylących nazw pól'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0caf5e8c158f2c434bd20e4b033ed1e2f7f37e5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Przegląd mylących nazw pól
|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Nazwa pola wystąpienia rozpoczyna się od "s_" lub nazwa `static` (`Shared` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pola rozpoczyna się ciągiem "m_".

## <a name="rule-description"></a>Opis reguły
 Pole o nazwach zaczynających "s_" są skojarzone z danych statycznych przez wielu użytkowników. Podobnie nazwami pola, które zaczynają się ciągiem "m_" są skojarzone z danych wystąpienia (członek). Dla zapewnienia łatwiej kodu nazw powinna zgodne z konwencjami powszechnie używanych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień nazwę pola, używając odpowiedniego prefiksu. Można również określić pole Akceptuję bieżącego sufiks przez dodanie lub usunięcie `static` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.