---
title: "CA2132: Konstruktory domyślne muszą być co najmniej tak ważne, jak podstawowe konstruktory domyślne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 752103825a25c4352ccc21730b8d2b7265f8f41b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne, jak podstawowe konstruktory domyślne
|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
> [!NOTE]
>  To ostrzeżenie jest stosowana tylko do kodu, który działa środowisko CoreCLR (wersja środowiska CLR, która jest specyficzna dla aplikacji sieci Silverlight Web).  
  
## <a name="cause"></a>Przyczyna  
 Atrybut przezroczystości domyślnego konstruktora klasy pochodnej nie jest tak ważne, jak przezroczystość klasy podstawowej.  
  
## <a name="rule-description"></a>Opis reguły  
 Typy i składniki, które mają <xref:System.Security.SecurityCriticalAttribute> nie można użyć przez kod aplikacji Silverlight. Krytyczne dla bezpieczeństwa typy i składowe mogą być używane tylko przez zaufany kod w środowisku .NET Framework dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical.  
  
 Dla kodu platformy środowisko CoreCLR Jeśli typ podstawowy ma konstruktora domyślnego nieprzezroczystych public lub protected następnie Typ pochodny musi przestrzegać reguły dziedziczenia konstruktora domyślnego. Typ pochodny również musi mieć konstruktora domyślnego i tego konstruktora musi wynosić co najmniej jako krytyczne domyślnego konstruktora typu podstawowego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie, Usuń typ lub nie pochodzi od typu nieprzezroczystych zabezpieczeń.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły. Naruszeń tej reguły przez kod aplikacji spowoduje środowisko CoreCLR odmowy można załadować typu z <xref:System.TypeLoadException>.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### <a name="comments"></a>Komentarze