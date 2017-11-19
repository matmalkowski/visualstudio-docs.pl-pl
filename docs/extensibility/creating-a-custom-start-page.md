---
title: "Tworzenie niestandardowej strony początkowej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9782e51688ae1ef4fda3ed52636de54149fa79e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-custom-start-page"></a>Tworzenie strony początkowej niestandardowych
Wykonując kroki opisane w tym dokumencie można utworzyć niestandardowej strony początkowej.  
  
## <a name="creating-a-blank-start-page"></a>Tworzenie strony początkowej puste  
 Najpierw upewnij puste strony początkowej, tworząc plik .xaml struktury znaczników, rozpoznawany przez Visual Studio. Następnie należy dodać kodu znaczników i kodu powiązanego do utworzenia wygląd i funkcjonalność, który ma.  
  
#### <a name="to-create-a-blank-start-page"></a>Aby utworzyć pustą stronę startową  
  
1.  Utwórz nowy projekt typu **aplikacji WPF** (**Visual C# / Windows Desktop**.  
  
2.  Dodaj odwołanie do `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Otwórz plik XAML w edytorze XML i zmień najwyższego poziomu \<okna > elementu \<UserControl > elementu bez usuwania deklaracji przestrzeni nazw.  
  
4.  Usuń `x:Class` deklaracji z elementu najwyższego poziomu. Dzięki temu zawartość XAML są zgodne z okna narzędzia Visual Studio, która hostuje strony początkowej.  
  
5.  Dodaj następujące deklaracje przestrzeni nazw na najwyższym poziomie \<UserControl > elementu.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Te obszary nazw umożliwiają uzyskanie dostępu do poleceń programu Visual Studio, kontrolek i ustawienia interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Dodawanie Visual Studio — polecenia do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Poniższy przykład przedstawia kod znaczników w pliku .xaml dla puste strony początkowej. Zawartość niestandardowych powinien znajdować się w wewnętrznej <xref:System.Windows.Controls.Grid> elementu.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Dodawanie formantów do pustych \<UserControl > elementu, aby wypełnić niestandardowej strony początkowej. Aby uzyskać informacje o sposobie dodawania funkcji, które są specyficzne dla programu Visual Studio, zobacz [Dodawanie Visual Studio — polecenia do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testowanie i stosowanie niestandardowej strony początkowej  
 Nie ustawiaj głównej wystąpienie programu Visual Studio, aby uruchomić niestandardowej strony początkowej bez sprawdzenia, czy nie awarię programu Visual Studio. Zamiast tego należy przetestować w eksperymentalnym wystąpieniu.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Aby przetestować utworzonych ręcznie niestandardowej strony początkowej  
  
1.  Kopiowanie pliku XAML oraz wszelkich obsługi plików tekstowych i znaczników pliki do **%USERPROFILE%\My 2015\StartPages Documents\Visual Studio\\**  folderu.  
  
2.  Jeśli stronę początkową odwołuje się do formantów ani typów w zestawach, które nie są instalowane przez program Visual Studio, skopiuj zestawy, a następnie wklej je w *folder instalacji programu Visual Studio***\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Wpisz w wierszu polecenia programu Visual Studio **devenv/rootsuffix Exp** otworzyć eksperymentalne wystąpienie programu Visual Studio.  
  
4.  W eksperymentalnym wystąpieniu, przejdź do **narzędzia / Opcje / środowiska / uruchamiania** strony i wybierz plik XAML z **dostosowanie strony początkowej** listy rozwijanej.  
  
5.  Na **widoku** menu, kliknij przycisk **— strona początkowa**.  
  
     Powinien zostać wyświetlony stronę początkową niestandardowych. Jeśli chcesz zmienić wszystkie pliki, możesz musi zamknąć eksperymentalne wystąpienie programu, zmiany, skopiuj i Wklej zmienionych plików, a następnie ponownie otwórz eksperymentalne wystąpienie, aby zobaczyć zmiany.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Aby zastosować niestandardowej strony początkowej w głównej wystąpienie programu Visual Studio  
  
-   Po przetestowane stronę początkową i znaleźć się stabilne użyj **dostosowanie strony początkowej** opcji **opcje** okno dialogowe, aby go wybrać jako strony początkowej w głównej wystąpienie programu Visual Studio  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Dodawanie niestandardowych XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)   
 [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Wskazówki: Zapisywanie ustawień użytkownika na stronę początkową](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Wdrażanie niestandardowych Start stron](../extensibility/deploying-custom-start-pages.md)