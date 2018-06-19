---
title: 'Projektant przepływu pracy — porady: Tworzenie biblioteki sekwencyjnego przepływu pracy (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ed341481ec3e82165a9f4cefd71eb362781d96c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970259"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Porady: Tworzenie biblioteki sekwencyjnego przepływu pracy (starsze)

Wykonaj następujące kroki, aby utworzyć projekt biblioteki sekwencyjnego przepływu pracy za pomocą starszego projektanta przepływów pracy Windows podane przez Visual Studio 2010. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

## <a name="to-create-a-sequential-workflow-library-project"></a>Aby utworzyć projekt biblioteki sekwencyjnego przepływu pracy

1.  Uruchom program Visual Studio.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  Wybierz opcję **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okno, aby uzyskać dostępu do starszych projektanta.

    > [!NOTE]
    > Jest domyślną opcją w Visual Studio 2010 **.NET Framework 4**. Ta opcja jest używana do tworzenia aplikacji systemu Windows Workflow Foundation (WF) przeznaczonych dla platformy .NET Framework 4 i nie używa starszej wersji projektanta.

4.  W **typów projektów** okienku, wybierz pozycję Visual C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz **przepływu pracy**.

5.  W **szablony** okienku wybierz **biblioteki sekwencyjnego przepływu pracy**.

6.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

7.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

     Katalog rozwiązania utworzony dla projektu, zaznacz **Utwórz katalog rozwiązania** pole wyboru, a następnie wprowadź nazwę w **Nazwa rozwiązania** pole.

8.  Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Style tworzenia przepływu pracy](http://msdn.microsoft.com/en-us/aacf4ec6-da05-4974-958a-974769dda739)