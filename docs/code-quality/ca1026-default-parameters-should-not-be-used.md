---
title: "CA1026: Domyślne parametry nie powinny być używane | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43f83bf88e017da06ee3653019aa91807229d55e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Domyślne parametry nie powinny być używane
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Widoczne na zewnątrz typu zawiera widocznej zewnętrznie metodzie, która używa domyślnego parametru.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody, które używają parametry domyślne są dozwolone w typowych specyfikacji języka (CLS); Jednak ze specyfikacją CLS pozwala kompilatory zignorowanie wartości, które są przypisane do tych parametrów. Kod, który jest przeznaczony dla kompilatorów, które będzie ignorować domyślne wartości parametrów jawnie podać argumenty dla każdego parametru domyślnego. Aby zapewnić zachowanie w językach programowania, metody, które używają parametrów domyślnych powinna zostać zastąpiona przeciążenia metody, które udostępniają domyślne parametry.  
  
 Kompilator wartości domyślne parametrów dla rozszerzenia zarządzane dla języka C++ w przypadku ignoruje uzyskuje dostęp do kodu zarządzanego. Kompilator Visual Basic obsługuje metody, których domyślne parametry, które używają [opcjonalnie](/dotnet/visual-basic/language-reference/modifiers/optional) — słowo kluczowe.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Zastąp metodę, która używa parametry domyślne przeciążeniami metod, zapewniających parametrów domyślnych.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metodę, która korzysta z domyślnych parametrów i przeciążonych metod, które zapewniają podobne funkcje.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1025: Zastąp powtarzające się argumenty tablicą parametrów](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)