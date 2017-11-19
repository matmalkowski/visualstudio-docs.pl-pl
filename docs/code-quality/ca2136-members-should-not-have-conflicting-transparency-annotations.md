---
title: "CA2136: Elementy członkowskie nie powinny mieć skonfliktowanych adnotacji przezroczystości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 350504d6e49351e96aa1c986ddf08893dc490d69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Elementy członkowskie nie powinny mieć skonfliktowanych adnotacji przezroczystości
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Ta zasada generowane, gdy członek typu jest oznaczony atrybutem <xref:System.Security> atrybutu zabezpieczeń, który ma inną przezroczystość niż wartość atrybutu zabezpieczeń kontenera elementu członkowskiego.  
  
## <a name="rule-description"></a>Opis reguły  
 Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu z większym zakresem mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład klasa, która jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu nie może zawierać metodę, która jest oznaczony atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać to naruszenie, usuń atrybut zabezpieczeń z elementu kodu, który ma niższy zakres, lub zmień jego atrybutu, aby była taka sama jak zawierającego element kodu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie metoda jest oznaczona atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu i jest elementem członkowskim klasy, która jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu. Atrybut zabezpieczeń bezpiecznych powinien zostać usunięty.  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]