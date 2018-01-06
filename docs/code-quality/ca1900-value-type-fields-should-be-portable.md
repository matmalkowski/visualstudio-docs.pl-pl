---
title: "CA1900: Pola typu wartości powinny być przenośne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f023749c16a1c4fed36654036813007a83b21a72
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Pola o typie wartości powinny być przenośne
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Kategoria|Microsoft.Portability|  
|Zmiana kluczowa|Przerywanie — Jeśli pole może być widoczny spoza zestawu.<br /><br /> Bez podziału — Jeśli pole nie jest widoczna poza zestaw.|  
  
## <a name="cause"></a>Przyczyna  
 Ta reguła sprawdza, czy struktur, które są zadeklarowane o układzie jawnym są poprawnie wyrównane, gdy przekazywane do kodu niezarządzanego na 64-bitowych systemach operacyjnych. IA-64 nie zezwala na uzyskuje dostęp do pamięci niewyrównany i proces ulegnie awarii, jeśli to naruszenie nie został rozwiązany.  
  
## <a name="rule-description"></a>Opis reguły  
 Struktury, które ma układ jawny, który zawiera niewyrównane pola powodują awarię na 64-bitowych systemach operacyjnych.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Wszystkie pola, które są mniejsze niż 8 bajtów musi mieć wartość przesunięcia, które są wielokrotnością ich rozmiaru i pola, które są 8 bajtów lub więcej musi mieć przesunięcia, które są wielokrotnością liczby 8. Innym rozwiązaniem jest użycie `LayoutKind.Sequential` zamiast `LayoutKind.Explicit`, jeśli jest to uzasadnione.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 To ostrzeżenie powinno być pomijane tylko wtedy, gdy wystąpi błąd.