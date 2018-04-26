---
title: 'Projektant przepływu pracy — porady: Tworzenie biblioteki projektanta działań'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d05ddb48e88627f4b7ab4112c164b5129ddba910
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-activity-designer-library"></a>Porady: Tworzenie biblioteki projektanta działań
Projektantów działań niestandardowych umożliwiają tworzenie interfejsu użytkownika dla standardowej lub działania niestandardowego. Kontrolowanie złożoności interfejsu użytkownika i mieć możliwość tworzenia więcej niż jeden Projektant działań dla działania. W tym scenariuszu pozwala utworzyć Designer, które są dostosowane do wielu odbiorców.

## <a name="to-create-an-activity-designer-library"></a>Aby utworzyć biblioteki projektanta działań

1.  Uruchom program Visual Studio 2010.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu** można otworzyć **nowy projekt** okno dialogowe.

3.  W **typów projektów** okienku wybierz **przepływu pracy** z jednej **Visual C#** lub **Visual Basic** grupowania w zależności od preferowany język.

4.  W **szablony** okienku wybierz **Biblioteka Projektant działań**.

5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

7.  W **rozwiązania** polu, wpisz nazwę opisową dla rozwiązania, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli chcesz dodać Aplikacja konsoli przepływu pracy do istniejącego rozwiązania, otworzyć tego rozwiązania w programie Visual Studio 2010, kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, a następnie **Nowy projekt** otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.

8.  Szablon projektu tworzy definicji działania projektanta XAML i kodem plik implementacji w kodzie źródłowym. Projektanta przepływów pracy programu Windows otwiera i wyświetla obszaru roboczego dla programu Projektant działań.

9. Przeciągnij Windows Presentation Foundation (WPF) formantów **przybornika** na powierzchnię projektu z nich korzystać w Projektancie Twoje działania niestandardowego.  Na przykład sposobu wdrażania Projektant działań niestandardowych, zobacz [porady: Tworzenie niestandardowego Projektant działań](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

    > [!WARNING]
    > Projektanci niestandardowych działań może służyć do niestandardowych działań, jak również podobnie jak w przypadku domyślnej 4activities .NET Framework.

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)