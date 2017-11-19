---
title: "CA1401: P-wywołuje nie powinny być widoczne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 707c78c6101c3cec554efe0f6957e4f08c059c3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes nie powinny być widoczne
|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|CheckId|CA1401|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Zawiera publiczne lub chronione metody w typie publicznego <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu (również implementowana przez `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Opis reguły  
 Metody, które są oznaczone ikoną z <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu (lub metod, które zdefiniowano przy użyciu `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) umożliwia dostęp do kodu niezarządzanego usług wywołania platformy. Takie metody nie powinny być udostępniane. Umieszczanie tych metod, prywatne lub wewnętrzne, należy upewnić się, że biblioteki nie może służyć do naruszenia zabezpieczeń, zezwalając wywołań dostęp do niezarządzanego interfejsów API, które ich nie można wywołać w przeciwnym razie wartość.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, zmień poziom dostępu do metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje metody, która narusza tę regułę.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]