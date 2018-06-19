---
title: 'Projektant przepływu pracy — porady: tworzenie aplikacji konsoli sekwencyjnego przepływu pracy (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb4e048fdf8eb8fee541f84656a29427b5a07a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973222"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Porady: tworzenie aplikacji konsoli sekwencyjnego przepływu pracy (starsze)

Wykonaj następujące kroki, aby utworzyć projekt aplikacji konsoli usługi sekwencyjnego przepływu pracy za pomocą starszego projektanta przepływów pracy Windows podane przez Visual Studio 2010. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

## <a name="to-create-a-sequential-workflow-console-application"></a>Do tworzenia aplikacji konsolowej sekwencyjnego przepływu pracy

1.  Uruchom program Visual Studio.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  Wybierz opcję **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okno, aby uzyskać dostępu do starszych projektanta.

    > [!NOTE]
    > Jest domyślną opcją w Visual Studio 2010 **.NET Framework 4**. Ta opcja jest używana do tworzenia aplikacji systemu Windows Workflow Foundation (WF) przeznaczonych dla platformy .NET Framework 4 i nie używa starszej wersji projektanta.

4.  W **typów projektów** okienku, wybierz projekty Visual C# lub projekty Visual Basic (w obszarze **inne języki**), a następnie wybierz **przepływu pracy**.

5.  W **szablony** okienku wybierz **sekwencyjnych Aplikacja konsoli przepływu pracy**.

6.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

7.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

     Projektant formularzy systemu Windows otwiera i wyświetla Form1 projektu, który został utworzony.

8.  Kliknij przycisk **OK**.

     Projektant przepływu pracy otwiera i wyświetla powierzchni projektu przepływu pracy sekwencyjnego przepływu pracy, który został utworzony.

9. Przeciągnij działanie z **przybornika** na powierzchnię projektu w **Upuść działanie** wyznaczony obszaru.

## <a name="see-also"></a>Zobacz także

- [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Tworzenie przepływów pracy](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)