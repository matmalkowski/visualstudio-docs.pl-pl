---
title: Zestaw reguł globalizacji dla zarządzanego kodu
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3c717eeeb94deee611c4e9cf5da573e1039e13fc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Zestaw reguł globalizacji dla zarządzanego kodu
Można użyć programu Microsoft globalizacji zestaw reguł skupić się na problemy, które mogą uniemożliwić danych w aplikacji poprawnie wyświetlany w różnych językach, ustawień regionalnych i kultur. Należy uwzględnić tej reguły, jeśli aplikacja jest zlokalizowana globalizowana, lub obie.

|Reguła|Opis|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Określ MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Należy unikać duplikowania akceleratorów|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Nie umieszczaj w kodzie ciągów specyficznych ustawień regionalnych|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nie należy przekazywać literałów jako zlokalizowanych parametrów|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Określ CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Określ IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Ustaw ustawienia regionalne dla typów danych|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Określ StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizuj ciągi na wielkie litery|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Użyj porządkowego StringComparison|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Określ kierowanie dla argumentów ciągu P/Invoke|