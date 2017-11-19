---
title: "Porady: Tworzenie biblioteki przepływu pracy automatu stanów (starsze) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 47092f4f541f4f6e797617db3cf2d9c24741d282
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Porady: Tworzenie biblioteki przepływu pracy automatu stanów (starsze)
Wykonaj następujące kroki, aby utworzyć projekt biblioteki przepływu pracy stan komputera za pomocą starszego [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] dostarczonych przez [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>Aby utworzyć projekt biblioteki stanu komputera przepływu pracy  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  Wybierz opcję **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okno, aby uzyskać dostępu do starszych projektanta.  
  
    > [!NOTE]
    >  Domyślna opcja [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacje, które odnoszą się do [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] i nie używa starszej wersji projektanta.  
  
4.  W **typów projektów** okienku, wybierz pozycję Visual C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz **przepływu pracy**.  
  
5.  W **szablony** okienku wybierz **Biblioteka przepływu pracy automatu stanu**.  
  
6.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.  
  
7.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.  
  
     Katalog rozwiązania utworzony dla projektu, zaznacz **Utwórz katalog rozwiązania** pole wyboru, a następnie wprowadź nazwę w **Nazwa rozwiązania** pole.  
  
8.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektów przepływu pracy starsza wersja](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Przepływy pracy automatu stanów](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)