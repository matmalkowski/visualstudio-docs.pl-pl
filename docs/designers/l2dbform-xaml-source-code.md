---
title: Kod źródłowy L2DBForm.XAML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11bad4bf923f3ed0fad7fe3ccf3618877727c6a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="l2dbformxaml-source-code"></a>Kod źródłowy L2DBForm.XAML
Ten temat zawiera i opisuje źródłowy plik XAML dla [WPF danych powiązania za pomocą LINQ do XML przykład](../designers/wpf-data-binding-using-linq-to-xml-example.md), L2DBForm.xaml.  
  
## <a name="overall-ui-structure"></a>Ogólna struktura interfejsu użytkownika  
 Podobnie jak w typowej w projekcie WPF, ten plik zawiera jeden element nadrzędny <xref:System.Windows.Window> — element XML skojarzone z klasy pochodnej `L2XDBFrom` w `LinqToXmlDataBinding` przestrzeni nazw.  
  
 Obszar klienta znajduje się w obrębie <xref:System.Windows.Controls.StackPanel> uzyskuje światła niebieskie tło. Panel ten zawiera cztery <xref:System.Windows.Controls.DockPanel> interfejsu użytkownika sekcje oddzielone <xref:System.Windows.Controls.Separator> pasków. Celem tych sekcjach opisano w **uwagi** w [poprzedniego tematu](../designers/walkthrough-linqtoxmldatabinding-example.md).  
  
 Każda sekcja zawiera etykietę, którą identyfikuje ją. Pierwsze dwie sekcje tej etykiecie jest obrócony o 90 stopni za pośrednictwem <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. W pozostałej części sekcji zawiera elementy interfejsu użytkownika należy celem tej sekcji: bloki tekstu, pól tekstowych, przycisków i tak dalej. Czasami element podrzędny <xref:System.Windows.Controls.StackPanel> służy do Dopasuj tych formantów podrzędnych.  
  
## <a name="window-resource-section"></a>Sekcja zasobów okna  
 Otwarcie `<Window.Resources>` tagu wiersza 9 wskazuje początek sekcji zasobów okna. Kończy się w wierszu 35 tagu zamykającego.  
  
 `<ObjectDataProvider>` Deklaruje tagu, który obejmuje 11 do 25 wierszy, <xref:System.Windows.Data.ObjectDataProvider>nazwanego `LoadedBooks`, która używa <xref:System.Xml.Linq.XElement> jako źródło. To <xref:System.Xml.Linq.XElement> jest inicjowany przez podczas analizowania osadzonego dokumentu XML ( `CDATA` elementu). Należy zauważyć, że biały znak jest zachowywana przy deklarowaniu osadzonych dokumentu XML, a także podczas analizowania. Wykonano ponieważ <xref:System.Windows.Controls.TextBlock> formant, który służy do wyświetlania raw XML, nie ma nie XML specjalne formatowanie możliwości.  
  
 Ponadto <xref:System.Windows.DataTemplate> o nazwie `BookTemplate` jest zdefiniowany w wierszach 28 za pośrednictwem 34. Ten szablon będzie używany do wyświetlania wpisy w **listy książek** sekcji interfejsu użytkownika. Używa powiązania danych i LINQ do XML właściwości dynamicznych pobieranie książki identyfikator i nazwa za pośrednictwem następujących przydziałów:  
  
```  
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"  
```  
  
## <a name="data-binding-code"></a>Kod powiązania danych  
 Oprócz <xref:System.Windows.DataTemplate> elementu powiązania danych jest używany w wielu innych miejsc, w tym pliku.  
  
 W otwarcia `<StackPanel>` tagu wiersza 38 <xref:System.Windows.FrameworkElement.DataContext%2A> ma ustawioną właściwość tego zespołu `LoadedBooks` dostawcy danych.  
  
```  
DataContext="{Binding Source={StaticResource LoadedBooks}}  
```  
  
 Dzięki temu (w wierszu 46) dla <xref:System.Windows.Controls.TextBlock> o nazwie `tbRawXml` do wyświetlania przez powiązanie do tego dostawcy danych raw XML `Xml` właściwości:  
  
