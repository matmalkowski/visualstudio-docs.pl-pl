---
title: 'Projektant przepływu pracy — porady: Tworzenie biblioteki działań przepływów pracy (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 432766e60ee1384db0f8cd5bad1f369e80ddd20a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Porady: Tworzenie biblioteki działań przepływów pracy (starsze)

Wykonaj następujące kroki, aby utworzyć projekt biblioteki działań przepływów pracy za pomocą starszego projektanta przepływów pracy Windows podane przez Visual Studio 2010. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

## <a name="to-create-a-workflow-activity-library-project"></a>Aby utworzyć projekt biblioteki działania przepływu pracy

1.  Uruchom program Visual Studio.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  Wybierz opcję **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okno, aby uzyskać dostępu do starszych projektanta.

    > [!NOTE]
    > Jest domyślną opcją w Visual Studio 2010 **.NET Framework 4**. Ta opcja jest używana do tworzenia aplikacji systemu Windows Workflow Foundation (WF) przeznaczonych dla platformy .NET Framework 4 i nie używa starszej wersji projektanta.

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