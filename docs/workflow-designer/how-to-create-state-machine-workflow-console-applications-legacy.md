---
title: 'Projektant przepływu pracy — porady: tworzenie aplikacji konsoli przepływu pracy automatu stanów (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 805b048a9e30f7a637e178d223b962259dadd926
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Porady: tworzenie aplikacji konsoli przepływu pracy automatu stanów (starsze)

Wykonaj następujące kroki, aby utworzyć projekt aplikacji Konsolowej przepływu pracy maszyny stanu za pomocą starszego projektanta przepływów pracy Windows podane przez Visual Studio 2010. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

## <a name="to-create-a-state-machine-application-project"></a>Aby utworzyć projekt aplikacji maszyny stanu

1.  Uruchom program Visual Studio.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  Wybierz opcję **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okno, aby uzyskać dostępu do starszych projektanta.

    > [!NOTE]
    > Jest domyślną opcją w Visual Studio 2010 **.NET Framework 4**. Ta opcja jest używana do tworzenia aplikacji systemu Windows Workflow Foundation (WF) przeznaczonych dla platformy .NET Framework 4 i nie używa starszej wersji projektanta.

4.  W **typów projektów** okienku, wybierz pozycję Visual C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz **przepływu pracy**.

5.  W **szablony** okienku wybierz **Aplikacja konsoli przepływu pracy maszyny stanu**.

6.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

7.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

     Katalog rozwiązania utworzony dla projektu, zaznacz **Utwórz katalog rozwiązania** pole wyboru, a następnie wprowadź nazwę w **Nazwa rozwiązania** pole.

8.  Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Instrukcje: Tworzenie biblioteki przepływu pracy automatu stanów (starsza wersja)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)