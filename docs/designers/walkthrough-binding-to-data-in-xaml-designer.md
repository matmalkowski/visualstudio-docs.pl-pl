---
title: "Wskazówki: Powiązanie z danymi w Projektancie XAML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 4e2192a7fbcf2491a0e131ee6d6df0ead16238fd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Wskazówki: Powiązanie z danymi w Projektancie XAML
W Projektancie XAML za pomocą obszaru roboczego i w oknie właściwości można ustawić właściwości powiązania danych. Przykład, w tym przewodniku pokazano, jak wiązanie danych do formantu. W szczególności przewodnika pokazano, jak utworzyć prostą klasę koszyka zakupów zawierający [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) o nazwie `ItemCount`, a następnie powiązać `ItemCount` właściwości **tekst** właściwości z [blok tekstu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) formantu.  
  
### <a name="to-create-a-class-to-use-as-a-data-source"></a>Aby utworzyć klasę do użycia jako źródło danych  
  
1.  Na **pliku** menu, wybierz **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, albo wybierz **Visual C#** lub **Visual Basic** węzła, rozwiń węzeł **pulpitu systemu Windows** węzeł, a następnie Wybierz **aplikacji WPF** szablonu.  
  
3.  Nazwij projekt **BindingTest**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  Otwórz plik MainWindow.xaml.cs (lub MainWindow.xaml.vb) i Dodaj następujący kod. W języku C#, należy dodać kodu w `BindingTest` przestrzeni nazw (przed ostatnim zamykający nawias okrągły w pliku). W języku Visual Basic wystarczy dodać nową klasę.  
  
    ```csharp  
    public class ShoppingCart : DependencyObject  
    {  
        public int ItemCount  
        {  
            get { return (int)GetValue(ItemCountProperty); }  
            set { SetValue(ItemCountProperty, value); }  
        }  
  
        public static readonly DependencyProperty ItemCountProperty =  
             DependencyProperty.Register("ItemCount", typeof(int),  
             typeof(ShoppingCart), new PropertyMetadata(0));  
    }  
  
    ```  
  
    ```vb  
    Public Class ShoppingCart  
        Inherits DependencyObject  
  
        Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(  
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))  
        Public Property ItemCount As Integer  
            Get  
                ItemCount = CType(GetValue(ItemCountProperty), Integer)  
            End Get  
            Set(value As Integer)  
                SetValue(ItemCountProperty, value)  
            End Set  
        End Property  
    End Class  
    ```  
  
     Ten kod ustawia wartość 0 jako domyślna liczba elementów przy użyciu [obiekt PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) obiektu.  
  
5.  Na **pliku** menu, wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Aby powiązać właściwość wartość elementu ItemCount blok tekstu formantu  
  
1.  W Eksploratorze rozwiązań Otwórz menu skrótów dla MainWindow.xaml i wybierz polecenie **Widok projektanta**.  
  
2.  W przyborniku wybierz [siatki](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) sterować i dodaj go do formularza.  
  
3.  Z `Grid` zaznaczone, w oknie właściwości wybierz **nowy** znajdujący się obok **DataContext** właściwości.  
  
4.  W **Wybieranie obiektu** okna dialogowego upewnij się, że **Pokaż wszystkie zestawy** pole wyboru jest wyczyszczone, wybierz **ShoppingCart** w obszarze **BindingTest** przestrzeni nazw, a następnie wybierz pozycję **OK** przycisku.  
  
     Na poniższej ilustracji pokazano **Wybieranie obiektu** okno dialogowe z **ShoppingCart** wybrane.  
  
     ![Okno dialogowe Wybieranie obiektu](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5.  W **przybornika**, wybierz `TextBlock` sterowania, aby dodać go do formularza.  
  
6.  Z `TextBlock` formantu w oknie właściwości wybierz znacznik właściwości z prawej strony **tekst** właściwości, a następnie wybierz **Utwórz powiązanie danych**. (Znacznik właściwości wygląda na małe pole).  
  
7.  W przypadku tworzenia powiązania danych okno dialogowe, w **ścieżki** wybierz **wartość elementu ItemCount: (int32)** właściwości, a następnie wybierz **OK** przycisku.  
  
     Na poniższej ilustracji pokazano **utworzyć powiązania danych** okno dialogowe z **wartość elementu ItemCount** wybrane właściwości.  
  
     ![Powiązanie danych okno dialogowe Tworzenie](../designers/media/xaml_create_data_binding.png "xaml_create_data_binding")  
  
8.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     `TextBlock` Kontroli powinny być widoczne wartość domyślna 0 jako tekst.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [Konwerter wartości, okno dialogowe Dodawanie](https://msdn.microsoft.com/en-us/c5f3d110-a541-4b55-8bca-928f77778af8)