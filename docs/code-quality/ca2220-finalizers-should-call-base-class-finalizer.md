---
title: "CA2220: Finalizatory powinny wywoływać finalizator klasy podstawowej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 46427cffe64c6c81e0f262520a61c1b1ea01fff8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizatory powinny wywoływać finalizatory klasy bazowej
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ, który zastępuje <xref:System.Object.Finalize%2A?displayProperty=fullName> nie wywołuje <xref:System.Object.Finalize%2A> metody w klasie podstawowej.  
  
## <a name="rule-description"></a>Opis reguły  
 Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zapewnić, typów należy wywołać klasy podstawowej <xref:System.Object.Finalize%2A> metodę z własnych <xref:System.Object.Finalize%2A> metody. Kompilator języka C#, które automatycznie dodaje wywołanie finalizator klasy podstawowej.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, wywołanie typu podstawowego <xref:System.Object.Finalize%2A> metody z Twojej <xref:System.Object.Finalize%2A> metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Niektóre kompilatory, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego Wstawianie wywołania do finalizator typu podstawowego na język pośredni firmy Microsoft (MSIL). Jeśli ostrzeżenie od tej reguły jest zgłaszany, kompilujący nie wstawia wywołania i należy go dodać do kodu.  
  
## <a name="example"></a>Przykład  
 Typ przedstawiono w poniższym przykładzie w języku Visual Basic `TypeB` poprawnie wywołującym <xref:System.Object.Finalize%2A> metody w klasie podstawowej.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)