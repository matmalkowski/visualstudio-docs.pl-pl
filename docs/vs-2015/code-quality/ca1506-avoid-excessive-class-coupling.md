---
title: 'CA1506: Unikaj nadmiernego sprzężenia klas | Dokumentacja firmy Microsoft'
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
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1611c1861b9961fd953d63cb4d45a5c4e3b276db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673556"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Unikaj nadmiernego sprzężenia klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1506: Unikaj nadmiernego sprzężenia klas](https://docs.microsoft.com/visualstudio/code-quality/ca1506-avoid-excessive-class-coupling).  
  
Element TypeName | AvoidExcessiveClassCoupling |  
| CheckId | CA1506 |  
| Kategoria | Microsoft.Maintainability|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Typ lub metoda jest sprzężona z wielu innych typów.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda.  
  
 Typy i metody, które mają wysokim stopniu sprzężenia klas mogą być trudne w utrzymaniu. Jest dobrą praktyką, typów i metod, które wykazują sprzężenia niski i wysoki spójności.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać problem to naruszenie, spróbuj zmienić układ typu lub metody w celu zmniejszenia liczby typów, do których jest sprzężona.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Wyklucz to ostrzeżenie, gdy typ lub metoda jest nadal uważana za łatwego w utrzymaniu pomimo dużej liczby zależności od innych typów.  
  
## <a name="see-also"></a>Zobacz też  
 [Utrzymanie — ostrzeżenia](../code-quality/maintainability-warnings.md)   
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



