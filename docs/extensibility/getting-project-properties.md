---
title: "Pobieranie właściwości projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 58a24a37de7986ef47acb916d488bd4661c5a4d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getting-project-properties"></a>Pobieranie właściwości projektu
W tym przewodniku przedstawiono sposób Wyświetla właściwości projektu w oknie narzędzia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Do tworzenia projektu VSIX i dodać okna narzędzia  
  
1.  Każde rozszerzenie programu Visual Studio rozpoczyna się od VSIX Projekt wdrożenia, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projektu o nazwie `ProjectPropertiesExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Dodaj okna narzędzia przez dodanie szablon elementu okna narzędzia niestandardowa o nazwie `ProjectPropertiesToolWindow`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **okno dialogowe Dodaj nowy element**, przejdź do **elementów Visual C# / rozszerzalności** i wybierz **okna narzędzia niestandardowe**. W **nazwa** u dołu okna dialogowego, Zmień nazwę pliku, aby `ProjectPropertiesToolWindow.cs`. Aby uzyskać więcej informacji o sposobie tworzenia okna narzędzi niestandardowych, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Skompiluj rozwiązanie i sprawdź, czy skompilowany bez błędów.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Aby wyświetlić właściwości projektu w oknie narzędzia  
  
1.  W pliku ProjectPropertiesToolWindowCommand.cs Dodaj następujące instrukcje using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  W ProjectPropertiesToolWindowControl.xaml istniejące przycisk Usuń, a następnie dodaj elementu TreeView z przybornika. Można również usunąć obsługi zdarzeń kliknięcia z pliku ProjectPropertiesToolWindowControl.xaml.cs.  
  
3.  W ProjectPropertiesToolWindowCommand.cs użyj metody ShowToolWindow(), aby otworzyć projekt i odczytywanie ich właściwości, a następnie dodać właściwości do elementu TreeView. Kod ShowToolWindow powinna wyglądać następująco:  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
5.  Otwórz projekt w eksperymentalnym wystąpieniu.  
  
6.  W **widoku / inne okna** kliknij **ProjectPropertiesToolWindow**.  
  
     Powinny pojawić się na drzewie w oknie narzędzia wraz z nazwą pierwszego projektu i jego właściwości projektu.