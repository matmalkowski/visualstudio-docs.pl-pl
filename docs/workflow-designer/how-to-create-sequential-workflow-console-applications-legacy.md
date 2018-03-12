---
title: "Porady: tworzenie aplikacji konsoli sekwencyjnego przepływu pracy (starsze) | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 211c750dd0baa1dad0a365310b3636c0d0922882
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Porady: tworzenie aplikacji konsoli sekwencyjnego przepływu pracy (starsze)
Wykonaj następujące kroki, aby utworzyć projekt aplikacji konsoli usługi sekwencyjnego przepływu pracy przy użyciu starszej wersji projektanta przepływów pracy Windows udostępniane przez [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-sequential-workflow-console-application"></a>Do tworzenia aplikacji konsolowej sekwencyjnego przepływu pracy

1.  Uruchom program Visual Studio.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  Wybierz opcję **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okno, aby uzyskać dostępu do starszych projektanta.

    > [!NOTE]
    > Domyślna opcja [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacje, które odnoszą się do [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] i nie używa starszej wersji projektanta.

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