---
title: "Porady: Migracja do nowej wersji języka specyficznego dla domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: "14"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: a1b7a8b2abafa4c63192c207ad73d00e508bddfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Porady: migracja języka specyficznego dla domeny do nowej wersji
Można migrować projektów, które definiowanie i korzystanie z języka specyficznego dla domeny na potrzeby [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] z wersji [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dostarczone z [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Narzędzie migracji jest dostarczana jako część [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. To narzędzie konwertuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektów i rozwiązań, które Użyj lub zdefiniuj narzędzia DSL.  
  
 Należy uruchomić narzędzie do migracji jawnie: go nie jest uruchamiane automatycznie po otwarciu rozwiązania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Narzędzia i dokument szczegółowe wskazówki można znaleźć na tej ścieżce:  
  
 **% Program Files%\Microsoft programu Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Przed przeprowadzeniem migracji projektów DSL  
 Narzędzie do migracji modyfikuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pliki projektu (**.csproj**) i pliki rozwiązania (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Aby przygotować projekty do migracji.  
  
-   Upewnij się, że **.csproj** i **.sln** można zapisywać pliki. Jeśli są pod kontrolą źródła, upewnij się, że ich są wyewidencjonowane.  
  
-   Utwórz kopię foldery, które zamierzasz migrować.  
  
## <a name="migrating-a-collection-of-projects"></a>Migrowanie kolekcji projektów  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Aby przeprowadzić migrację DSL projektów i rozwiązań programu Visual Studio 2010  
  
1.  Uruchom narzędzie do migracji DSL.  
  
    -   Kliknij dwukrotnie pozycję Narzędzia w Eksploratorze Windows (lub Eksploratora plików) lub uruchom narzędzie z wiersza polecenia. Narzędzie znajduje się w tej lokalizacji:  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Wybierz folder, który zawiera rozwiązania i projekty, które ma zostać przekonwertowany.  
  
    -   Wprowadź ścieżkę w polu u góry tego narzędzia, lub kliknij przycisk **Przeglądaj**.  
  
     Narzędzie migracji wyświetli drzewa projektów, które zdefiniuj lub użyj DSLs. Drzewo zawiera każdego projektu, który używa **Microsoft.VisualStudio.Modeling.Sdk** lub **TextTemplating** zestawów.  
  
3.  Przejrzyj drzewa projektów, a następnie usuń zaznaczenie pola wyboru projektów, które chcesz przekonwertować.  
  
    -   Wybierz projekt lub rozwiązanie, aby zobaczyć listę zmian spowoduje, że narzędzie.  
  
        > [!NOTE]
        >  Pola wyboru, które są wyświetlane obok nazwy folderów nie obowiązują. Należy rozwinąć foldery, aby sprawdzić, projekty i rozwiązania.  
  
4.  Konwertowanie projektów.  
  
    1.  Kliknij przycisk **przekonwertować**.  
  
         Przed konwersją każdego pliku projektu, kopię *projektu***.csproj** zostanie zapisany jako *projektu***. vs2008.csproj**  
  
         Kopia każdego *rozwiązania***.sln** zostanie zapisany jako *rozwiązania***. vs2008.sln**  
  
    2.  Zbadaj jakiejkolwiek konwersji nie powiodło się, które są zgłaszane.  
  
         Błędy są zgłaszane z okna tekstowego. Ponadto widok drzewa zawiera czerwona w każdym węźle, której nie można przekonwertować. Możesz kliknąć węzeł, aby uzyskać więcej informacji na temat tego błędu.  
  
5.  **Przekształć wszystkie szablony** w rozwiązaniach zawierający pomyślnie przekonwertowany projektów.  
  
    1.  Otwórz rozwiązanie.  
  
    2.  Kliknij przycisk **Przekształć wszystkie szablony** przycisku w nagłówku Eksploratora rozwiązań.  
  
        > [!NOTE]
        >  Ten krok można wykonać niepotrzebne. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować Przekształć wszystkie szablony](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Zaktualizuj niestandardowego kodu w projektach przekonwertowany.  
  
    -   Próba kompilacji projektów i zbadaj zakończą się niepowodzeniem.  
  
    -   Test z projektantem.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też  
 [Wpisy na blogu pokrewne](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

