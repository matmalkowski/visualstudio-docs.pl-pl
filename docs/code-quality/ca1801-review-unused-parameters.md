---
title: "CA1801: Przejrzyj nieużywane parametry | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bb8c38d1436ca687664f92bfe0ba6db1ccf68ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Przejrzyj nieużywane parametry
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału — Jeśli element członkowski nie jest widoczny spoza zestawu, niezależnie od tego, wprowadzone zmiany.<br /><br /> Bez podziału — Jeśli zmienisz element członkowski, aby użyć parametru w jego treści.<br /><br /> Przerywanie — Jeśli Usuń parametr i jest on widoczny spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Podpis metody zawiera parametr, który nie jest używany w jej treści. Ta zasada nie bada następujących metod:  
  
-   Metody odwołuje się delegata.  
  
-   Metody stosowane jako procedury obsługi zdarzeń.  
  
-   Metody zadeklarowane jako z `abstract` (`MustOverride` w języku Visual Basic) modyfikator.  
  
-   Metody zadeklarowane jako z `virtual` (`Overridable` w języku Visual Basic) modyfikator.  
  
-   Metody zadeklarowane jako z `override` (`Overrides` w języku Visual Basic) modyfikator.  
  
-   Metody zadeklarowane jako z `extern` (`Declare` instrukcji w języku Visual Basic) modyfikator.  
  
## <a name="rule-description"></a>Opis reguły  
 Przejrzyj parametry w metodach-virtual, które nie są używane w treści metody do upewnij się, że istnieje nie poprawności wokół błąd dostępu do nich. Nieużywane parametry pociągnąć za sobą wydajność i koszty.  
  
 Czasami naruszenie tej reguły może wskazywać na błąd implementacji w metodzie. Na przykład parametr powinien mieć używany w treści metody. Pomijanie ostrzeżeń tej reguły, jeśli parametr musi istnieć z powodu zgodności z poprzednimi wersjami.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Usuń nieużywane parametr (istotne zmiany), lub użyj parametru w treści metody (z systemem innym niż istotnej zmiany).  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły dla uprzednio wysłane kodu, dla którego poprawkę byłoby na istotne zmiany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dwie metody. Jedna z metod naruszają tę regułę i innej metody spełnia reguły.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Unikaj wewnętrznych klas bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)