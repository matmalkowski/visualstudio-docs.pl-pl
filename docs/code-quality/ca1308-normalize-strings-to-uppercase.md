---
title: 'CA1308: Znormalizuj ciągi na wielkie litery'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 358910be4245c5c00541a7a4f686226b6250e902
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545703"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Znormalizuj ciągi na wielkie litery
|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja normalizuje ciąg na małe litery.

## <a name="rule-description"></a>Opis reguły
 Ciągi powinny być znormalizowane do użycia wielkich liter. Niewielkiej liczby znaków, gdy są konwertowane na małe litery, nie mogą wykonywać rund. Można wykonywać rund, sposób konwertowania znaków z ustawień regionalnych co do innej wersji regionalnej, który reprezentuje dane znakowe inaczej, a następnie do dokładnie pobierać oryginalne znaki z przekonwertowanego znaków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień operacje, które konwersji ciągów znaków na małe litery, tak aby ciągi są konwertowane na wielkie litery w zamian. Na przykład zmienić `String.ToLower(CultureInfo.InvariantCulture)` do `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń komunikat ostrzegawczy, gdy nie wykonujesz decyzja dotycząca zabezpieczeń na podstawie wyniku (na przykład w przypadku wyświetlania go w interfejsie użytkownika).

## <a name="see-also"></a>Zobacz także
 [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)