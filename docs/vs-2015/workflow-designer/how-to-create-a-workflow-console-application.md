---
title: 'Porady: tworzenie aplikacji konsoli przepływu pracy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8a6b38f6026e7a9bba1e668f47a37b32feaa2b7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628483"
---
# <a name="how-to-create-a-workflow-console-application"></a>Porady: tworzenie aplikacji konsoli przepływu pracy
[!INCLUDE[wf](../includes/wf-md.md)] Umożliwia tworzenie przepływów pracy na potrzeby wykonywania systemu lub procesów przez ludzi. [!INCLUDE[wfd1](../includes/wfd1-md.md)] Udostępnia na powierzchnię projektową do tworzenia tych przepływów pracy. [!INCLUDE[wfd2](../includes/wfd2-md.md)] Może służyć do tworzenia przepływów pracy z poziomu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub może być zintegrowane do innych aplikacji, których ponowne hostowanie projektanta.  
  
 W tym temacie opisano sposób użycia [!INCLUDE[wfd2](../includes/wfd2-md.md)] w [!INCLUDE[vs2010](../includes/vs2010-md.md)] Tworzenie przepływu pracy w aplikacji konsoli.  
  
### <a name="to-create-a-workflow-console-application"></a>Do tworzenia aplikacji konsolowej przepływu pracy  
  
1.  Rozpocznij [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Na **pliku** menu wskaż **New**, a następnie wybierz pozycję **projektu...** .  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku wybierz **przepływu pracy** albo **Visual C#** lub **języka Visual Basic** grupowania, w zależności od usługi język preferencji.  
  
4.  W środkowym okienku wybierz **Aplikacja konsoli przepływu pracy**.  
  
5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić identyfikowanie.  
  
6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.  
  
7.  W **rozwiązania** wprowadź nazwę dla nowego rozwiązania. Kliknij przycisk **OK** do tworzenia aplikacji.  
  
    > [!NOTE]
    >  Jeśli chcesz dodać aplikację konsoli przepływu pracy do istniejącego rozwiązania, otwórz rozwiązanie w [!INCLUDE[vs2010](../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie  **Nowy projekt...** Aby otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.  
  
8.  Szablon projektu umożliwia utworzenie definicji przepływu pracy w XAML i definicji aplikacji konsoli jest w kodzie źródłowym. [!INCLUDE[wfd2](../includes/wfd2-md.md)] Otwiera i wyświetla obszar roboczy został utworzony przepływ pracy.  
  
9. Do tworzenia przepływu pracy, przeciągnij działania lub inne elementy przepływu pracy z **przybornika** do powierzchni projektowej w przepływie pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)