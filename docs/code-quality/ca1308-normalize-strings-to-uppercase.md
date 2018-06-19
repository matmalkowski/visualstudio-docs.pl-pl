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
ms.openlocfilehash: a5cda66d2a43ee3fde8e3e7b2d22a64a09655da3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897146"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Znormalizuj ciągi na wielkie litery
|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja normalizuje ciągu na małe litery.

## <a name="rule-description"></a>Opis reguły
 Ciągi powinny być znormalizowane do użycia wielkich liter. Dla niewielkiej liczby znaków, gdy są konwertowane na małe litery, nie można wprowadzić podróż. Aby podróż oznacza, że do konwersji znaków z jednego ustawień regionalnych innych regionalnych reprezentujący dane znakowe inaczej, a następnie dokładnie pobrać oryginalne znaki z przekonwertowanego znaków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień operacje, które Konwertowanie ciągów na małe litery, dzięki czemu ciągi są konwertowane na wielkie litery w zamian. Na przykład zmienić `String.ToLower(CultureInfo.InvariantCulture)` do `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń komunikat ostrzegawczy, gdy nie podejmowania decyzji zabezpieczeń na podstawie wyniku (na przykład gdy wyświetlasz w interfejsie użytkownika).

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)