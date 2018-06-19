---
title: 'Wskazówki: Dodawanie niestandardowych XAML do strony początkowej | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e6e782e703282f9eb4e189671c086eb17db427
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140062"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Wskazówki: Dodawanie niestandardowych XAML do strony początkowej
W tym przewodniku przedstawiono sposób tworzenia niestandardowych Visual Studio — strona początkowa zawierający przeglądarki sieci Web.  
  
## <a name="adding-custom-xaml"></a>Dodawanie niestandardowej XAML  
  
1.  Utwórz stronę startową, postępując zgodnie z instrukcjami w [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).  
  
2.  W pliku MainWindow.xaml znaleźć \<siatki > sekcji.  
  
3.  Dodaj \<TabControl > element i \<TabItem > wewnątrz \< siatki > element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Dodaj drugi \<TabItem >, z \<przycisk > elementu, którego kliknięcie spowoduje otwarcie nowego projektu:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Testowanie strony początkowej niestandardowych  
  
1.  Naciśnij F5.  
  
     Zostanie otwarta eksperymentalne wystąpienie programu Visual Studio z niestandardowej strony początkowej zainstalowany, ale nie są wybrane.  
  
2.  Eksperymentalne wystąpienie programu Visual Studio, otwórz **/narzędzia Options / środowiska** strony.  
  
3.  Wybierz **uruchamiania**. Na **dostosowanie strony początkowej** listy, wybierz plik .xaml, a następnie kliknij przycisk **OK**.  
  
4.  Na **widoku** menu, kliknij przycisk **— strona początkowa**.  
  
5.  Kliknij przycisk **Bing** kartę.  
  
     Powinna zostać wyświetlona strona sieci web usługi Bing.  
  
6.  Kliknij przycisk **MyButton** kartę.  
  
     Powinny pojawić się **MyProject** przycisku, co spowoduje otwarcie **nowy projekt** okna dialogowego.  
  
7.  Zamknij eksperymentalne wystąpienie.  
  
## <a name="applying-the-custom-start-page"></a>Stosowanie strony początkowej niestandardowych  
  
#### <a name="to-test-the-custom-start-page"></a>Aby przetestować niestandardowej strony początkowej  
  
1.  W **narzędzia / Opcje / środowiska**, wybierz pozycję **uruchamiania**. Na **dostosowanie strony początkowej** listy, wybierz plik .xaml, a następnie kliknij przycisk **OK**.  
  
## <a name="next-steps"></a>Następne kroki  
 Visual Studio — strona początkowa zawiera teraz kartę, która wyświetla karty przeglądarki sieci Web i MyButton. Można tworzyć niestandardowe strony Start mające innych funkcji za pomocą *CodeBehind* modelu, aby dodać niestandardowe biblioteki dll, jak pokazano w [Dodawanie formantu użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md). Niestandardowe strony Start można udostępniać innym użytkownikom przez publikowanie wynikowy plik .vsix [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witryny sieci Web, lub do innej witryny sieci Web lub sieci udział. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowych stron Start](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Kontrole kontenerów WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)