---
title: Kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 190bcbbb990c0dce447e4153d747fb9f4d6156d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio
Korzystając z procedur opisanych w tym temacie, kompilacji, skompiluj ponownie lub wyczyść wszystkie lub niektóre projekty lub elementy projektu w rozwiązaniu. Samouczek krok po kroku, zobacz [wskazówki: Kompilowanie aplikacji](../ide/walkthrough-building-an-application.md).  
  
> [!NOTE]
> Interfejs użytkownika w posiadanej wersji programu Visual Studio może się różnić od co w tym temacie opisano, w zależności od ustawienia aktywne. Aby zmienić ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia** > **Import i eksport ustawień**, a następnie wybierz pozycję **zresetować wszystkie ustawienia**.
  
## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Aby utworzyć, odbudować, lub wyczyścić całego rozwiązania  
  
1.  W **Eksploratora rozwiązań**, wybierz lub Otwórz rozwiązanie.  
  
2.  Na pasku menu wybierz **kompilacji**, a następnie wybierz jedną z następujących poleceń:  
  
    -   Wybierz **kompilacji** lub **Kompiluj rozwiązanie** skompilować tylko tych plików i składników, które zostały zmienione od czasu ostatniej kompilacji projektu.  
  
        > [!NOTE]
        >  **Kompilacji** staje się polecenie **Kompiluj rozwiązanie** Jeśli rozwiązanie zawiera więcej niż jeden projekt.  
  
    -   Wybierz **Kompiluj ponownie rozwiązanie** "clean" rozwiązania i późniejszego kompilowania plików projektu i wszystkie składniki.  
  
    -   Wybierz **czystą rozwiązania** do usunięcia żadnych plików pośrednich i wynikowych. Tylko do projektu i składnik plików po lewej nowe wystąpienia klasy obiektów i pliki wyjściowe mogą następnie zostać skompilowane.  
  
## <a name="to-build-or-rebuild-a-single-project"></a>Aby utworzyć lub odbudować pojedynczego projektu  
  
1.  W **Eksploratora rozwiązań**, wybierz lub Otwórz projekt.  
  
2.  Na pasku menu wybierz **kompilacji**i wybrać opcję **kompilacji** *ProjectName* lub **odbudować** *ProjectName*.  
  
    -   Wybierz **kompilacji** *ProjectName* tworzenie tylko tych projektu składników, które zostały zmienione od czasu ostatniej kompilacji.  
  
    -   Wybierz **odbudować** *ProjectName* "Wyczyść" Projekt i późniejszego kompilowania plików projektu i wszystkie składniki projektu.  
  
## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Tworzenie tylko projekt startowy i jego zależności  
  
1.  Na pasku menu wybierz **narzędzia** > **opcje**.  
  
2.  W **opcje** okna dialogowego rozwiń **projekty i rozwiązania** węzeł, a następnie wybierz pozycję **skompilować i uruchomić** strony.  
  
     **Skompilować i uruchomić** > **projekty i rozwiązania** > **opcje** zostanie otwarte okno dialogowe.  
  
3.  Wybierz **tworzyć tylko projekty startowe i zależności przy uruchomieniu** pole wyboru.  
  
     Gdy to pole wyboru jest zaznaczone, tylko bieżący projekt startowy i jego zależności są tworzone podczas wykonywania jednej z następujących czynności:  
  
    -   Na pasku menu wybierz **debugowania** > **Start** (**F5**).  
  
    -   Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie** (**Ctrl**+**Shift** +  **B**).  
  
    Jeśli to pole wyboru jest wyczyszczone, wszystkie projekty, ich zależności i plików rozwiązania są tworzone po uruchomieniu dowolne z powyższych poleceń. Domyślnie to pole wyboru jest wyczyszczone.  
  
## <a name="to-build-only-the-selected-visual-c-project"></a>Aby utworzyć tylko dla wybranego projektu Visual C++  
  
Wybierz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektu, a następnie na pasku menu wybierz **kompilacji** > **projektu tylko**i jedną z następujących poleceń:  

- **Tylko kompilację** *ProjectName*  
  
- **Skompiluj ponownie tylko** *ProjectName*  
  
- **Wyczyść tylko** *ProjectName*  
  
- **Połącz tylko** *ProjectName*  

Polecenia te dotyczą tylko [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] wybranego, bez tworzenia, ponownie skompilować, czyszczenia lub łączenia wszystkie zależności projektu lub rozwiązania pliki projektu. W zależności od używanej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **projektu tylko** podmenu może zawierać więcej poleceń.  
  
## <a name="to-compile-multiple-c-project-items"></a>Aby skompilować projekt C++ wielu elementów  
  
W **Eksploratora rozwiązań**, wybierz wiele plików, które mają może być skompilowany akcje, otwórz menu skrótów dla jednego z tych plików, a następnie wybierz pozycję **skompilować**.  

Jeśli pliki mają zależności, plik zostanie skompilowany w kolejności zależności. Operacja kompilacji zakończy się niepowodzeniem, jeśli pliki wymagają prekompilowanego nagłówka, który nie jest dostępna podczas kompilowania. Operacja kompilacji używa bieżącej aktywnej konfiguracji rozwiązania.  
  
## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację  
  
Wykonaj jedną z następujących czynności:  

- Na pasku menu wybierz **kompilacji** > **anulować**.  
  
- Naciśnij klawisz **Ctrl**+**Podziel**.  
  
## <a name="see-also"></a>Zobacz także

[Porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)  
[Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)  
[Kompilowanie i tworzenia](../ide/compiling-and-building-in-visual-studio.md)  
[Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)  
[Instrukcje: ustawienia konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md)  
[Odwołanie kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)  
[Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)  
[Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
