---
title: "CA2216: Typy usuwalne powinny deklarować finalizator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 087df27916465b3ddba0b8e2c92bacf89dd33c1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Typy usuwalne powinny deklarować finalizator
|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName>i ma pola, które sugeruje korzystania z zasobów niezarządzanych, nie implementuje finalizator, zgodnie z opisem w <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Opis reguły  
 Naruszenie tej reguły jest zgłaszany, gdy jednorazowe typ zawiera pola z następujących typów:  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, implementuje finalizator, który wywołuje Twojej <xref:System.IDisposable.Dispose%2A> metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli typ nie implementuje <xref:System.IDisposable> na potrzeby zwalniania niezarządzanych zasobów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza tę regułę.  
  
 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2115: Wywołaj GC. KeepAlive, gdy używasz zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: Wywołaj GC. Metodę SuppressFinalize poprawnie](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: Typy, które posiadają natywne zasoby powinny być usuwalne](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)