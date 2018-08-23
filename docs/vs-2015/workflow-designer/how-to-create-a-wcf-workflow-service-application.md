---
title: 'Porady: tworzenie aplikacji usługi przepływu pracy WCF | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 22531f171b07493f69bcf017634d9c6d299de844
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681231"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Porady: tworzenie aplikacji usługi przepływu pracy WCF
[!INCLUDE[indigo1](../includes/indigo1-md.md)] aplikacje usług przepływu pracy są usług łączności rozproszonych, które przekazywania wiadomości między klientami a same granice procesu. Implementację kontraktu usługi po stronie usługi odbywa się deklaratywne za pośrednictwem działań przepływu pracy w [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] w sposób analogiczny do usług przepływu pracy w starszej wersji w .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Do tworzenia aplikacji usługi przepływu pracy WCF  
  
1.  Rozpocznij [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Na **pliku** menu wskaż **New**, a następnie wybierz pozycję **projektu...** .  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku wybierz **WCF** lub **przepływu pracy** albo **Visual C#** lub **języka Visual Basic** grupowania w zależności od języka wybranego.  
  
4.  W środkowym okienku wybierz **aplikacja usługi przepływu pracy WCF**.  
  
5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić identyfikowanie.  
  
6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.  
  
7.  W **rozwiązania** wybierz albo utworzyć nowe rozwiązanie, a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]
    >  Jeśli chcesz dodać aplikację konsoli przepływu pracy do istniejącego rozwiązania, otwórz rozwiązanie w [!INCLUDE[vs2010](../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie  **Nowy projekt...** Aby otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.  
  
8.  Szablon projektu umożliwia utworzenie definicji usługi jako XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] Zostanie otwarty widok projektu za pomocą <xref:System.Activities.Statements.Sequence> działania, który zawiera zbiór <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie działania](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)