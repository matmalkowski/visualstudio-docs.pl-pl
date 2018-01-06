---
title: "Porady: Użyj nadrzędnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 95e79ab384c6311aa17f2592b514d62b899b8b6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-breadcrumb-navigation"></a>Porady: Użyj nadrzędnych
Istnieją trzy podstawowe sposoby zmianę zestawu działań, które są wyświetlane w [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]:  
  
1.  Kliknij dwukrotnie, aby przejść do szczegółów celu działania podrzędnego.  
  
2.  Kliknij przycisk paska stron nadrzędnych można przejść do działanie nadrzędne.  
  
3.  Rozwiń lub Zwiń działań w miejscu.  
  
### <a name="using-breadcrumb-navigation"></a>Za pomocą stron nadrzędnych  
  
1.  Kliknij dwukrotnie działanie z [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] do działania głównego zmiany klikniętej działania. Działanie klikniętej jest następnie pełni rozwinięty w katalogu głównym i jego obiektów nadrzędnych są wyświetlane na pasku stron nadrzędnych. Jest to czasem nazywane przechodzenia na wyższy poziom do lub z działania.  
  
2.  Aby przejść do elementu nadrzędnego bieżącego działania głównego, kliknij działanie na pasku stron nadrzędnych.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Rozwijanie lub zwijanie działania w miejscu  
  
1.  Kliknij cudzysłów ostrokątny w działaniu rozwija lub zwija działania w miejscu.  
  
2.  Po zmianie stanu rozszerzenia stanu po kliknięciu przycisku Nowy stan rozszerzenia jest zapisany w języku XAML.  
  
    > [!WARNING]
    >  Nie wszystkie działania można rozszerzać w miejscu. Istnieją dwa przypadki, gdy działanie nie może być rozwinięty w miejscu: albo element nadrzędny działania nie zezwala na jego elementów podrzędnych do wyodrębnienia w miejscu, (na przykład działania w elemencie Schemat blokowy nie może być rozwinięty w miejscu), lub nie zezwala na siebie Projektant działań można rozwinąć w miejscu. Mimo że żaden z projektantami działań objętych [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] ostatnie zachowują, niektóre działania niestandardowe mogą działać to zachowanie.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Wszystkie rozwijanie lub zwijanie wszystkich działań  
  
1.  Użyj **Rozwiń wszystkie** i **Zwiń wszystkie** przycisków w interfejsie użytkownika, aby rozwinąć lub zwinąć wszystkie działania w katalogu głównym bieżącej stron nadrzędnych. Należy pamiętać, że wszystkie rozwijanie i zwijanie, wszystkie są globalne stanów. Oznacza to, że podczas działania głównego przy użyciu nadrzędnych, rozwiń wszystkie zmiany lub Zwiń wszystkie stan będzie się powtarzał dopiero po kliknięciu przycisku **przywrócić**.  
  
2.  Po zostały zastosowane wszystkie rozwiń lub Zwiń wszystkie stanu, możesz kliknąć **przywrócić** przycisku, który pojawia się, aby powrócić do przeglądania stanu wcześniej zastosowane do każdego działania.  
  
    > [!WARNING]
    >  Jeśli działanie, takich jak <xref:System.Activities.Statements.Flowchart>, zrezygnowała z rozwiń w miejscu, funkcje związane z **Rozwiń wszystko** i **Zwiń wszystkie** przycisków jest wyłączona na **schematu blokowego**  projektanta. [!INCLUDE[crabout](../test/includes/crabout_md.md)]**schemat blokowy** projektanta, zobacz [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) tematu.  
  
    > [!WARNING]
    >  Rozwiń wszystko również ma wpływ specjalne **przełącznika** i **TryCatch** projektantów działań. Po kliknięciu **Rozwiń wszystkie**, są wyświetlane wszystkie przypadki przełącznika i wszystkie bloki try/catch/finally. Kliknięcie przycisku **przywrócić** lub **Zwiń wszystkie** zwraca te projektantów ich stan domyślny, w którym można kliknąć poszczególne przypadku/zablokowanych, aby wyświetlić jego zawartość.