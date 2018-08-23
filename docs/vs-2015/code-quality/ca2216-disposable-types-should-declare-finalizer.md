---
title: 'CA2216: Typy usuwalne powinny deklarować finalizator | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e7cdf0d5b120f2cdeda206187a144dbd37058d88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42671652"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Typy usuwalne powinny deklarować finalizator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2216: typy usuwalne powinny deklarować finalizator](https://docs.microsoft.com/visualstudio/code-quality/ca2216-disposable-types-should-declare-finalizer).  
  
Element TypeName | DisposableTypesShouldDeclareFinalizer |  
| CheckId | CA2216 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName>i zawiera pola, które sugerują wykorzystanie zasobów niezarządzanych, nie implementuje finalizatora, zgodnie z opisem w <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Opis reguły  
 Naruszenie tej zasady jest zgłaszany, gdy możliwe do rozporządzania typ zawiera pola z następujących typów:  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy zaimplementować finalizator, który wywołuje swoje <xref:System.IDisposable.Dispose%2A> metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Bezpiecznie Pomijaj ostrzeżeń dla tej reguły, jeśli typ nie implementuje <xref:System.IDisposable> na potrzeby zwalniania niezarządzanych zasobów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje typ, który narusza tę regułę.  
  
 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: Wywołaj poprawnie metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: Typy z zasobami natywnymi powinny być możliwe do likwidacji](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Wzorzec Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



