---
title: "Porady: Dodawanie nowego elementu do projektu przepływu pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e2031f084b11f9879fd94f5d2e454e0966ed3787
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Porady: Dodawanie nowego elementu do projektu przepływu pracy
Po utworzeniu projektu przepływu pracy, można dodać działania przepływu pracy, projektantów i innych znanych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elementy do projektu.  
  
 W poniższej tabeli wymieniono [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] elementy dodane do projektu przepływu pracy.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|Działanie|Działanie składa się z innymi działaniami. Wybranie tego elementu dodaje tego samego pliku XAML do projektu, jak można uzyskać po wybraniu **Biblioteka działań** szablonu dla nowego projektu. [!INCLUDE[crabout](../test/includes/crabout_md.md)]na tej procedury, zobacz [porady: Tworzenie biblioteki działań](../workflow-designer/how-to-create-an-activity-library.md).|  
|Projektant działań|Projektant umożliwiający dostosowanie środowiska czasu projektowania działania. Wybranie tego elementu dodaje tych samych plików do projektu, jak można uzyskać po wybraniu **Biblioteka Projektant działań** szablonu dla nowego projektu. [!INCLUDE[crabout](../test/includes/crabout_md.md)]na tej procedury, zobacz [porady: Tworzenie biblioteki projektanta działania](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Działania związane z kodem|Działanie z logiką wykonywania zapisaną w kodzie. Pliku kodu źródłowego za pomocą zastąpienia z <xref:System.Activities.CodeActivity.Execute%2A> metoda została już wygenerowana automatycznie.|  
|Usługi przepływu pracy WCF|A [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] usługi utworzone przy użyciu działań przepływu pracy. Wybranie tego elementu dodaje tych samych plików do projektu, jak można uzyskać po wybraniu **aplikacji usługi przepływu pracy WCF** szablonu dla nowego projektu. [!INCLUDE[crabout](../test/includes/crabout_md.md)]na tej procedury, zobacz [porady: tworzenie aplikacji usługi przepływu pracy WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element...** .  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2.  W **zainstalowane szablony** okienku wybierz **przepływu pracy** grupy.  
  
3.  Wybierz jedną z czterech elementów. W poprzedniej tabeli wymieniono dostępne opcje.  
  
4.  Wpisz odpowiednią nazwę elementu w **nazwa** u dołu okna dialogowego.  
  
5.  Kliknij przycisk **Dodaj** można dodać elementu do bieżącego projektu przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)