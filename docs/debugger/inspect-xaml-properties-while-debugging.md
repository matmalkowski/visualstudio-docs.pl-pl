---
title: "Sprawdzanie właściwości XAML podczas debugowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f587c0241452d995a6676ca16d878c775da4750f
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="inspect-xaml-properties-while-debugging"></a>Sprawdzanie właściwości XAML podczas debugowania
Można uzyskać w czasie rzeczywistym widok kodu XAML uruchomionego za pomocą **dynamicznym drzewie wizualnym** i **Live Explorer właściwości**. Te narzędzia umożliwiają widoku drzewa elementów interfejsu użytkownika w uruchomionej aplikacji XAML i wyświetlić właściwości środowisko uruchomieniowe dowolny element interfejsu użytkownika, którą wybierzesz.  
  
 Te narzędzia można użyć w następujących konfiguracji:  
  
|Typ aplikacji|System operacyjny i narzędzia|  
|-----------------|--------------------------------|  
|Aplikacje systemu Windows Presentation Foundation (4.0 i nowsze)|Windows 7 i nowsze|  
|Windows 8.1 i Windows Phone 8.1 aplikacji|Windows 10 i nowsze, z [systemu Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
|Aplikacje uniwersalne systemu Windows|Windows 10 i nowsze, z [systemu Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Trwa wyszukiwanie elementów dynamiczne drzewo wizualne  
 Rozpocznijmy bardzo prostą aplikację WPF, która zawiera widok listy i przycisk. Za każdym razem, gdy przycisk, inny element został dodany do listy. Parzystych elementy mają kolor szary, a elementy o numerach nieparzystych są kolor żółty.  
  
 Tworzenie nowej aplikacji WPF C# (Plik > Nowy > Projekt, a następnie wybierz C# i znaleźć w aplikacji WPF). Nadaj mu nazwę **TestXAML**.  
  
 Zmień MainWindow.xaml na następujący:  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Dodaj następujący program obsługi poleceń w pliku MainWindow.xaml.cs:  
  
```csharp 
int count;

private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Skompiluj projekt i Rozpocznij debugowanie. (Konfiguracja kompilacji musi być debugowania, a nie wersji. Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).)  
  
 Po wyświetleniu okna, kliknij przycisk **Dodaj element** przycisk kilka razy. Powinny pojawić się dane podobne do poniższych:  
  
 ![Okno główne aplikacji](../debugger/media/livevisualtree-app.png "LiveVIsualTree aplikacji")  
  
 Teraz otworzyć **dynamicznym drzewie wizualnym** okna (**Debuguj > Windows > dynamicznym drzewie wizualnym**, lub znajdź go z lewej strony IDE). Przeciągnij od położenia dokowania, więc można przyjrzymy się to okno i **Live właściwości** okna obok siebie. W **dynamicznym drzewie wizualnym** okna, rozwiń węzeł **ContentPresenter** węzła. Powinien on zawierać węzły dla przycisku i pola listy. Rozwiń pole listy (i następnie **ScrollContentPresenter** i **ItemsPresenter**) można znaleźć na liście elementów. Okno powinien wyglądać następująco:  
  
 ![Obiekty ListBoxItem w dynamiczne drzewo wizualne obiekcie](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")  
  
 Wróć do okna aplikacji i dodać kilka więcej elementów. Powinny pojawić się więcej elementów pole listy są wyświetlane w **dynamicznym drzewie wizualnym**.  
  
 Teraz Przyjrzyjmy się jeden z elementów pole listy właściwości. Wybierz pierwszy element pole listy w **dynamicznym drzewie wizualnym** i kliknij przycisk **Pokaż właściwości** ikonę na pasku narzędzi. **Live Explorer właściwość** powinna zostać wyświetlona. Należy pamiętać, że **zawartości** pole jest "Item1" i **tła** pole jest **#FFFFFFE0** (żółty światła). Wróć do **dynamicznym drzewie wizualnym** i wybierz pozycję drugiego elementu pola listy. **Live Explorer właściwości** powinien pokazują, że **zawartości** pole jest "Item2" i **tła** pole jest **#FFD3D3D3** (światła szarym ).  
  
 Rzeczywiste struktury XAML ma wiele elementów, które prawdopodobnie nie masz bezpośrednio zainteresowani, a jeśli nie znasz również kod może być czas twardych nawigowanie po drzewie, aby dowiedzieć się, czego szukasz. Dlatego **dynamicznym drzewie wizualnym** ma kilka sposobów umożliwiające korzystanie z interfejsu użytkownika aplikacji w celu znalezienia element do sprawdzenia.  
  
 **Włącz zaznaczanie w uruchomionej aplikacji**. Można włączyć ten tryb, po wybraniu lewy przycisk na **dynamicznym drzewie wizualnym** paska narzędzi. W tym trybie można wybrać elementu interfejsu użytkownika w aplikacji i **dynamicznym drzewie wizualnym** (i **Live podglądu właściwości**) automatycznie aktualizowany, aby wyświetlić węzeł w drzewie odpowiadający tego elementu i jego właściwości.  
  
 **Wyświetl moduły definiowania układu kodu w uruchomionej aplikacji**. Po wybraniu przycisku, który jest od razu po prawej stronie przycisku wyboru Włącz można włączyć ten tryb. Gdy **Wyświetl moduły definiowania układu kodu** jest włączona, ta powoduje, że okno aplikacji do Pokaż linie poziome i pionowe wzdłuż granice wybranego obiektu pozwala zobaczyć, co powoduje wyrównanie, a także prostokąty marginesów. Na przykład włączyć zarówno **Włącz zaznaczanie** i **Układ wyświetlania** na i wybierz **Dodaj element** bloku tekstu w aplikacji. Powinny pojawić się węzła bloku tekstu w **dynamicznym drzewie wizualnym** i tekst blok właściwości w **Live podglądu właściwości**, oraz poziome i pionowe wierszach zakresem bloku tekstu.  
  
 ![LivePropertyViewer w DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Wyświetl podgląd zaznaczenia**. W tym trybie można włączyć, wybierając trzeci przycisk z lewej strony na pasku narzędzi w dynamicznym drzewie wizualnym. W tym trybie pokazuje XAML, w którym element został zadeklarowany, jeśli użytkownik ma dostęp do kodu źródłowego aplikacji. Wybierz **Włącz zaznaczanie** i **podgląd zaznaczenia**, a następnie wybierz przycisk w naszej aplikacji testu. Otwiera plik MainWindow.xaml w programie Visual Studio i kursor znajduje się w wierszu, której zdefiniowano przycisku.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Za pomocą narzędzi XAML z uruchomionymi aplikacjami  
 Można użyć tych narzędzi XAML, nawet wtedy, gdy nie ma kodu źródłowego. Po dołączeniu do uruchomionej aplikacji XAML, można użyć **dynamicznym drzewie wizualnym** na elementy interfejsu użytkownika tej aplikacji za. Oto przykład, przy użyciu tej samej aplikacji test WPF używanych przed.  
  
1.  Uruchom **TestXaml** aplikacji w konfiguracji wydanie. Nie można dołączyć do procesu, który jest uruchomiony w **debugowania** konfiguracji.  
  
2.  Otwórz drugie wystąpienie programu Visual Studio, a następnie kliknij przycisk **Debuguj > dołączyć do procesu**. Znajdź **TestXaml.exe** na liście dostępnych procesów, a następnie kliknij przycisk **Attach**.  
  
3.  Aplikacja rozpoczyna działanie.  
  
4.  Drugie wystąpienie programu Visual Studio Otwórz **dynamicznym drzewie wizualnym** (**Debuguj > Windows > dynamicznym drzewie wizualnym**). Powinny pojawić się **TestXaml** elementy interfejsu użytkownika i powinno być możliwe do manipulowania nimi jak podczas debugowania aplikacji bezpośrednio.