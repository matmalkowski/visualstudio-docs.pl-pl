---
title: Uruchamianie tworzenia rozszerzenia programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 09/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d788121e81af48cb972631d0845ad7b4317818b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Uruchamianie tworzenia rozszerzenia programu Visual Studio
Jeśli rozszerzenia programu Visual Studio przed nigdy nie zostały zapisane, prawdopodobnie masz kilka pytań. Firma Microsoft zostały umieszczone niektóre z najczęściej następujące. Jeśli nie widzisz informacje, których szukasz, użyj przycisków opinii (**był pomocny tę stronę?** w dolnej części ekranu) aby poprosić o jaką mają.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Jakie oprogramowanie należy opracowywania rozszerzeń programu Visual Studio?  
 Musisz zainstalować program Visual Studio SDK oprócz programu Visual Studio w celu opracowywania rozszerzeń programu Visual Studio. Visual Studio SDK można zainstalować jako część instalacji regularnych lub możesz zainstalować ją później. Aby uzyskać więcej informacji na temat instalowania programu Visual Studio SDK, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Jakiego rodzaju rzeczy może zrobić z rozszerzeń programu Visual Studio?  
 Niebo przez limit, jeśli chodzi o opracowująca w wyobraźni inne rozszerzenia programu Visual Studio. Oczywiście większość rozszerzenia mają związek z pisania kodu, ale które nie mają w przypadku. Oto kilka przykładów rodzajów rozszerzeń, które można tworzyć:  
  
-   Obsługa języków, które nie są uwzględnione w programie Visual Studio, kolorowanie składni, funkcję IntelliSense i obsługi kompilatora i debugowania  
  
-   Narzędzia wydajności, które rozszerzają podstawowe IDE wystąpić dodatkowe szablony, okna dialogowe refaktoryzacji, nowy kod lub okna narzędzi  
  
-   Projektanci specyficznego dla domeny w scenariuszach, takich jak obsługa danych projektu lub w chmurze  
  
 Przykłady rozszerzeń, zapoznaj się z [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Wiele rozszerzeń są otwarte powierzając jej ich konserwację i witryny Marketplace zawiera łącza do ich repozytorium GitHub. 
  
## <a name="which-visual-studio-features-can-i-extend"></a>Funkcje programu Visual Studio można rozszerzyć?  
 Teoretycznie można rozszerzyć o niemal dowolnym część programu Visual Studio: menu, paski narzędzi, polecenia, windows, rozwiązania, projekty, edytory i tak dalej.  
  
 W praktyce znaleźliśmy, czy funkcje, które większość osób chce rozszerzyć polecenia, menu i pasków narzędzi systemu windows, IntelliSense i projektów. Poniżej podano linki do odpowiednich sekcji:  
  
-   [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md): dodać własne elementy do programu Visual Studio menu i pasków narzędzi. Aby uruchomić nowe funkcje programu Visual Studio lub własnych aplikacji zewnętrznych pomocnika można używać ich. Można też podać skróty niestandardowe dla elementów menu.  
  
-   [Rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md): rozszerzyć istniejącą okna narzędzi lub utworzyć własne okna narzędzi. Na przykład można dodać nowych właściwości do **właściwości**, lub można utworzyć nowe okno narzędzi, aby dodać dodatkowe funkcje.  
  
-   [Edytora i rozszerzenia usługi języka](../extensibility/editor-and-language-service-extensions.md): dodać własne dostosowania IntelliSense określonych języków Visual Studio lub utworzyć obsługę nowych języków programowania. Można utworzyć nowego zakończeń instrukcji, sugestie i nowych QuickInfo etykietek narzędzi. Żarówki możesz dodać refaktoryzacji sugestie i poprawki kodu do obsługi nowych języków programowania.  
  
-   [Rozszerzanie projektów](../extensibility/extending-projects.md)  
  
-   [Opcje i rozszerzanie ustawień użytkownika](../extensibility/extending-user-settings-and-options.md)  
  
-   [Rozszerzanie właściwości i w oknie właściwości](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio izolowane powłoki](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>Szablony projektów, które są udostępniane przez VSSDK?  
 Dwa główne typy rozszerzeń są pakiety VSPackage i MEF rozszerzenia. Ogólnie rzecz biorąc pakiet VSPackage rozszerzenia są używane dla rozszerzeń używających lub rozszerzyć poleceń, narzędzi systemu windows i projektów. Rozszerzenia MEF służą do rozszerzania lub Dostosuj edytorze programu Visual Studio.  
  
 W przypadku rozszerzenia Visual C# i Visual Basic VSSDK zapewnia pusty szablon projektu VSIX można użyć razem z nowych szablonów elementu utworzonych polecenia menu okna narzędzi i rozszerzenia edytora. Można również użyć tego szablonu szablony projektów pakietu fragmentów kodu i pozostałych artefaktów, w celu dystrybucji do innych użytkowników.  
  
 Dla języka C++ Kreator pakiet VSPackage zawiera kod, aby dodać polecenia menu okna narzędzi i edytory niestandardowych.  
  
 Szablon programu Isolated Shell jest używany do rozszerzenie w wersji programu Visual Studio shell, który można oznaczyć i rozpowszechniać jako własnego pakietu. W następujących tematach opisano, jak rozpocząć pracę z każdym rodzajem rozszerzenia:  
  
-   Polecenia menu: [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Narzędzia systemu windows: [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Rozszerzenia edytora: [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Podstawowe VSPackages: [Tworzenie rozszerzenia z pakiet VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Szablon projektu VSIX: [wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio izolowana powłoka: [wskazówki: tworzenie izolowane powłoki aplikacji w warstwie podstawowa](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Jak uzyskać Moje rozszerzenia, aby wyglądały jak Visual Studio?  
 Bardzo porady dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Gdzie można znaleźć przykłady kodu VSSDK?  
 Łącza wymienione w poprzedniej sekcji mają wskazówki krok po kroku, który opisano sposób wykonania określonych funkcji. Możesz również znaleźć typu open source VSSDK próbek w witrynie GitHub pod [przykłady dotyczące programu Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Jak można rozpowszechniać Moje rozszerzenie?  
 Można zainstalować rozszerzenia na innym komputerze lub przesyłać je do Twoich znajomych jako pliku .vsix zainstalowaniu kliknij go dwukrotnie. Można znaleźć więcej informacji na temat pakietów VSIX w [wysyłania rozszerzenia dla programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Można również publikować swoje rozszerzenie w Visual Studio Marketplace, dzięki czemu są widoczne dla dużej liczby klientów programu Visual Studio. Na przykład pakietu rozszerzenia do witryny Marketplace, zobacz [wskazówki: publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Aby uzyskać więcej informacji dotyczących co należy zrobić, aby publikować w witrynie Marketplace, zobacz [produktów i rozszerzenia programu Visual Studio](https://docs.microsoft.com/en-us/vsts/integrate/ide/extensions/overview).
