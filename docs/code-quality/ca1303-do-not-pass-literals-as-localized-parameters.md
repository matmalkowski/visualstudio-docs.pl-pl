---
title: 'CA1303: Nie należy przekazywać literałów jako parametrów zlokalizowanych'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b621306bab673172c1c437ca0a959e4bc36f6da
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Nie należy przekazywać literałów jako parametrów zlokalizowanych
|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda przekazuje ciąg literału jako parametr do konstruktora lub metody [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] klasy biblioteki i czy powinien on być lokalizowalny.

 To ostrzeżenie jest wywoływane, gdy ciąg literału jest przekazywany jako wartość parametru lub właściwości i co najmniej jeden z następujących przypadków jest prawdziwy:

-   <xref:System.ComponentModel.LocalizableAttribute> Atrybut parametru lub właściwość jest ustawiona na true.

-   Nazwa parametru lub właściwości zawiera "Text", "Komunikat" lub "Podpis".

-   Nazwa parametru ciągu, który jest przekazywany do metody Console.Write lub elementu Console.WriteLine jest "value" lub "format".

## <a name="rule-description"></a>Opis reguły
 Literały ciągu, które są osadzone w kodzie źródłowym są trudne do zlokalizowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zamień literału ciągu pobierane w drodze wystąpienia ciągu <xref:System.Resources.ResourceManager> klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli nie jest lokalizowany biblioteki kodu lub ciąg nie jest widoczne dla użytkownika końcowego lub deweloperem, za pomocą biblioteki kodu.

 Użytkownicy można wyeliminować szumu przed metod, które nie powinny być przekazywane zlokalizowanych ciągów albo zmiana nazwy parametru lub właściwości o nazwie lub oznaczenie tych elementów jako warunkowego.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę, która zgłasza wyjątek, gdy jeden z jego dwóch argumentów są poza zakresem. Dla pierwszego argumentu konstruktora do wyjątku jest przekazywany literału ciągu, który narusza tę regułę. Drugi argument konstruktora poprawnie jest przekazany ciąg pobierane w drodze <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Zobacz też
 [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index)