---
title: Ustawianie unikatowej właściwości automatyzacji dla kontrolek platformy UWP przeznaczonych do testowania
ms.date: 05/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: fbb815dc17e8b71efcefee8410faa01df0914e35
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692359"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Ustawianie unikatowej właściwości automatyzacji dla kontrolek platformy UWP przeznaczonych do testowania

Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows opartych na języku XAML, każdego formantu musi być identyfikowany przez unikatowej właściwości automatyzacji. Można przypisać unikatowej właściwości automatyzacji na podstawie typu kontrolki XAML w aplikacji.

## <a name="static-xaml-definition"></a>Statyczne definicji XAML

Aby określić unikatowej właściwości automatyzacji dla formantu, który jest zdefiniowany w pliku XAML, można ustawić **AutomationProperties.AutomationId** lub **AutomationProperties.Name** jawnie lub niejawnie, jak przedstawiono w przykładach, które należy wykonać. Ustawienia jednej z tych wartości daje kontrolę unikatowej właściwości automatyzacji, który może służyć do identyfikowania formantu, gdy tworzenie kodowanego testu lub Akcja nagrywania interfejsu użytkownika.

### <a name="set-the-property-implicitly"></a>Ustaw właściwość niejawnie

Ustaw **AutomationProperties.AutomationId** do **ButtonX** przy użyciu **nazwa** właściwości w języku XAML dla formantu.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** do **ButtonY** przy użyciu **zawartości** właściwości w języku XAML dla formantu.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Ustaw jawnie właściwość

Ustaw **AutomationProperties.AutomationId** do **ButtonX** jawnie w kodzie XAML dla formantu.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw **AutomationProperties.Name** do **ButtonY** jawnie w kodzie XAML dla formantu.

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Przypisywanie unikatowych nazw

W programie Blend for Visual Studio możesz wybrać opcję, aby przypisać unikalną nazwę do interaktywnego elementów, takich jak przyciski, pola listy, pola kombi i pól tekstowych. Dzięki temu formanty unikatowe wartości **AutomationProperties.Name**.

Aby przypisać unikatowe nazwy istniejących formantów, zaznacz **narzędzia** > **elementy interakcyjne nazwa**.

![Nazwa interaktywne elementy w programie Blend for Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Aby automatycznie nadaj unikatową nazwę nowych formantów, które można dodać, wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego. Wybierz **projektanta XAML** , a następnie wybierz **automatycznie nazwij elementy interakcyjne przy tworzeniu**. Wybierz **OK** aby zamknąć okno dialogowe.

## <a name="use-a-data-template"></a>Użyj szablonu danych

Można zdefiniować przy użyciu prostego szablonu **ItemTemplate** powiązać wartości w polu listy zmiennych:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

Można również użyć szablonu z **ItemContainerStyle** można powiązać wartości do zmiennych:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemContainerStyle>
      <Style TargetType="ListBoxItem">
         <Setter Property="Template">
            <Setter.Value>
               <ControlTemplate TargetType="ListBoxItem">
                  <Grid>
                     <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                  </Grid>
               </ControlTemplate>
            </Setter.Value>
         </Setter>
      </Style>
   </ListBox.ItemContainerStyle>
</ListBox>
```

Oba te przykłady, następnie należy zastąpić **ToString()** metody **ItemSource**, jak pokazano w następującym przykładzie kodu. Ten kod, sprawdza **AutomationProperties.Name** wartość jest ustawiona i jest unikatowa, ponieważ nie można ustawić unikatowej właściwości automatyzacji dla każdego elementu listy powiązane z danymi za pomocą powiązania. Ustawienie unikatową wartość **Properties.Name automatyzacji** w tym przypadku jest wystarczająca.

> [!NOTE]
> W ten sposób wewnętrzny zawartość elementu listy można również można ustawić na ciąg w klasie pracowników przez powiązanie. Jak pokazano w przykładzie, formantu przycisku wewnątrz każdego elementu listy jest przypisany identyfikator unikatowy automatyzacji, czyli identyfikatora pracownika.

```csharp
Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}
```

## <a name="use-a-control-template"></a>Użyj szablonu formantu

Za pomocą szablonu formantu, tak aby każde wystąpienie określonego typu uzyskuje unikatowej właściwości automatyzacji, gdy są zdefiniowane w kodzie. Tworzenie szablonu, aby **AutomationProperty** wiąże Unikatowy identyfikator w wystąpienia formantu. Następujące XAML przedstawiono jeden ze sposobów tworzenia tego powiązania z szablonem sterowania:

```xaml
<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>
```

Podczas definiowania dwa wystąpienia przy użyciu tego szablonu formantu przycisku ustawiony identyfikator automatyzacji unikatowy ciąg zawartości formantów w szablonie, jak pokazano w poniższych XAML:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Formantów dynamicznych

Jeśli masz formantów, które są tworzone dynamicznie w kodzie i nie utworzono statycznie lub za pomocą szablonów w plikach XAML, musisz ustawić **zawartości** lub **nazwa** właściwości formantu. Dzięki temu się, że każdy dynamicznej kontroli unikatowej właściwości automatyzacji. Na przykład jeśli pole wyboru, które można wyświetlić, wybierz element listy, można ustawić te właściwości, jak pokazano poniżej:

```csharp
private void CreateCheckBox(string txt, StackPanel panel)
{
   CheckBox cb = new CheckBox();
   cb.Content = txt; // Sets the AutomationProperties.Name
   cb.Height = 50;
   cb.Width = 100;
   cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
   panel.Children.Add(cb);
}
```

## <a name="see-also"></a>Zobacz także

- [Test aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](../test/test-uwp-app-with-coded-ui-test.md)
