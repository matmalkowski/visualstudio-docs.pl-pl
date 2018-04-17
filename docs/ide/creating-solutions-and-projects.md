---
title: Tworzenie projektów i rozwiązań w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/06/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bb984c1a6947438df663e228bb21bda4eea763c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="create-solutions-and-projects"></a>Tworzenie projektów i rozwiązań

*Projekty* są kontenerami logicznymi w Visual Studio, który przechowuje elementy potrzebne do utworzenia aplikacji, takich jak pliki kodu źródłowego, mapy bitowe, ikony, a odwołania do składnika i usługi. Podczas tworzenia nowego projektu programu Visual Studio tworzy *rozwiązania* zawiera projekt. Następnie można dodać inne nowych lub istniejących projektów do rozwiązania, jeśli chcesz. Rozwiązania może również zawierać pliki, które nie są podłączone do danego projektu.

![Rozwiązanie lub projekt hierarchii](./media/vside-proj-soln.png)

Można wyświetlić Twojego rozwiązania i projekty, które znajdują się w oknie narzędzia o nazwie **Eksploratora rozwiązań**. Poniższy zrzut ekranu przedstawia przykład rozwiązania **Eksploratora rozwiązań** (**BikeSharing.Xamarin UWP**) zawiera dwa projekty: **BikeSharing.Clients.Core** i **BikeSharing.Clients.Windows**. Każdy projekt zawiera wiele plików, folderów i odwołań. Nazwa projektu pogrubione jest *projekt startowy*; oznacza to, że w projekcie, który rozpoczyna się po uruchomieniu aplikacji. Można określić, który projekt jest projekt startowy.

![Eksplorator rozwiązań z projektami](./media/vside-solution-explorer-projects.png)

Podczas tworzenia projektu samodzielnie przez dodanie do niej niezbędne pliki, program Visual Studio oferuje wyboru szablonów projektu i rozpoczęcie head. Tworzenie nowego projektu z szablonu. umożliwi projekt o essentials dla tego typu projektu, a można zmienić nazwy plików lub Dodaj nowy lub istniejący kod i innych zasobów do niej zgodnie z potrzebami.

