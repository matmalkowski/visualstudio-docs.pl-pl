---
title: "CA1011: Należy rozważyć przekazywanie typów podstawowych jako parametrów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae6923e369d0f4245759bff2c66dc931dc51baf8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Należy rozważyć przekazywanie typów bazowych jako parametrów
|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Deklaracja metody obejmuje formalny parametr, który jest typem pochodnym, a metoda wywołuje tylko elementy członkowskie typu podstawowego parametru.  
  
## <a name="rule-description"></a>Opis reguły  
 Jeśli typ podstawowy jest określony jako parametr w deklaracji metody, dowolny typ, który pochodzi od typu podstawowego, może zostać przekazany jako odpowiadający argument do metody. Gdy argument jest używany wewnątrz treści metody, określonej metody, która jest wykonywana zależy od typu argumentu. Jeśli dodatkowe funkcje, że pochodzi od typu pochodnego nie jest wymagany, typ podstawowy umożliwiają szersze użyj metody.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, należy zmienić typ parametru na jego typ podstawowy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Aby pominąć ostrzeżenie od tej reguły można bezpiecznie  
  
-   Jeśli metoda wymaga określonych funkcji, które są udostępniane przez typ pochodny  
  
     \-lub -  
  
-   Aby wymusić, że typ pochodny lub typu pochodnego jest przekazywany do metody.  
  
 W takich przypadkach kod będzie bardziej niezawodne z powodu silnego typu sprawdzanie zapewnianej przez kompilator i środowiska wykonawczego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metodę, `ManipulateFileStream`, które mogą być używane tylko w przypadku <xref:System.IO.FileStream> obiektu, który narusza tę regułę. Druga metoda `ManipulateAnyStream`, spełnia reguły zastępując <xref:System.IO.FileStream> parametru za pomocą <xref:System.IO.Stream>.  
  
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1059: Elementy członkowskie nie powinny ujawniać niektórych typów konkretnych](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)