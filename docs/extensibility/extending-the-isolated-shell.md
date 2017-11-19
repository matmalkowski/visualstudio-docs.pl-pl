---
redirect_url: shell/extending-the-isolated-shell
title: Rozszerzanie programu Isolated Shell | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ebd219beb28fc183d876e0391192390da03f8ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-isolated-shell"></a>Rozszerzanie programu Isolated Shell
Powłoka programu Visual Studio izolowane można rozszerzyć przez dodanie pakiet VSPackage, część Managed Extensibility Framework (MEF) lub ogólnego projektu VSIX do aplikacji programu isolated shell.  
  
> [!NOTE]
>  Poniższe kroki zakładają, że utworzono aplikację podstawowe programu isolated shell za pomocą programu Visual Studio Shell izolowanego szablonu projektu. Aby uzyskać więcej informacji dotyczących tego szablonu projektu, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablon projektu pakietu Visual Studio  
 Szablon projektu pakietu Visual Studio można znaleźć w trzech różnych miejscach w **nowy projekt** okna dialogowego:  
  
1.  W obszarze **Visual Basic**, **rozszerzalności**. Domyślny język projektu jest Visual Basic.  
  
2.  W obszarze **Visual C#**, **rozszerzalności**. Domyślny język projektu jest C#.  
  
3.  W obszarze **innych typów projektów**, **rozszerzalności**. Domyślny język projektu jest C++.  
  
## <a name="adding-a-vspackage"></a>Dodawanie pakiet VSPackage  
 Pakiet VSPackage można dodać do aplikacji programu isolated shell. Poniższe kroki pokazują, jak utworzyć klucz, który dodaje poleceń menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Aby dodać nowy pakiet VSPackage  
  
1.  Dodaj projekt pakietu Visual Studio o nazwie `MenuCommandsPackage`.  
  
2.  Na **podstawowe informacje o pakiecie VSPackage** kreatora, ustaw **nazwa firmy** do `Fabrikam` i **nazwa pakiet VSPackage** do `FabrikamMenuCommands`. Wybierz **dalej** przycisku.  
  
3.  Na następnej stronie wybierz **polecenie** , a następnie wybierz **dalej**.  
  
4.  Na następnej stronie można ustawić **nazwa polecenia** do `Fabrikam Command` i **identyfikator polecenia** do `cmdidFabrikamCommand`, a następnie wybierz pozycję **dalej**.  
  
5.  Na **wybierz opcje projektu testu** strony, usuń zaznaczenie opcji testowania, a następnie wybierz **Zakończ** przycisku.  
  
6.  W projekcie ShellExtensionsVSIX Otwórz plik Source.Extension.vsixmanifest,a.  
  
     **Zasoby** sekcji powinien zawierać wpis dla projektu VSShellStub.AboutBoxPackage.  
  
7.  Wybierz **nowy** przycisku.  
  
8.  W **Dodaj nowy element zawartości** okna w **typu** listy, wybierz **Microsoft.VisualStudio.VsPackage**.  
  
9. W **źródła** listy, upewnij się, że **projektu w bieżącym rozwiązaniu** jest zaznaczone. W **projektu** pola listy, wybierz opcję **MenuCommandsPackage**.  
  
10. Zapisz i zamknij plik.  
  
11. Ponownie skompiluj rozwiązanie i Rozpocznij debugowanie programu isolated shell.  
  
12. Na pasku menu wybierz **narzędzia** menu, a następnie **polecenia Fabrikam**.  
  
     Okno komunikatu powinny być wyświetlane.  
  
13. Zatrzymaj debugowanie aplikacji.  
  
## <a name="adding-a-mef-component-part"></a>Dodawanie część MEF  
 Poniższe kroki przedstawiają sposób dodawania część MEF do aplikacji programu isolated shell.  
  
#### <a name="to-add-a-mef-component"></a>Aby dodać składnik MEF  
  
1.  W **Dodawanie nowego projektu** okna dialogowego, w obszarze **Visual C#**, **rozszerzalności**, użyj **marginesu edytora** szablonu można dodać projektu. Nadaj mu nazwę `ShellEditorMargin`.  
  
2.  W projekcie ShellExtensionsVSIX Otwórz plik Source.Extension.vsixmanifest,a w widoku Projekt, a nie w widoku kodu.  
  
3.  W `Asset` wybierz **Dodaj zawartość**.  
  
4.  W **Dodaj nowy element zawartości** okna w **typu** listy, wybierz **Microsoft.VisualStudio.MefComponent**.  
  
5.  W **źródła** listy, upewnij się, że **projektu w bieżącym rozwiązaniu** jest zaznaczone. W **projektu** pola listy, wybierz opcję **ShellEditorMargin**.  
  
6.  Zapisz i zamknij plik.  
  
7.  Ponownie skompiluj rozwiązanie i Rozpocznij debugowanie programu isolated shell.  
  
8.  Otwórz plik tekstowy.  
  
     Zielony margines, który zawiera tekst "Hello world!" powinny być wyświetlane w dolnej części okna pliku tekstowego.  
  
9. Zatrzymaj debugowanie aplikacji.  
  
## <a name="adding-a-generic-vsix-project"></a>Dodawanie projektu VSIX ogólny  
  
#### <a name="to-add-a-generic-vsix-project"></a>Aby dodać ogólnego projektu VSIX  
  
1.  W **Dodawanie nowego projektu** okna dialogowego, w obszarze **Visual C#**, **rozszerzalności**, użyj **VSIXProject** szablonu można dodać projektu. Nadaj mu nazwę `EmptyVSIX`.  
  
2.  W projekcie ShellExtensionsVSIX Otwórz plik Source.extensions.vsixmanifest w widoku Projekt, a nie w widoku kodu.  
  
3.  W `Assets` wybierz **nowy**.  
  
4.  W **Dodaj nowy element zawartości** okna w **typu** wybierz rodzaj zawartości, które chcesz dodać.  
  
5.  W **źródła**, upewnij się, że **projekt w bieżącym rozwiązaniu** opcja jest zaznaczona. W polu listy wybierz nazwę projektu VSIX.  
  
6.  Zapisz i zamknij plik.  
  
7.  Jeśli ten projekt zawiera skompilowany kod, należy edytować projekt tak, aby zestaw znajduje się w danych wyjściowych.  
  
    1.  Zwolnienie projektu VSIX, a następnie otwórz plik projektu.  
  
    2.  W pierwszym `<PropertyGroup>` bloków, zmień wartość `<CopyBuildOutputToOutputDirectory>` do `true`.  
  
    3.  Zapisz i ponownie Załaduj projekt.  
  
8.  Tworzenie i uruchamianie rozwiązania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie aplikacji podstawowe Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)