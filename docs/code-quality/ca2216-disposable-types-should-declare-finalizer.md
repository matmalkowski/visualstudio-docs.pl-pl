---
title: 'CA2216: Typy usuwalne powinny deklarować finalizator'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cccc628bf9561569dd92e06ca5440d6f47913fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918287"
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
 [CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Wywołaj poprawnie metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: Typy z zasobami natywnymi powinny być możliwe do likwidacji](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName> <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> <xref:System.Object.Finalize%2A?displayProperty=fullName> [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)