```  
Text="{Binding Path=Xml}"   
```  
  
 <xref:System.Windows.Controls.ListBox> w **listy książek** sekcji interfejsu użytkownika w wierszach 58 za pośrednictwem 62, ustawia szablon jego wyświetlania elementów do `BookTemplate` zdefiniowane w sekcji zasobów okno:  
  
```  
ItemTemplate ="{StaticResource BookTemplate}"   
```  
  
 Następnie wierszach 59 za pośrednictwem 62 rzeczywistymi wartościami książek są powiązane z tej listy:  
  
```  
<ListBox.ItemsSource>  
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
</ListBox.ItemsSource>  
```  
  
 Trzeci sekcji interfejsu użytkownika, **edytować wybraną książkę**, najpierw wiąże <xref:System.Windows.FrameworkElement.DataContext%2A> elementu nadrzędnego <xref:System.Windows.Controls.StackPanel> do aktualnie wybranego elementu z **listy książek** sekcji interfejsu użytkownika (wiersza 82):  
  
```  
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"  
```  
  
 Następnie używa powiązanie dwukierunkowe danych tak, aby bieżące wartości elementów książki są wyświetlane na i aktualizowane w polach tekstowych wyświetlanych w tym panelu. Powiązywanie danych do właściwości dynamicznych jest podobny do używanego w `BookTemplate` szablon danych:  
  
```  
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"  
```  
  
 W ostatniej sekcji interfejsu użytkownika **Dodawanie nowej książki**, nie używa danych powiązania w jego kod XAML; zamiast tego taki kod znajduje się w jego obsługa kodu w pliku L2DBForm.xaml.cs zdarzeń.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
  
> [!NOTE]
>  Firma Microsoft zaleca, skopiuj następujący kod poniżej w edytorze kodu, takich jak C# Edytor kodu źródłowego w programie Visual Studio, aby numery wierszy są łatwiejsze do śledzenia.  
  
### <a name="code"></a>Kod  
  
```xml  
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:system="clr-namespace:System;assembly=mscorlib"  
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"  
    xmlns:local="clr-namespace:LinqToXmlDataBinding"  
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">  
  
    <Window.Resources>  
        <!-- Books provider and inline data -->  
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">  
            <ObjectDataProvider.MethodParameters>  
                <system:String xml:space="preserve">  
<![CDATA[  
<books xmlns="http://www.mybooks.com">  
  <book id="0">book zero</book>  
  <book id="1">book one</book>  
  <book id="2">book two</book>  
  <book id="3">book three</book>  
</books>  
]]>                  
                </system:String>  
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>  
            </ObjectDataProvider.MethodParameters>  
        </ObjectDataProvider>  
  
        <!-- Template for use in Books List listbox. -->  
        <DataTemplate x:Key="BookTemplate">  
            <StackPanel Orientation="Horizontal">  
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>  
                <TextBlock Margin="3" Text="-"/>  
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>  
            </StackPanel>  
        </DataTemplate>  
    </Window.Resources>  
  
    <!-- Main visual content container -->  
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">  
        <!-- Raw XML display section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML  
            <Label.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Label.LayoutTransform>  
            </Label>  
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- List box to display all books section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List  
                <Label.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Label.LayoutTransform>  
            </Label>  
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">  
                <ListBox.ItemsSource>  
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
                </ListBox.ItemsSource>  
            </ListBox>  
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">      
            <Button.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Button.LayoutTransform>  
            </Button>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Edit current selection section -->  
        <DockPanel Margin="5">  
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">  
                    Changes are live!  
                <TextBlock.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </TextBlock.LayoutTransform>  
            </TextBlock>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>      
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book ID and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book Value and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Add new book section -->  
        <DockPanel Margin="5">  
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book  
                <Button.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Button.LayoutTransform>  
            </Button>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>  
                <StackPanel Margin="1">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="tbAddID" Width="410">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="tbAddValue" Width="410" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
    </StackPanel>  
</Window>  
  
```  
  
### <a name="comments"></a>Komentarze  
 C# kodu źródłowego dla programów obsługi zdarzeń skojarzonych z elementów interfejsu użytkownika WPF, zobacz [kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Przykład LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)