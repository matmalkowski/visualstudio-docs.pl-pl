---
title: 'Wskazówki: Powiązanie z danymi w Projektancie XAML | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a770bd8224906ccd45a2d3f4be9e169368bb20cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Wskazówki: Powiązanie z danymi w Projektancie XAML

W Projektancie XAML za pomocą obszaru roboczego i w oknie właściwości można ustawić właściwości powiązania danych. Przykład, w tym przewodniku pokazano, jak wiązanie danych do formantu. W szczególności przewodnika pokazano, jak utworzyć prostą klasę koszyka zakupów zawierający [DependencyProperty](/uwp/api/Windows.UI.Xaml.DependencyProperty) o nazwie `ItemCount`, a następnie powiązać `ItemCount` właściwości **tekst** właściwości z [blok tekstu](/uwp/api/Windows.UI.Xaml.Controls.TextBlock) formantu.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Aby utworzyć klasę do użycia jako źródło danych

1. Na **pliku** menu, wybierz **nowy**> **projektu**.

1. W **nowy projekt** okna dialogowego, albo wybierz **Visual C#** lub **Visual Basic** węzła, rozwiń węzeł **pulpitu systemu Windows** węzeł, a następnie Wybierz **aplikacji WPF** szablonu.

1. Nazwij projekt **BindingTest**, a następnie wybierz pozycję **OK** przycisku.

1. Otwórz plik MainWindow.xaml.cs (lub MainWindow.xaml.vb) i Dodaj następujący kod. W języku C#, należy dodać kodu w `BindingTest` przestrzeni nazw (przed ostatnim zamykający nawias okrągły w pliku). W języku Visual Basic wystarczy dodać nową klasę.

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

   Ten kod ustawia wartość 0 jako domyślna liczba elementów przy użyciu [obiekt PropertyMetadata](/uwp/api/Windows.UI.Xaml.PropertyMetadata) obiektu.

1. Na **pliku** menu, wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Aby powiązać właściwość wartość elementu ItemCount blok tekstu formantu

1. W Eksploratorze rozwiązań Otwórz menu skrótów dla MainWindow.xaml i wybierz polecenie **Widok projektanta**.

1. W przyborniku wybierz [siatki](/uwp/api/Windows.UI.Xaml.Controls.Grid) sterować i dodaj go do formularza.

1. Z `Grid` zaznaczone, w oknie właściwości wybierz **nowy** znajdujący się obok **DataContext** właściwości.

1. W **Wybieranie obiektu** okna dialogowego upewnij się, że **Pokaż wszystkie zestawy** pole wyboru jest wyczyszczone, wybierz **ShoppingCart** w obszarze **BindingTest** przestrzeni nazw, a następnie wybierz pozycję **OK** przycisku.

     Na poniższej ilustracji pokazano **Wybieranie obiektu** okno dialogowe z **ShoppingCart** wybrane.

     ![Okno dialogowe Wybierz obiekt](../designers/media/blendselectobject.PNG "BlendSelectObject")

1. W **przybornika**, wybierz `TextBlock` sterowania, aby dodać go do formularza.

1. Z `TextBlock` formantu w oknie właściwości wybierz znacznik właściwości z prawej strony **tekst** właściwości, a następnie wybierz **Utwórz powiązanie danych**. (Znacznik właściwości wygląda na małe pole).

1. W przypadku tworzenia powiązania danych okno dialogowe, w **ścieżki** wybierz **wartość elementu ItemCount: (int32)** właściwości, a następnie wybierz **OK** przycisku.

     Na poniższej ilustracji pokazano **utworzyć powiązania danych** okno dialogowe z **wartość elementu ItemCount** wybrane właściwości.

     ![Powiązanie danych okno dialogowe Tworzenie](../designers/media/xaml_create_data_binding.png "xaml_create_data_binding")

1. Naciśnij klawisz **F5** do uruchomienia aplikacji.

     `TextBlock` Kontroli powinny być widoczne wartość domyślna 0 jako tekst.

## <a name="see-also"></a>Zobacz także

[Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)  
[Konwerter wartości, okno dialogowe Dodawanie](https://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8)