Trwa powiedział, rozwiązań i projektów nie wymagane do opracowywania aplikacji w programie Visual Studio. Możesz także po prostu otworzyć kod, który zostały sklonowane z repozytorium Git lub pobrana w innym miejscu. Aby uzyskać więcej informacji, zobacz [Opracuj kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

> [!NOTE]
> Opisy w tym temacie są oparte na wersji Visual Studio Community. Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w tym miejscu, w zależności od ustawień lub wersji Visual Studio. Aby zmienić ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia**, **Import i eksport ustawień**, a następnie Wybierz **zresetować wszystkie ustawienia**.

## <a name="to-create-a-project-from-a-project-template"></a>Aby utworzyć projekt z szablonu projektu

1. Istnieje wiele sposobów, aby utworzyć nowy projekt w programie Visual Studio. Na **— strona początkowa**, wprowadź nazwę szablonu projektu w **Wyszukaj szablony projektów** wpisz lub wybierz **Tworzenie nowego projektu** łącze, aby otworzyć **nowy Projekt** okno dialogowe. Można również wybrać **pliku** > **nowy** > **projektu...**  menu paska lub wybierz **nowy projekt** przycisk na pasku narzędzi.

  ![Strona początkowa](./media/vside-newproject1.png)

  W **nowy projekt** okno dialogowe Szablony projektów dostępne są wyświetlane na liście w obszarze **szablony** kategorii. Szablony są zorganizowane według języków programowania i typu projektu, takie jak Visual C#, JavaScript i usługi Azure Data Lake.

  ![Okno dialogowe Nowy projekt](./media/vside-newproject-templates-list.png)

  > [!NOTE]
  > Lista dostępnych języków i szablony projektów wyświetlonym zależy od wersji programu Visual Studio są uruchomione i obciążeń, które są zainstalowane. Aby dowiedzieć się więcej o sposobie instalowania dodatkowych obciążeń, zobacz [zmodyfikować Visual Studio 2017 przez dodanie lub usunięcie obciążeń i składniki](../install/modify-visual-studio.md).

1. Pokaż listę szablonów dla języka programowania, który ma być używany przez wybranie trójkąt obok nazwy języka, a następnie wybierz typ projektu.

  W poniższym przykładzie przedstawiono dostępne dla projektów Visual C# .NET Core szablonów projektu.

  ![Szablony projektu](./media/new-project-dialog-net-core.png)

1. Wprowadź nazwę dla nowego projektu w **nazwa** pole. Użytkownik może zapisać projekt w domyślnej lokalizacji na komputerze, lub wybierz **Przeglądaj** przycisk, aby znaleźć lokalizację.

  Opcjonalnie można zmienić nazwy rozwiązania, lub Dodaj nowy projekt z repozytorium Git, wybierając **Dodaj do kontroli źródła**.

1. Wybierz **OK** przycisk, aby utworzyć rozwiązania i projektu.

1. Jeśli chcesz dodać dodatkowy projekt do rozwiązania, wybierz węzeł rozwiązania w **Eksploratora rozwiązań**, a następnie na pasku menu wybierz pozycję **projektu** > **Dodaj nowy element**.

## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu z istniejących plików kodu

Jeśli masz kolekcję plików kodu źródłowego, można łatwo dodać je do projektu.

1. W menu, wybierz **pliku** > **nowy** > **projektu z istniejącego kodu**.

1. W **utworzyć projekt z istniejących plików kodu** kreatora, wybierz typ projektu w **jaki typ projektu chcesz utworzyć?** listy rozwijanej pola, a następnie wybierz pozycję **dalej**  przycisku.

1. W kreatorze, przejdź do lokalizacji plików, a następnie wprowadź nazwę dla nowego projektu w **nazwa** pole. Gdy wszystko będzie gotowe, wybierz pozycję **Zakończ** przycisku.

> [!NOTE]
> Ta opcja działa najlepiej w stosunkowo proste kolekcji plików. Obecnie są obsługiwane tylko typy projektów Visual C++, Apache Cordova, Visual Basic i C#.

## <a name="add-files-to-a-solution"></a>Dodawanie plików do rozwiązania

Jeśli plik, który ma zastosowanie do wielu projektów, takich jak plik readme dla rozwiązania, lub innych plików, które logicznie na poziomie rozwiązania, a nie w określonym projekcie, następnie należy dodać je do rozwiązania, sam. Aby dodać element do rozwiązania, w menu kontekstowym (kliknij prawym przyciskiem myszy) w węźle rozwiązania **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy element**, lub **Dodaj** > **istniejący element**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Tworzenie projektu platformy .NET, przeznaczonego dla określonej wersji programu .NET Framework

Podczas tworzenia projektu można określić określonej wersji programu .NET Framework, która ma projektu do użycia. Aby określić wersji programu .NET framework, wybierz **Framework** menu rozwijane w **nowy projekt** okno dialogowe.

![W ramach listy rozwijanej w oknie dialogowym Nowy projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> .NET Framework 3.5 zainstalowanego w systemie do wersji systemu .NET Framework starszych niż program .NET Framework 4 są wymagane.

## <a name="create-empty-solutions"></a>Utwórz puste rozwiązania

Można również utworzyć pusty rozwiązania, które mają projektów. Może to być korzystniejsze w przypadkach, w której chcesz utworzyć rozwiązanie i projekty od początku.

### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie

1. W menu, wybierz **pliku** > **nowy** > **projektu...** .

1. W lewym (**szablony**) okienku wybierz **inne typy projektów** > **rozwiązań programu Visual Studio** na wyświetlonej liście.

1. W środkowym okienku wybierz **puste rozwiązanie**.

1. Wprowadź **nazwa** i **lokalizacji** wartości dla rozwiązania, a następnie wybierz **OK**.

Po utworzeniu puste rozwiązanie nowych lub istniejących projektów lub elementów można dodawać do niego, wybierając **Dodaj nowy element** lub **Dodaj istniejący element** na **projektu** menu.

Jak wspomniano wcześniej, można również otworzyć pliki kodu bez konieczności projekt lub rozwiązanie. Aby dowiedzieć się więcej o tworzeniu kodu w ten sposób, zobacz [Opracuj kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Tworzenie tymczasowych projektu (C# i Visual Basic)

Jeśli utworzysz. Projekt na podstawie NET bez określenia lokalizacji na dysku, jest tymczasowy projektu. Tymczasowe projekty umożliwiają eksperymentować projektów platformy .NET. W dowolnym momencie podczas pracy z projektem tymczasowe, można go zapisać czy odrzucić go.

Aby utworzyć projekt tymczasowy, najpierw przejść do **narzędzia** > **opcje** > **projekty i rozwiązania**  >   **Ogólne**i usuń zaznaczenie pola wyboru **zapisać nowe projekty podczas tworzenia** wyboru. Następnie otwórz **nowy projekt** okna dialogowego w zwykły sposób.

## <a name="delete-a-solution-project-or-item"></a>Usuwanie rozwiązania, projektu lub elementu

Możesz usunąć rozwiązań i ich zawartość stałe, ale nie za pomocą środowiska IDE programu Visual Studio. Usuwanie elementów w programie Visual Studio tylko usuwa je z bieżącego rozwiązania lub projektu. Aby trwale usunąć rozwiązania lub innego składnika z systemu, użyj Eksploratora plików, można usunąć folderu, który zawiera *.sln* i *.suo* pliki rozwiązania. Jednak przed trwałe usunięcie rozwiązania, zalecane jest, wykonać kopię zapasową wszelkich projektów lub pliki w przypadku, gdy należy je ponownie.

> [!NOTE]
> *.Suo* plik jest plikiem ukrytym, które nie są wyświetlane w obszarze domyślne ustawienia Eksploratora plików. Aby wyświetlić ukryte pliki na **widoku** menu w Eksploratorze plików wybierz **ukryte elementy** wyboru.

### <a name="to-permanently-delete-a-solution"></a>Aby trwale usunąć rozwiązania

1. W **Eksploratora rozwiązań**, w menu kontekstowym rozwiązania do usunięcia, wybierz **Otwórz folder w Eksploratorze plików**.

1. W Eksploratorze plików Przejdź w górę o jeden poziom.

1. Wybierz folder zawierający rozwiązania, a następnie wybierz pozycję **usunąć** klucza.

## <a name="see-also"></a>Zobacz także

[Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)  
[Repozytoria typu open source firmy Microsoft w witrynie GitHub](https://github.com/Microsoft)  
[Przykłady programu Visual Studio](../ide/visual-studio-samples.md)  
[Przykłady kodu dewelopera](https://code.msdn.microsoft.com/)
