---
title: "CA1303: Nie należy przekazywać literałów jako zlokalizowanych parametrów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce6ed64a6991342b4dc1506b8384f7691cc90b8f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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