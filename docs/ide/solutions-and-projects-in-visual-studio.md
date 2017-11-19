---
title: "Rozwiązania i projekty w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Rozwiązania i projekty w programie Visual Studio
Po utworzeniu aplikacji witryny sieci Web, itp. dodatek programu Visual Studio rozpoczyna *projektu*. W tym sensie logicznej projekt zawiera wszystkie pliki kodu źródłowego, ikony, obrazów, plików danych i czymkolwiek innym, który zostanie skompilowany w program wykonywalny lub witryny sieci web, w przeciwnym razie jest wymagana w celu przeprowadzenia kompilacji. Projekt zawiera także wszystkie ustawienia kompilatora i inne pliki konfiguracyjne, które mogą być wymagane przez różne usług lub składników, które program będzie komunikować się z.  

> [!NOTE]
>  Nie trzeba użyć rozwiązań lub projektów, jeśli nie chcesz. Możesz po prostu otwarte pliki w programie Visual Studio i rozpocząć edycję kodu. Zobacz [Opracuj kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Aby uzyskać więcej informacji.  

Plik projektu (vbproj, .csproj, .vcxproj) jest plik XML, który definiuje hierarchię folderów wirtualne oraz ścieżki do wszystkich elementów w projekcie. Zawiera ona także ustawienia kompilacji. Aby wyświetlić zawartość pliku projektu, możesz wybrać nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz **Zwolnij projekt** z menu kontekstowego (kliknij prawym przyciskiem myszy). Następnie ponownie otworzyć menu kontekstowe i wybierz **Edytuj \<projectname\>**.  

W programie Visual Studio pliku projektu jest wykorzystywane przez Eksploratora rozwiązań do wyświetlania zawartości projektu i ustawień. Podczas kompilowania projektu aparat MSBuild zużywa plik projektu do tworzenia pliku wykonywalnego. Można również dostosować projektów produkcji inne rodzaje danych wyjściowych.  

Projekt jest zawarty, w rozumieniu logicznych i w systemie plików w *rozwiązanie*, które mogą zawierać jedną lub więcej powiązanych projektów, a także informacji o kompilacji, ustawienia okna programu Visual Studio i różne pliki, które nie są skojarzone z danym projekcie. Rozwiązanie opisanego przez plik tekstowy (.sln) z własną unikatową formacie. go jest zwykle nie mają być edytowane ręcznie.  

Rozwiązanie ma skojarzoną *.suo* plik przechowujący ustawień, preferencji i informacje o konfiguracji dla każdego użytkownika, który działał w projekcie.  

 Na poniższym diagramie przedstawiono relację między projektami i rozwiązaniami i elementy, które zawierają logicznie.  

 ![Projekty Visual Studio i rozwiązania](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>Tworzenie nowych projektów  
 Najprostszym sposobem tworzenia nowego projektu jest uruchomienie z szablonem projektu, który składa się z podstawowego zestawu wstępnie wygenerowanego kodu plików, pliki konfiguracji, zasoby i ustawienia, które ułatwią rozpoczęcie pracy tworzenia określonego typu aplikacji lub witryny sieci Web, w szczególności język programowania. Te szablony są widoczne w **nowy projekt** lub **nowej witryny sieci Web** okno dialogowe po wybraniu **pliku**, **nowy**,  **Projekt** lub **pliku**, **nowe**, **witryny sieci Web**. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](../ide/creating-solutions-and-projects.md).  

Istnieje również możliwość utworzenia niestandardowych szablonów projektów i elementów. Aby uzyskać więcej informacji, zobacz [szablony tworzenie projektów i elementów](../ide/creating-project-and-item-templates.md).  

## <a name="managing-projects-in-solution-explorer"></a>Zarządzanie projektami w Eksploratorze rozwiązań  
 Po utworzeniu nowego projektu, należy użyć **Eksploratora rozwiązań** do wyświetlania i zarządzania projektów i rozwiązań i ich skojarzonych elementów. Na poniższej ilustracji przedstawiono Eksplorator rozwiązań z rozwiązaniem C#, który zawiera dwa projekty.  

 ![Eksplorator rozwiązań](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>W tej sekcji  

-   [Tworzenie rozwiązań i projektów](../ide/creating-solutions-and-projects.md)  

-   [Dodawanie i usuwanie elementów projektu](../ide/adding-and-removing-project-items.md)  

-   [Zarządzanie właściwościami projektów i rozwiązań](../ide/managing-project-and-solution-properties.md)  

-   [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)  

-   [Właściwości aplikacji](../ide/application-properties.md)  

-   [Zarządzanie zestawem i podpisywanie manifestu](../ide/managing-assembly-and-manifest-signing.md)  

-   [Porady: Określanie aplikacji Iicon (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Przeznaczonych dla określonej wersji środowiska .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
