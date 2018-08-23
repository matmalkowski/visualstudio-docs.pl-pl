---
title: 'CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych | Dokumentacja firmy Microsoft'
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
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1e5c063cb6a7fff98ed3d89eb425b2997028d1ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683528"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Nie deklaruj wirtualnych elementów członkowskich w typach zapieczętowanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1048: nie deklaruj wirtualnych składowych w typach zapieczętowanych](https://docs.microsoft.com/visualstudio/code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types).  
  
Element TypeName | DoNotDeclareVirtualMembersInSealedTypes |  
| CheckId | CA1048 |  
| Kategoria | Microsoft.Design|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Typ publiczny jest zapieczętowany i deklaruje metodę, która jest zarówno `virtual` (`Overridable` w języku Visual Basic) i nie jest final. Ta zasada nie raportuje naruszenia typami delegatów, które muszą korzystać z tego wzoru.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody wirtualne są zadeklarowane w typach tak, aby typy dziedziczące mogły zmieniać implementację metod wirtualnych. Zgodnie z definicją nie może dziedziczyć od typu zapieczętowanego podjęcia metoda wirtualna w typie zapieczętowanym ta nie ma znaczenia.  
  
 Kompilatory języków Visual Basic .NET i języka C# nie zezwalają na typy narusza tę regułę.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, wprowadzić metody na niewirtualną lub zmień typ dziedziczone.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie typ w jego bieżącym stanie może spowodować problemy z konserwacji i nie zapewnia żadnych korzyści.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje typ, który narusza tę regułę.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]



