---
title: 'CA1900: Pola o typie wartości powinny być przenośne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9add21d932f7685a2dee214f396b2cbda089a5a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917218"
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