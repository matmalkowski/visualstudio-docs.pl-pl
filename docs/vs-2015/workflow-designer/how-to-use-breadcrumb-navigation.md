---
title: 'Porady: Korzystanie z nawigacji z linków do stron nadrzędnych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b59318b6aa3924578ea802ce33956e32f3f82ab6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682891"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Porady: Korzystanie z nawigacji z linków do stron nadrzędnych
Istnieją trzy podstawowe sposoby zmianę zestawu działań, które są wyświetlane w [!INCLUDE[wfd1](../includes/wfd1-md.md)]:  
  
1.  Kliknij dwukrotnie, aby przejść do działania podrzędnego.  
  
2.  Kliknij przycisk na pasku nawigacji, aby przejść do działania w elemencie nadrzędnym.  
  
3.  Rozwiń lub Zwiń działań w miejscu.  
  
### <a name="using-breadcrumb-navigation"></a>Przy użyciu nadrzędnych  
  
1.  Kliknij dwukrotnie działanie [!INCLUDE[wfd2](../includes/wfd2-md.md)] zmienić działania głównego kliknięto działania. Kliknięto działania jest w pełni rozszerzany w katalogu głównym i jego elementów nadrzędnych są wyświetlane na pasku nawigacji. Jest to czasem nazywane przechodzenia do szczegółów w lub poza nią działania.  
  
2.  Aby przejść do elementu nadrzędnego bieżącego działania głównego, kliknij działanie na pasku nawigacji.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Rozwijanie lub zwijanie działania w miejscu  
  
1.  Kliknij cudzysłów ostrokątny w działaniu rozwija lub zwija działania w miejscu.  
  
2.  Po zmianie stanu stanu rozszerzenia, klikając przycisk Nowy stan rozszerzenia jest zapisywany w XAML.  
  
    > [!WARNING]
    >  Nie wszystkie działania można rozszerzać w miejscu. Istnieją dwa przypadki, gdy działanie nie może być rozwinięty w miejscu: albo nadrzędnym działania nie zezwala na jego elementów podrzędnych do wyodrębnienia w miejscu, (na przykład działania w elemencie Schemat blokowy nie może być rozwinięty w miejscu), lub nie zezwala na się Projektant działań można rozwinąć w miejscu. Mimo że żaden z Projektanci działań objętych [!INCLUDE[wfd2](../includes/wfd2-md.md)] ostatnie zachowanie, niektóre działania niestandardowe mogą stosować tego zachowania.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Wszystkie rozwijanie lub zwijanie wszystkich działań  
  
1.  Użyj **Rozwiń wszystko** i **Zwiń wszystkie** przycisków w interfejsie użytkownika, aby rozwinąć lub zwinąć wszystkie działania w bieżącym katalogu głównym łączy do stron nadrzędnych. Należy zauważyć, że Rozwiń wszystko i Zwiń wszystko są globalne stanów. Oznacza to, że podczas zmiany działania głównego przy użyciu nadrzędnych, Rozwiń wszystko lub Zwiń wszystkie stany będzie się powtarzał dopóki nie klikniesz **przywrócić**.  
  
2.  Po zastosowaniu wszystkich rozwiń lub Zwiń wszystkie stany, możesz kliknąć **przywrócić** przycisk, który pojawia się, aby wrócić do wyszukiwania w stanie uprzednio zastosowane do każdego działania.  
  
    > [!WARNING]
    >  Jeśli działania, takie jak <xref:System.Activities.Statements.Flowchart>, wybrał poza rozwiń w miejscu, funkcje skojarzone z **Rozwiń wszystko** i **Zwiń wszystko** przycisków jest wyłączona na **schematu blokowego**  projektanta. [!INCLUDE[crabout](../includes/crabout-md.md)] **schemat blokowy** projektanta, zobacz [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) tematu.  
  
    > [!WARNING]
    >  Rozwiń wszystkie efekty specjalne zawiera również w **przełącznika** i **TryCatch** Projektanci działań. Po kliknięciu **Rozwiń wszystko**, zostaną wyświetlone wszystkie przypadki przełącznika i wszystkie bloki try/catch/finally. Klikając **przywrócić** lub **Zwiń wszystko** zwraca te projektantów do stanu domyślnego, z którego możesz kliknąć poszczególne przypadek/bloku, aby wyświetlić jego zawartość.