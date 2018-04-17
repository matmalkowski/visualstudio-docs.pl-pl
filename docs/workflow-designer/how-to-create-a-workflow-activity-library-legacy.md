---
title: 'Porady: Tworzenie biblioteki działań przepływów pracy (starsze) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18fa570f732f71336ce5a2f5e8e56d1185366afa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Porady: Tworzenie biblioteki działań przepływów pracy (starsze)

Wykonaj następujące kroki, aby utworzyć projekt biblioteki działań przepływów pracy za pomocą starszej wersji projektanta przepływów pracy Windows udostępniane przez [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-workflow-activity-library-project"></a>Aby utworzyć projekt biblioteki działania przepływu pracy

1.  Uruchom program Visual Studio.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  Wybierz opcję **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okno, aby uzyskać dostępu do starszych projektanta.

    > [!NOTE]
    > Domyślna opcja [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacje, które odnoszą się do [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] i nie używa starszej wersji projektanta.

4.  W **typów projektów** okienku, wybierz pozycję Visual C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz **przepływu pracy**.

5.  W **szablony** okienku wybierz **biblioteki działań przepływów pracy**.

6.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

7.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

     Katalog rozwiązania utworzony dla projektu, zaznacz **Utwórz katalog rozwiązania** pole wyboru, a następnie wprowadź nazwę w **Nazwa rozwiązania** pole.

8.  Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Używanie starszej wersji projektanta działań](../workflow-designer/using-the-legacy-activity-designer.md)
- [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)
- [Tworzenie działań przepływu pracy](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)
- [Działań w systemie Windows Workflow Foundation](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)