---
title: "CA1824: Oznacz zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6c9d4da3becaa6831f30a5cc6c72d1f0b3b70eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Oznacz zestawy za pomocą NeutralResourcesLanguageAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Zestaw zawiera **ResX**— na podstawie zasobów, ale nie ma <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> zastosować dla niego.  
  
## <a name="rule-description"></a>Opis reguły  
 **NeutralResourcesLanguage** atrybut informuje **ResourceManager** języka, który został użyty do wyświetlenia zasobów kultury neutralnej dla zestawu. Podczas wyszukiwania zasobów w tej samej kulturze jako język neutralne zasoby **ResourceManager** automatycznie używa zasobów, które znajdują się w zestawie głównym. Robi to zamiast wyszukiwania zestawu satelickiego, który ma bieżącej kultury interfejsu użytkownika dla bieżącego wątku. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy.  
  
## <a name="fixing-violations"></a>Ustalania naruszeń  
 Aby rozwiązać naruszenie tej reguły, Dodaj atrybut do zestawu i określ język zasobów kultury neutralnej.  
  
## <a name="specifying-the-language"></a>Określanie języka  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Określa język zasobu kultury neutralnej  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.  
  
2.  Na pasku nawigacyjnym po lewej stronie wybierz **aplikacji**, a następnie kliknij przycisk **informacji o zestawie**.  
  
3.  W **informacji o zestawie** oknie dialogowym Wybierz język z **języka Neutral** listy rozwijanej.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest dozwolone w celu pominięcia ostrzeżenia od tej reguły. Jednak może zmniejszyć wydajność uruchamiania.