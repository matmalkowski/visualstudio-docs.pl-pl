---
title: Konfiguracje kompilacji opis | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 003e4abaf5e6fbabead604c495b2018402cf74ec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="understanding-build-configurations"></a>Ogólne informacje o konfiguracjach kompilacji
Można przechowywać różne konfiguracje właściwości rozwiązania i projektu do użycia w różnych rodzajów kompilacji. Aby utworzyć, wybierz, zmodyfikować lub usunąć konfigurację, można użyć **programu Configuration Manager**. Aby otworzyć go na pasku menu, wybierz polecenie **kompilacji**, **programu Configuration Manager**, lub po prostu wpisz **konfiguracji** w **Szybkie uruchamianie** pole. Można również użyć **konfiguracje rozwiązania** listy na **standardowe** narzędzi, aby wybrać konfigurację, lub Otwórz **programu Configuration Manager**.  
  
> [!NOTE]
>  Jeśli nie można znaleźć rozwiązania ustawień konfiguracji na pasku narzędzi i nie można uzyskać dostępu **programu Configuration Manager**, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] można stosować ustawienia środowiska deweloperskiego. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie konfiguracjami z zastosować ustawień dewelopera Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).  
  
 Domyślnie, debugowania i konfiguracje wersji znajdują się w projektach, które są tworzone za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonów. Konfiguracja debugowania obsługuje debugowania aplikacji i konfiguracji wydanie kompilacje wersji aplikacji, które można wdrożyć. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie debugowania i konfiguracje wersji](../debugger/how-to-set-debug-and-release-configurations.md). Można również utworzyć konfiguracje niestandardowego rozwiązania oraz projektu. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i edycja konfiguracji](../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="solution-configurations"></a>Konfiguracje rozwiązania  
 Konfiguracja rozwiązania określa, jak projektów w rozwiązaniu są wbudowane i wdrożone. Aby zmodyfikować konfigurację rozwiązania lub zdefiniuj nowe, w **programu Configuration Manager**w obszarze **aktywnej konfiguracji rozwiązania**, wybierz **Edytuj** lub **nowy** .  
  
 Każdy wpis **projektu kontekstów** projektu w rozwiązaniu reprezentuje pole w konfiguracji rozwiązania. Dla każdej kombinacji **aktywnej konfiguracji rozwiązania** i **platformy aktywne rozwiązanie**, można ustawić użycia każdego projektu. (Aby uzyskać więcej informacji na temat platformy rozwiązania, zobacz [platformy kompilacji opis](../ide/understanding-build-platforms.md).)  
  
> [!NOTE]
>  Podczas definiowania nowej konfiguracji rozwiązania i wybierz **Utwórz nowe konfiguracje projektu** pole wyboru [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie przypisuje nowej konfiguracji do wszystkich projektów. Podobnie, kiedy należy zdefiniować nowa platforma rozwiązania i wybierz **Utwórz nowe platformy projektu** pole wyboru [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie przypisuje nowa platforma do wszystkich projektów. Ponadto po dodaniu projektu, którego celem jest nowa platforma Visual Studio dodaje tej platformy do listy platformy rozwiązania i przypisuje go do wszystkich projektów.  
>   
>  Nadal można zmodyfikować ustawienia dla każdego projektu.  
  
 Konfiguracja aktywnego rozwiązania także kontekstu do środowiska IDE. Na przykład, jeśli pracujesz nad projektem i konfiguracja Określa, że jej zostanie skompilowany dla urządzenia przenośnego, **przybornika** wyświetla tylko te elementy, których można użyć w projekcie z urządzeń przenośnych.  
  
## <a name="project-configurations"></a>Konfiguracje projektu  
 Configuration i platform docelowych projektu ze sobą używanych do określania właściwości do użycia, gdy jest ona wbudowana. Projekt może mieć inny zestaw definicji właściwości dla każdej kombinacji konfiguracji i platformy. Aby zmodyfikować właściwości projektu, można użyć strony jej właściwości. (W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.)  
  
 Dla każdej konfiguracji projektu można określić właściwości zależne od konfiguracji zgodnie z potrzebami. Na przykład dla określonej kompilacji, można ustawić elementy projektu, które będą uwzględnione, i co output plików zostanie utworzony, gdzie będą umieszczane i jak będzie optymalizowany.  
  
 Konfiguracje projektu może się znacznie różnić. Na przykład właściwości jednej konfiguracji może określić zoptymalizowana swojego pliku wyjściowego zajmować minimalny odstęp w trakcie innej konfiguracji może określić, że jego plik wykonywalny uruchamiany przy maksymalnej szybkości łącza.  
  
 Konfiguracje projektu są przechowywane przez rozwiązanie — nie przez użytkownika, dzięki czemu mogą być współużytkowane przez zespół.  
  
 Mimo że zależności projektu są niezależne od konfiguracji, zostanie utworzona tylko projekty, które są określone w aktywnej konfiguracji rozwiązania.  
  
## <a name="how-visual-studio-assigns-project-configurations"></a>W jaki sposób program Visual Studio przypisuje konfiguracje projektu  
 Podczas definiowania nowej konfiguracji rozwiązania, a nie kopiuje ustawień z istniejącego, Visual Studio korzysta z następujących kryteriów można przypisać domyślnej konfiguracji projektu. Kryteria są oceniane w podanej kolejności.  
  
1.  Jeśli projekt ma nazwę konfiguracji (*\<Nazwa konfiguracji > \<nazwa platformy >*) czy dopasowań dokładnie nazwę nowej konfiguracji rozwiązania, że konfiguracja jest przypisany. Nazwy konfiguracji nie jest rozróżniana.  
  
2.  Projekt ma nazwę konfiguracji, w której części nazwy konfiguracji odpowiada nowej konfiguracji rozwiązania, zostanie przypisany tej konfiguracji, czy składnik platformy odpowiada lub nie.  
  
3.  Jeśli nadal są niezgodne, przypisano pierwszy konfiguracji, który znajduje się w projekcie.  
  
## <a name="how-visual-studio-assigns-solution-configurations"></a>W jaki sposób program Visual Studio przypisuje konfiguracje rozwiązania  
 Po utworzeniu konfiguracji projektu (w **programu Configuration Manager**, wybierając **nowy** z menu rozwijanego w **konfiguracji** kolumny dla tego projektu) i Wybierz **Utwórz nowe konfiguracje rozwiązania** pole wyboru programu Visual Studio szuka Konfiguracja rozwiązania o nazwie podobnej do skompilowania projektu na każdej z obsługiwanych platform. W niektórych przypadkach program Visual Studio zmienia nazwę istniejącej konfiguracji rozwiązania lub definiuje nowe.  
  
 Visual Studio korzysta z następujących kryteriów można przypisać konfiguracje rozwiązania.  
  
-   Jeśli Konfiguracja projektu nie określa platformy lub określa tylko jednej platformie, następnie konfiguracji rozwiązania, którego nazwa jest zgodna z nowej konfiguracji projektu jest znalezione lub dodane. Nazwa domyślnej tej konfiguracji rozwiązania nie zawiera nazwę platformy; ma formę  *\<Nazwa konfiguracji projektu >*.  
  
-   Jeśli projekt obsługuje wiele platform, Konfiguracja rozwiązania jest znalezione lub dodać do każdej z obsługiwanych platform. Nazwa konfiguracji każdego rozwiązania obejmuje zarówno nazwę konfiguracji projektu, jak i nazwę platformy i ma postać  *\<Nazwa konfiguracji projektu > \<nazwa platformy >*.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md)   
 [Kompilowanie i tworzenia](../ide/compiling-and-building-in-visual-studio.md)   
 [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)   
 [Odwołanie kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)   
 [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)