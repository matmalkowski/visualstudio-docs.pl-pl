---
title: "Porady: tworzenie aplikacji Konsolowej przepływu pracy | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 94058f15911ed0f72023ea4cd10c9a935f13ba44
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-a-workflow-console-application"></a>Porady: tworzenie aplikacji Konsolowej przepływu pracy
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Służy do tworzenia przepływów pracy dla wykonywania systemu lub człowieka procesów. Projektant przepływu pracy systemu Windows zapewnia powierzchnię projektu do tworzenia tych przepływów pracy. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Może służyć do tworzenia przepływów pracy za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub może być zintegrowane do innych aplikacji, które rehost projektanta.

 W tym temacie opisano sposób użycia [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] do tworzenia przepływu pracy w aplikacji konsoli.

### <a name="to-create-a-workflow-console-application"></a>Do tworzenia aplikacji konsolowej przepływu pracy

1.  Uruchom [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu...** .

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  W **zainstalowane szablony** okienku wybierz **przepływu pracy** z jednej **Visual C#** lub **Visual Basic** grupowania, w zależności od sieci język preferencji.

4.  W środkowym okienku wybierz **Aplikacja konsoli przepływu pracy**.

5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

7.  W **rozwiązania** wprowadź nazwę dla nowego rozwiązania. Kliknij przycisk **OK** do tworzenia aplikacji.

    > [!NOTE]
    > Jeśli chcesz dodać Aplikacja konsoli przepływu pracy do istniejącego rozwiązania, otworzyć tego rozwiązania w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie  **Nowy projekt...**  otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.

8.  Szablon projektu służy do tworzenia definicji przepływu pracy w języku XAML i definicji aplikacji konsoli jest w kodzie źródłowym. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Otwiera i wyświetla obszar roboczy utworzony przepływ pracy.

9. Utworzenie przepływu pracy, przeciągnij działania lub innych elementów przepływu pracy z **przybornika** na powierzchnię projektu w przepływie pracy.

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)