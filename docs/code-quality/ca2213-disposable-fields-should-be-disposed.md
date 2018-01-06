---
title: "CA2213: Pola usuwalne powinny zostać usunięte | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4da3299e839be08a5ff11792aa2c80a364349b18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola usuwalne powinny zostać usunięte
|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pola, które są typów, które również implementują <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metody pola nie jest wywoływany przez <xref:System.IDisposable.Dispose%2A> metody typ deklarujący.  
  
## <a name="rule-description"></a>Opis reguły  
 Typ jest odpowiedzialny za usuwanie wszystkich jej zasobów niezarządzanych; jest to osiągane przez wdrożenie <xref:System.IDisposable>. Ta reguła sprawdza, czy typ jednorazowe `T` deklaruje on pole `F` czyli wystąpienia typu jednorazowe `FT`. Dla każdego pola `F`, reguła próbuje zlokalizować wywołania `FT.Dispose`. Reguły będzie przeszukiwana metody wywoływane przez `T.Dispose`, a jeden poziom w dół (metody wywoływane przez metody wywołane `FT.Dispose`).  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, należy wywołać <xref:System.IDisposable.Dispose%2A> w polach, które są typów implementujących <xref:System.IDisposable> Jeśli jest odpowiedzialny za przydzielanie i zwalniania niezarządzanych zasobów posiadanych przez pole.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli nie jesteś odpowiedzialny do zwolnienia zasobu posiadanych przez pole lub wywołanie <xref:System.IDisposable.Dispose%2A> występuje na poziomie wywoływania głębiej niż sprawdza reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typu `TypeA` implementującej <xref:System.IDisposable> (`FT` w dyskusji previosu).  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typu `TypeB` co narusza tę regułę przez zadeklarowanie pola `aFieldOfADisposableType` (`F` w poprzedniej dyskusji) jako możliwe do rozporządzania typ (`TypeA`) i nie wywołuje metody <xref:System.IDisposable.Dispose%2A> w tym polu. `TypeB`odpowiada `T` w poprzedniej dyskusji.  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)