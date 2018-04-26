---
title: 'CA1302: Nie należy kodować ciągów określonych dla ustawień regionalnych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a00f78739a9287c996e87f182ca34ecba6d484c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nie należy kodować ciągów określonych dla ustawień regionalnych
|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda używa literału ciągu reprezentujący części ścieżki niektórych folderów systemowych.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> Wyliczenie zawiera elementy członkowskie, które dotyczą foldery specjalne systemu. Lokalizacje folderów może mieć różne wartości w różnych systemach operacyjnych, użytkownik może zmienić niektóre lokalizacje i lokalizacje są zlokalizowane. Przykładem folderu specjalnego jest folderem systemowym, który jest "C:\WINDOWS\system32" na [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] , ale "C:\WINNT\system32" na [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Metoda zwraca lokalizacje, które są skojarzone z <xref:System.Environment.SpecialFolder> wyliczenia. Lokalizacje, które są zwracane przez <xref:System.Environment.GetFolderPath%2A> są zlokalizowane i właściwe dla uruchomionego komputera.

 Ta zasada tokenizes ścieżki folderów, które są pobierane przy użyciu <xref:System.Environment.GetFolderPath%2A> metody na poziomie katalogów. Literał ciągu jest porównywany z tokenów. Jeśli zostanie znaleziony dopasowanie, zakłada się, że metoda tworzy ciąg, który odwołuje się do lokalizacji w systemie, która jest skojarzona z tokenem. Mobilność i możliwości zlokalizowania użyć <xref:System.Environment.GetFolderPath%2A> metoda pobierania lokalizacje folderów systemowych specjalne, zamiast używania literałów ciągów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, należy pobrać lokalizacji za pomocą <xref:System.Environment.GetFolderPath%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli literał ciągu nie jest używana do odwoływania się do jednego z lokalizacji systemu, które jest skojarzone z <xref:System.Environment.SpecialFolder> wyliczenia.

## <a name="example"></a>Przykład
 Poniższy przykład tworzy ścieżce wspólnej folderu danych aplikacji, który generuje ostrzeżenie od tej reguły. Następnie przykładzie pobiera ścieżkę przy użyciu <xref:System.Environment.GetFolderPath%2A> metody.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1303: Nie przekazuj literałów jako parametrów zlokalizowanych](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)