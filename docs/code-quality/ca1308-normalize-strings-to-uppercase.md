---
title: "CA1308: Znormalizuj ciągi na wielkie litery | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9064ca9861f609499971b9f5188f5b0006458c15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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