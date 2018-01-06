---
title: "Dodawanie kontrolki użytkownika do strony początkowej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 448eba0d13a9501c328da79fa31fa66f4376d5df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adding-user-control-to-the-start-page"></a>Dodawanie kontrolki użytkownika do strony początkowej
W tym przewodniku przedstawiono sposób dodawania odwołania biblioteki DLL do niestandardowej strony początkowej. W przykładzie dodano kontrolkę użytkownika do rozwiązania, tworzy kontrolkę użytkownika, a następnie odwołuje się do zestawu skompilowanego z pliku .xaml strony początkowej. Nowa karta obsługuje kontrolki użytkownika, który działa jako podstawowa przeglądarka sieci Web.  
  
 Ten sam proces służy do dodawania zestawu, który może zostać wywołana z pliku .xaml.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Dodawanie formanty użytkownika WPF do rozwiązania  
 Najpierw dodaj kontrolkę użytkownika Windows Presentation Foundation (WPF) do rozwiązania strony początkowej.  
  
1.  Utwórz stronę startową przy użyciu utworzyliśmy w [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
3.  W lewym okienku **nowy projekt** okna dialogowego rozwiń albo **Visual Basic** lub **Visual C#** węzeł, a następnie kliknij przycisk **Windows**. W środkowym okienku wybierz **Biblioteka kontrolek użytkownika WPF**.  
  
4.  Nazwa kontrolki `WebUserControl` , a następnie kliknij przycisk **OK**.  
  
## <a name="implementing-the-user-control"></a>Implementowanie kontrolki użytkownika  
 Aby zaimplementować formanty użytkownika WPF, Tworzenie interfejsu użytkownika (UI) w języku XAML, a następnie wpisz zdarzenia związane z kodem w języku C# lub innego języka .NET.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Można zapisać XAML kontrolki użytkownika  
  
1.  Otwórz plik XAML kontrolki użytkownika. W \<siatki > elementu, Dodaj następujące definicje wiersza do formantu.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  W oknie głównym `Grid` elementu, Dodaj następujące nowe `Grid` element, który zawiera pole tekstowe wpisywać adresy sieci Web i przycisk służący do ustawiania nowego adresu.  
  
    ```xml  
    <Grid Grid.Row="0">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*" />  
            <ColumnDefinition Width="Auto" />  
        </Grid.ColumnDefinitions>  
        <TextBox x:Name="UserSource" Grid.Column="0" />  
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
    </Grid>  
    ```  
  
3.  Dodaj następujące ramki do najwyższego poziomu `Grid` elementu tuż po `Grid` element, który zawiera przycisk i pola tekstowego.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  W poniższym przykładzie przedstawiono ukończone XAML kontrolki użytkownika.  
  
    ```xml  
    <UserControl x:Class="WebUserControl.UserControl1"  
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
                 mc:Ignorable="d"   
                 d:DesignHeight="300" d:DesignWidth="300">  
        <Grid>  
            <Grid.RowDefinitions>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition Height="*" />  
            </Grid.RowDefinitions>  
            <Grid Grid.Row="0">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="Auto" />  
                </Grid.ColumnDefinitions>  
                <TextBox x:Name="UserSource" Grid.Column="0" />  
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
            </Grid>  
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
        </Grid>  
    </UserControl>  
  
    ```  
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Można zapisać zdarzenia związane z kodem kontrolki użytkownika  
  
1.  W Projektancie XAML, kliknij dwukrotnie **ustawiony adres** przycisk dodany do formantu.  
  
     Plik UserControl1.cs zostanie otwarty w edytorze kodu.  
  
2.  Wypełnij SetButton_Click obsługi zdarzeń w następujący sposób.  
  
    ```csharp  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
    {  
        try  
        {  
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);  
        }  
        catch (Exception error)  
        {  
            MessageBox.Show(error.Message);  
        }  
    }  
    ```  
  
     Ten kod ustawia adres sieci Web, które jest wpisane w polu tekstowym jako miejsce docelowe dla przeglądarki sieci Web. Jeśli adres nie jest prawidłowy, kod powoduje błąd.  
  
3.  Musi również obsługiwać zdarzenia WebFrame_Navigated:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Skompiluj rozwiązanie.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Dodawanie kontrolki użytkownika do strony początkowej  
 Aby udostępnić ten formant do projektu strony początkowej w pliku projektu strony początkowej, Dodaj odwołanie do nowej biblioteki formantu. Następnie można dodać kontrolki znaczników XAML strony początkowej.  
  
1.  W **Eksploratora rozwiązań**, w projekcie strony początkowej, kliknij prawym przyciskiem myszy **odwołania** , a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2.  Na **projekty** wybierz opcję **WebUserControl** , a następnie kliknij przycisk **OK**.  
  
3.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Tworzenie rozwiązania udostępnia kontrolkę użytkownika IntelliSense dla innych plików w rozwiązaniu.  
  
 Aby dodać kontrolki do znaczników strony początkowej XAML, Dodaj odwołanie do zestawu przestrzeni nazw, a następnie umieszczanie kontrolki na stronie.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Aby dodać kontrolki znaczników  
  
1.  W **Eksploratora rozwiązań**, otwórz plik .xaml strony początkowej.  
  
2.  W **XAML** okienka, Dodaj następujące deklaracji przestrzeni nazw na najwyższym poziomie <xref:System.Windows.Controls.Grid> elementu.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  W **XAML** okienka, przewiń do \<siatki > sekcji.  
  
     Sekcja zawiera <xref:System.Windows.Controls.TabControl> element <xref:System.Windows.Controls.Grid> elementu.  
  
4.  Dodaj \<TabControl > zawierające element \<TabItem > zawiera odwołanie do formantu użytkownika.  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 Teraz możesz przetestować formantu.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Testowanie ręcznie utworzonych niestandardowej strony początkowej  
  
1.  Kopiowanie pliku XAML oraz wszelkich obsługi plików tekstowych i znaczników pliki do **%USERPROFILE%\My 2015\StartPages Documents\Visual Studio\\**  folderu.  
  
2.  Jeśli stronę początkową odwołuje się do formantów ani typów w zestawach, które nie są instalowane przez program Visual Studio, skopiuj zestawy, a następnie wklej je w *folder instalacji programu Visual Studio***\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Wpisz w wierszu polecenia programu Visual Studio **devenv/rootsuffix Exp** otworzyć eksperymentalne wystąpienie programu Visual Studio.  
  
4.  W eksperymentalnym wystąpieniu, przejdź do **narzędzia / Opcje / środowiska / uruchamiania** strony i wybierz plik XAML z **dostosowanie strony początkowej** listy rozwijanej.  
  
5.  Na **widoku** menu, kliknij przycisk **— strona początkowa**.  
  
     Powinien zostać wyświetlony stronę początkową niestandardowych. Jeśli chcesz zmienić wszystkie pliki, możesz musi zamknąć eksperymentalne wystąpienie programu, zmiany, skopiuj i Wklej zmienionych plików, a następnie ponownie otwórz eksperymentalne wystąpienie, aby zobaczyć zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrole kontenerów WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [Przewodnik: dodawanie niestandardowych elementów XAML do strony początkowej](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)