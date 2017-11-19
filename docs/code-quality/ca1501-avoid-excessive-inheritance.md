---
title: 'CA1501: Unikaj nadmiernego dziedziczenia | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c09a3367985613072944c5f74f0c708a149da15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Unikaj nadmiernego dziedziczenia
|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Kategoria|Microsoft.Maintainability|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia.  
  
## <a name="rule-description"></a>Opis reguły  
 Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. Ta zasada ogranicza analizy do hierarchii, w tym samym module.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, typ lub pochodzić od typu podstawowego, który jest mniej głębokie w hierarchii dziedziczenia wyeliminować niektóre typy podstawowe pośrednich.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły. Jednak kod może być bardziej trudne w utrzymaniu. Należy pamiętać, że w zależności od widoczność typów podstawowych rozpoznawania naruszeń tej reguły może utworzyć najważniejszych zmian. Na przykład usunięcie publicznej typów podstawowych jest istotne zmiany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza zasady.  
  
 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]