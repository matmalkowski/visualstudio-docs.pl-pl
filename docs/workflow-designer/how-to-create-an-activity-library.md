---
title: 'Porady: Tworzenie biblioteki działań | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: faa7c593d27474c0980e7c7df7bf932bd2d5431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-activity-library"></a>Porady: Tworzenie biblioteki działań
Działania niestandardowe są używane do model procesów biznesowych konkretnego w przepływie pracy. Szablon biblioteki działań w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] została przekazana umożliwiają tworzenie takich działań niestandardowych sposób wizualny przy użyciu projektanta przepływów pracy systemu Windows.

### <a name="to-create-a-workflow-activity-library"></a>Aby utworzyć biblioteki działań przepływów pracy

1.  Uruchom [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu...** .

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  W **typów projektów** okienku wybierz **przepływu pracy** z jednej **Visual C#** projektów lub **Visual Basic** grupowania w zależności od sieci Preferencje językowe.

4.  W **szablony** okienku wybierz **Biblioteka działań**.

5.  W **nazwa** okno, wpisz opisową nazwę projektu, aby ułatwić jego późniejszą identyfikację.

6.  W **lokalizacji** , wpisz w katalogu, w którym chcesz zapisać projekt lub kliknij przycisk **Przeglądaj** można przejść do niego.

7.  W **rozwiązania** polu, wpisz nazwę opisową dla rozwiązania, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli chcesz dodać Aplikacja konsoli przepływu pracy do istniejącego rozwiązania, otworzyć tego rozwiązania w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie **Nowy projekt...** otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.

8.  Szablon projektu tworzy definicji działania w języku XAML. Projektant przepływu pracy systemu Windows otwiera i wyświetla obszar roboczy dla działania niestandardowego.

9. Przeciągnij działanie z **przybornika** na powierzchnię projektu, aby objąć działania niestandardowego.

    > [!CAUTION]
    > Tylko jeden element podrzędny działania są dozwolone w treści działania niestandardowego; jednak tego działania podrzędnego może być złożonego działania, takie jak <xref:System.Activities.Statements.Sequence> działania lub <xref:System.Activities.Statements.Flowchart> działania.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie działania](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)