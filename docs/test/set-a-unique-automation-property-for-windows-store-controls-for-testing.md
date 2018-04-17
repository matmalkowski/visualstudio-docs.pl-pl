---
title: Ustawianie unikatowej właściwości automatyzacji dla formantów platformy uniwersalnej systemu Windows do testowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: a27b3472080f1b22f0b07b01e92d6a0e5326396e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Ustawianie unikatowej właściwości automatyzacji dla formantów platformy uniwersalnej systemu Windows do testowania

Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows opartych na języku XAML, musi mieć właściwość unikatowy automatyzacji, która identyfikuje każdego formantu.

 Można przypisać unikatowej właściwości automatyzacji na podstawie typu kontrolki XAML w aplikacji. Poniżej przedstawiono sposób przypisać ten unikatowej właściwości automatyzacji w następujących sytuacjach:

-   [Statyczne definicji XAML formantów](#UniquePropertyWindowsStoreControlsStaticXAML)

-   [Przypisz unikatowy automatyzacji właściwości przy użyciu programu Visual Studio i Blend for Visual Studio](#UniquePropertyWindowsStoreControlsExpressionBlend)

-   [Użyj szablonie danych](#UniquePropertyWindowsStoreControlsDataTemplate)

-   [Użyj szablonu formantu](#UniquePropertyWindowsStoreControlsControlTemplate)

-   [Formantów dynamicznych](#UniquePropertyWindowsStoreControlsDynamicControls)

## <a name="use-methods-to-assign-a-unique-automation-property"></a>Użyj metody, aby przypisać unikatowej właściwości automatyzacji

###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Statyczne definicji XAML
 Aby określić unikatowej właściwości automatyzacji dla formantu, który jest zdefiniowany w pliku XAML, można ustawić AutomationProperties.AutomationId lub AutomationProperties.Name jawnie lub niejawnie, jak przedstawiono w przykładach, które należy wykonać. Ustawienia jednej z tych wartości daje kontrolę unikatowej właściwości automatyzacji, który może służyć do identyfikowania formantu, gdy tworzenie kodowanego testu lub Akcja nagrywania interfejsu użytkownika.

 **Ustaw właściwość niejawnie**

Ustaw AutomationProperties.AutomationId **ButtonX** używając właściwości Name w XAML dla formantu.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ustaw AutomationProperties.Name **ButtonY** przy użyciu właściwości zawartości w kodzie XAML dla formantu.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

 **Ustaw jawnie właściwość**

 Ustaw AutomationProperties.AutomationId **ButtonX** jawnie w kodzie XAML dla formantu.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

 Ustaw AutomationProperties.Name **ButtonY** jawnie w kodzie XAML dla formantu.

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Przypisz unikatowy automatyzacji właściwości przy użyciu programu Visual Studio i Blend for Visual Studio
 Aby przypisać unikalną nazwę do interaktywnego elementów, takich jak przyciski, pola listy, pola kombi i pól tekstowych, można użyć programu Visual Studio lub program Blend for Visual Studio. To zapewnia kontrolę unikatową wartość dla AutomationProperties.Name.

 **Visual Studio:** na **narzędzia** menu wskaż **opcje** , a następnie wybierz **Edytor tekstu**, następnie **XAML**, a na końcu **Różne**.

 Wybierz **automatycznie nazwij elementy interakcyjne przy tworzeniu** , a następnie wybierz **OK**.

 ![XAML różne opcje](../test/media/cuit_windowsstoreapp_b.png "CUIT_WindowsStoreApp_B")

 **Program Blend for Visual Studio:** użyj jednej z następujących metod, w tym celu z programu Blend for Visual Studio.

> [!NOTE]
>  Tej metody można używać tylko dla formantów, które są tworzone statycznie przy użyciu kodu XAML.

 **Aby nadać unikatową nazwę istniejących formantów**

 Na **narzędzia** menu, wybierz **elementy interakcyjne nazwa**, jak pokazano poniżej:

 ![Wybierz elementy interakcyjne nazwy z menu narzędzia](../test/media/cuit_windowsstoreproperty_blend_1.png "CUIT_WindowsStoreProperty_Blend_1")

 **Aby automatycznie nadaj unikatową nazwę z formantami, które możesz utworzyć**

 Na **narzędzia** menu wskaż **opcje**, a następnie wybierz pozycję **projektu**. Wybierz **automatycznie nazwij elementy interakcyjne przy tworzeniu** , a następnie wybierz **OK**, jak pokazano poniżej:

 ![Projekt zestawu elementy interakcyjne nazwa](../test/media/cuit_windowsstoreproeprty_blend_2.png "CUIT_WindowsStoreProeprty_Blend_2")

###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Użyj szablonu danych
 Można zdefiniować prostego szablonu przy użyciu ItemTemplate powiązać wartości w polu listy zmiennych przy użyciu następującego kodu XAML.

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

 Za pomocą szablonu i ItemContainerStyle można powiązać wartości do zmiennych przy użyciu następujących XAML:

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

 Dla obu tych przykładów należy następnie zastąpić metodę ToString() ItemSource, jak pokazano w następującym przykładzie kodu. Ten kod upewnia się, że wartość AutomationProperties.Name jest ustawiona i jest unikatowa, ponieważ nie można ustawić unikatowej właściwości automatyzacji dla każdego elementu listy powiązania danych za pomocą powiązania. Ustawianie unikatową wartość dla Properties.Name automatyzacji wystarcza w takim przypadku.

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

###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Użyj szablonu formantu

Za pomocą szablonu formantu, tak aby każde wystąpienie określonego typu uzyskuje unikatowej właściwości automatyzacji, gdy są zdefiniowane w kodzie. Utwórz szablon, aby AutomationProperty wiąże Unikatowy identyfikator w wystąpienia formantu. Następujące XAML przedstawiono jeden ze sposobów tworzenia tego powiązania z szablonem formantu.

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

###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Formantów dynamicznych
 Jeśli masz formantów, które są tworzone dynamicznie w kodzie i nie utworzono statycznie lub za pomocą szablonów w plikach XAML, należy ustawić właściwości zawartości lub nazwa dla formantu. Dzięki temu się, że każdy dynamicznej kontroli unikatowej właściwości automatyzacji. Na przykład jeśli pole wyboru, które można wyświetlić, wybierz element listy, można ustawić te właściwości, jak pokazano poniżej:

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

- [Testowanie aplikacji platformy UWP systemu Windows za pomocą kodowanych testów interfejsu użytkownika](../test/test-windows-store-8-1-apps-with-coded-ui-tests.md)
