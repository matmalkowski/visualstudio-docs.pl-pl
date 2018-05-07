---
title: Rozwiązania i projekty w programie Visual Studio
ms.date: 10/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dc94838423cea7eeab8cef6357267609394352b
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="solutions-and-projects-in-visual-studio"></a>Rozwiązania i projekty w programie Visual Studio

## <a name="projects"></a>Projekty

Po utworzeniu aplikacji witryny sieci Web, itp. dodatek programu Visual Studio rozpoczyna *projektu*. W tym sensie logicznej projekt zawiera wszystkie pliki kodu źródłowego, ikony, obrazów, plików danych, itp., które są kompilowane do pliku wykonywalnego, biblioteki lub witryny sieci Web. Projekt zawiera także ustawienia kompilatora i inne pliki konfiguracyjne, które mogą być wymagane przez różne usługi lub składniki, które komunikuje się z programem.

> [!NOTE]
> Nie trzeba użyć rozwiązań lub projektów programu Visual Studio do edytowania, tworzenie i debugowanie kodu. Można po prostu otwórz folder, który zawiera plików źródłowych w programie Visual Studio i rozpocznij edycję. Aby uzyskać więcej informacji, zobacz [Opracuj kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Projekt jest zdefiniowany w pliku XML z rozszerzeniem, takich jak *vbproj*, *.csproj*, lub *.vcxproj*. Ten plik zawiera hierarchię folderów wirtualnych i ścieżek dla wszystkich elementów w projekcie. Zawiera ona także ustawienia kompilacji.

> [!TIP]
> Aby przyjrzeć się zawartość pliku projektu w programie Visual Studio, najpierw zwolnić projekt, wybierając nazwę projektu w **Eksploratora rozwiązań** i wybierając polecenie **zwolnienie projektu** z menu kontekstowego lub kliknij prawym przyciskiem myszy. Następnie ponownie otworzyć menu kontekstowe i wybierz **Edytuj \<projectname\>**.

W programie Visual Studio, plik projektu jest używany przez **Eksploratora rozwiązań** do wyświetlania zawartości projektu i ustawień. Podczas kompilowania projektu aparat MSBuild zużywa plik projektu do tworzenia pliku wykonywalnego. Można również dostosować projektów produkcji inne rodzaje danych wyjściowych.

## <a name="solutions"></a>Rozwiązania

Projekt jest zawarty w *rozwiązania*. Rozwiązanie zawiera jeden lub więcej projektów pokrewnych, oraz informacje o kompilacji, ustawienia okna programu Visual Studio i różne pliki, które nie są skojarzone z danym projekcie. Rozwiązanie opisanego przez plik tekstowy (rozszerzenie *.sln*) z własną unikatową format; nie jest on przeznaczony do można edytowane ręcznie.

Rozwiązanie ma skojarzoną *.suo* plik przechowujący ustawień, preferencji i informacje o konfiguracji dla każdego użytkownika, który działał w projekcie.

## <a name="create-new-projects"></a>Utwórz nowe projekty

Najprostszym sposobem tworzenia nowego projektu jest zacząć od szablonu projektu dla określonego typu aplikacji lub witryny sieci Web. Szablon projektu składa się z podstawowego zestawu wstępnie wygenerowanego kodu plików, pliki konfiguracji, zasoby i ustawienia. Te szablony są widoczne w **nowy projekt** lub **nowej witryny sieci Web** okno dialogowe po wybraniu **pliku** > **nowy**  >  **Projektu** lub **pliku** > **nowe** > **witryny sieci Web**. Aby uzyskać więcej informacji, zobacz [tworzenia rozwiązań i projektów](../ide/creating-solutions-and-projects.md).

Istnieje również możliwość utworzenia niestandardowych szablonów projektów i elementów. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Zarządzanie projektami w Eksploratorze rozwiązań

Po utworzeniu nowego projektu można użyć **Eksploratora rozwiązań** do wyświetlania i zarządzania projektu i rozwiązania i ich skojarzonych elementów. Na poniższej ilustracji pokazano **Eksploratora rozwiązań** z rozwiązaniem C#, który zawiera dwa projekty.

![Eksplorator rozwiązań](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE](../ide/visual-studio-ide.md)