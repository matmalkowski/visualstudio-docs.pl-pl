---
title: 'CA1504: Przegląd mylących nazw pól'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 1457390b523af45b5e3b23a3420cba830f45cee5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915085"
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