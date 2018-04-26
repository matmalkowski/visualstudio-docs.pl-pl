---
title: 'Projektant przepływu pracy — porady: tworzenie aplikacji Konsolowej przepływu pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-console-application"></a>Porady: tworzenie aplikacji Konsolowej przepływu pracy

Windows Workflow Foundation (WF) służy do tworzenia przepływów pracy dla wykonywania systemu lub człowieka procesów. Projektant przepływu pracy systemu Windows zapewnia powierzchnię projektu do tworzenia tych przepływów pracy. Projektanta przepływów pracy można używać do tworzenia przepływów pracy z poziomu programu Visual Studio lub może być zintegrowany inne aplikacje, które rehost projektanta.

W tym temacie opisano, jak za pomocą projektanta przepływów pracy programu Visual Studio 2010 tworzenia przepływu pracy w aplikacji konsoli.

## <a name="to-create-a-workflow-console-application"></a>Do tworzenia aplikacji konsolowej przepływu pracy

1.  Uruchom program Visual Studio 2010.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  W **zainstalowane szablony** okienku wybierz **przepływu pracy** z jednej **Visual C#** lub **Visual Basic** grupowania, w zależności od sieci język preferencji.

4.  W środkowym okienku wybierz **Aplikacja konsoli przepływu pracy**.

5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

7.  W **rozwiązania** wprowadź nazwę dla nowego rozwiązania. Kliknij przycisk **OK** do tworzenia aplikacji.

    > [!NOTE]
    > Jeśli chcesz dodać Aplikacja konsoli przepływu pracy do istniejącego rozwiązania, otworzyć tego rozwiązania w programie Visual Studio 2010, kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie  **Nowy projekt** otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.

8.  Szablon projektu służy do tworzenia definicji przepływu pracy w języku XAML i definicji aplikacji konsoli jest w kodzie źródłowym. Projektant przepływu pracy otwiera i wyświetla obszar roboczy dla przepływu pracy, który został utworzony.

9. Utworzenie przepływu pracy, przeciągnij działania lub innych elementów przepływu pracy z **przybornika** na powierzchnię projektu w przepływie pracy.

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)