---
title: Dodawanie poleceń programu Visual Studio do strony początkowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87a5e6d29877efb857b846a7b3fac5f19f790d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101797"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Dodawanie poleceń programu Visual Studio do strony początkowej
Po utworzeniu strony początkowej niestandardowe polecenia programu Visual Studio można dodać do niego. W tym dokumencie omówiono różne sposoby Powiąż polecenia programu Visual Studio z obiekty XAML strony początkowej.  
  
 Aby uzyskać więcej informacji dotyczących poleceń w języku XAML, zobacz [droższe — omówienie](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>Dodawanie poleceń również polecenia  
 Utworzone strony początkowej w [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md) dodane <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> i <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> przestrzeni nazw w następujący sposób.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Dodaj inny obszar nazw dla Microsoft.VisualStudio.Shell z zestawu Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Może być konieczne dodanie odwołania do tego zestawu w projekcie).  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Można użyć `vscom:` alias powiązać polecenia programu Visual Studio w języku XAML kontrolki na stronie przez ustawienie <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> właściwości formantu `vscom:VSCommands.ExecuteCommand`. Następnie można ustawić <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> właściwość na nazwę polecenie do wykonania, jak pokazano w poniższym przykładzie.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` Alias, który odwołuje się do schematu XAML, jest wymagany na początku wszystkich poleceń.  
  
 Można ustawić wartości `Command` właściwości dowolne polecenie, które są dostępne z **polecenia** okna. Aby uzyskać listę dostępnych poleceń, zobacz [programu Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).  
  
 Jeśli polecenie, aby dodać wymaga dodatkowych parametrów, można dodać go do wartości `CommandParameter` właściwości. Oddzielne parametry poleceń za pomocą spacji, jak pokazano w poniższym przykładzie.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Podczas wywoływania rozszerzenia polecenia również  
 Polecenia można wywołać z VSPackages zarejestrowanych przy użyciu takiej samej składni, które są używane do wywoływania inne polecenia programu Visual Studio. Na przykład, jeśli jest zainstalowany pakiet VSPackage dodaje **strony głównej** polecenie **widoku** menu, należy wywołać polecenie ustawiając `CommandParameter` do `View.HomePage`.  
  
> [!NOTE]
>  Wywołanie polecenia, który jest skojarzony z pakiet VSPackage po wywołaniu polecenia musi załadować pakietu.  
  
## <a name="adding-commands-from-assemblies"></a>Dodawanie poleceń z zestawów  
 Aby wywołać polecenie z zestawu lub kod dostępu w pakiet VSPackage, który nie jest skojarzony z polecenia menu, należy utworzyć alias dla zestawu, a następnie wywołać alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Aby wywołać polecenie z zestawu  
  
1.  W rozwiązaniu Dodaj odwołanie do zestawu.  
  
2.  W górnej części pliku StartPage.xaml należy dodać dyrektywę przestrzeń nazw dla zestawu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Wywołaj polecenie ustawiając `Command` właściwości obiektu XAML, jak pokazano w poniższym przykładzie.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Należy skopiować z zestawu, a następnie wklej go w... \\ *Folder instalacji programu visual Studio*\Common7\IDE\PrivateAssemblies\ się upewnić, że jest załadowany, przed jego wywołaniu.  
  
## <a name="adding-commands-with-the-dte-object"></a>Dodawanie poleceń za pomocą obiektu DTE  
 Można uzyskać dostępu do obiektu DTE ze strony początkowej, zarówno w znaczniku, jak i w kodzie.  
  
 W znaczniku, można do niego dostęp przy użyciu [powiązanie — rozszerzenie znaczników](/dotnet/framework/wpf/advanced/binding-markup-extension) składni, aby wywołać <xref:EnvDTE.DTE> obiektu. Ta metoda służy do powiązania właściwości proste, takich jak te, które zwracają kolekcje, ale nie można powiązać z metodami lub usług. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.TextBlock> formant, który jest powiązany z <xref:EnvDTE._DTE.Name%2A> właściwości oraz <xref:System.Windows.Controls.ListBox> formant, który wylicza <xref:EnvDTE.Window.Caption%2A> właściwości kolekcji, która jest zwracana w wyniku <xref:EnvDTE._DTE.Windows%2A> właściwości.  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Na przykład zobacz [wskazówki: zapisywanie ustawień użytkownika na stronie Start](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)