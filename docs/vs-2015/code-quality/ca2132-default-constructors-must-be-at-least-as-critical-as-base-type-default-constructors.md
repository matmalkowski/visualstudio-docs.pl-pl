---
title: 'CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego | Dokumentacja firmy Microsoft'
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
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 165e745d40e5a8a488a3f35bc1ad8b066b0ae523
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42696949"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne, jak podstawowe konstruktory domyślne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2132: konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego](https://docs.microsoft.com/visualstudio/code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors).  
  
Element TypeName | DefaultConstructorsMustHaveConsistentTransparency |  
| CheckId | CA2132 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
> [!NOTE]
>  To ostrzeżenie jest stosowane tylko do kodu, który jest uruchomiony w środowisku CoreCLR (wersja środowiska CLR, które są specyficzne dla aplikacji sieci Web w technologii Silverlight).  
  
## <a name="cause"></a>Przyczyna  
 Atrybut przezroczystości pod względem konstruktora domyślnego w klasie pochodnej nie jest tak krytyczny, jak przezroczystość klasy bazowej.  
  
## <a name="rule-description"></a>Opis reguły  
 Typy i elementy członkowskie, które mają <xref:System.Security.SecurityCriticalAttribute> nie może być używany przez kod aplikacji Silverlight. Krytyczne dla bezpieczeństwa typy i składowe mogą być używane tylko przez zaufany kod w środowisku .NET Framework dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical.  
  
 Dla kodu platformy CoreCLR Jeśli typ podstawowy ma publiczny lub chroniony nieprzezroczyste domyślnego konstruktora następnie Typ pochodny musi przestrzegać zasady dziedziczenia Konstruktor domyślny. Typ pochodny również musi mieć konstruktora domyślnego i tego konstruktora musi wynosić co najmniej jako krytyczne domyślny konstruktor obiektu typu podstawowego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie, Usuń typ lub pochodzi z zabezpieczenia-przejrzysty.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń od tej reguły. Naruszenie tej zasady przez kod aplikacji spowoduje CoreCLR odmowy można załadować typu o <xref:System.TypeLoadException>.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]  
  
### <a name="comments"></a>Komentarze



