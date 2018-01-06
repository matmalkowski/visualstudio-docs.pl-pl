---
title: "Porady: Tworzenie biblioteki projektanta działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e488d7daceb5bbebae318e674fdffa9256c53eeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-activity-designer-library"></a>Porady: Tworzenie biblioteki projektanta działań
Projektantów działań niestandardowych umożliwiają tworzenie interfejsu użytkownika dla standardowej lub działania niestandardowego. Kontrolowanie złożoności interfejsu użytkownika i mieć możliwość tworzenia więcej niż jeden Projektant działań dla działania. W tym scenariuszu pozwala utworzyć Designer, które są dostosowane do wielu odbiorców.  
  
### <a name="to-create-an-activity-designer-library"></a>Aby utworzyć biblioteki projektanta działań  
  
1.  Uruchom [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu...**  otworzyć **nowy projekt** okno dialogowe.  
  
3.  W **typów projektów** okienku wybierz **przepływu pracy** z jednej **Visual C#** lub **Visual Basic** grupowania w zależności od preferowany język.  
  
4.  W **szablony** okienku wybierz **Biblioteka Projektant działań**.  
  
5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.  
  
6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.  
  
7.  W **rozwiązania** polu, wpisz nazwę opisową dla rozwiązania, a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]
    >  Jeśli chcesz dodać Aplikacja konsoli przepływu pracy do istniejącego rozwiązania, otworzyć tego rozwiązania w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, a następnie **Nowy projekt...**  otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.  
  
8.  Szablon projektu tworzy definicji działania projektanta XAML i kodem plik implementacji w kodzie źródłowym. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] Otwiera i wyświetla obszaru roboczego dla programu Projektant działań.  
  
9. Przeciągnij [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] formantów **przybornika** na powierzchnię projektu z nich korzystać w Projektancie Twoje działania niestandardowego.  Na przykład sposobu wdrażania Projektant działań niestandardowych, zobacz [porady: Tworzenie niestandardowego Projektant działań](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).  
  
    > [!WARNING]
    >  Projektanci działań niestandardowych mogą służyć do niestandardowych działań, jak również podobnie jak w przypadku domyślnej [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]działań.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)