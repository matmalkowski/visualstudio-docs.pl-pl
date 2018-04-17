---
title: Rozszerzanie w oknie danych wyjściowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b9a8b260c1a3cab126d19f0cedc0c1e5362cf81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-output-window"></a>Rozszerzanie w oknie danych wyjściowych
**Dane wyjściowe** okna jest zestawem okienek tekstu odczytu/zapisu. Visual Studio ma te wbudowane okienka: **kompilacji**, w poszczególnych projektach przekazywania wiadomości o kompilacjach i **ogólne**, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komunikuje się komunikaty o IDE. Projekty odwołać się do **kompilacji** automatycznie za pomocą okienka <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metod interfejsu i Visual Studio zapewnia bezpośredni dostęp do **ogólne** okienko za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Usługa. Oprócz wbudowanych okienka można utworzyć i zarządzać własnego niestandardowego okienka.  
  
 Można kontrolować **dane wyjściowe** okna bezpośrednio za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Interfejs, który jest oferowany przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> usługi, definiuje metody tworzenia, pobierania i niszczenie **dane wyjściowe** okienka. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Interfejs definiuje metody przedstawiający okienka, ukrywanie okienka i manipulowanie tekstu. Alternatywny sposób kontrolowania **dane wyjściowe** okno jest za pośrednictwem <xref:EnvDTE.OutputWindow> i <xref:EnvDTE.OutputWindowPane> obiektów w modelu obiektów programu Visual Studio automatyzacji. Te obiekty Hermetyzowanie prawie wszystkie funkcje <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów. Ponadto <xref:EnvDTE.OutputWindow> i <xref:EnvDTE.OutputWindowPane> obiektów dodać niektóre funkcje wyższego poziomu, aby ułatwić wyliczyć **dane wyjściowe** okienka i pobrać tekst z okienka.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Tworzenie rozszerzenia, która używa w okienku danych wyjściowych  
 Istnieje możliwość rozszerzenia, które wykonuje różne aspekty w okienku danych wyjściowych.  
  
1.  Tworzenie projektu VSIX o nazwie `TestOutput` za pomocą polecenia menu o nazwie **TestOutput**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Dodaj następujące informacje:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  W TestOutput.cs, dodaj następującą instrukcję using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  W TestOutput.cs Usuń metody ShowMessageBox. Dodaj następujące szkieletu metody:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  W Konstruktorze TestOutput zmienić OutputCommandHandler program obsługi poleceń. Poniżej przedstawiono część, które umożliwia dodanie polecenia:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  W poniższych rozdziałach mają różne metody, które przedstawiono różne sposoby postępowania z okienku danych wyjściowych. Możesz wywołać treści metody OutputCommandHandler() tych metod. Na przykład następujący kod dodaje metody CreatePane() podanej w następnej sekcji.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Tworzenie okna dane wyjściowe z IVsOutputWindow  
 W tym przykładzie pokazano, jak utworzyć nową **dane wyjściowe** okienka przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfejsu.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Po dodaniu tej metody do rozszerzenia podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony **dane wyjściowe** okna z informacją nagłówka **wyświetlane dane wyjściowe z: CreatedPane** i wyrazy **to okienko utworzony** w okienku samej siebie.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Tworzenie okna dane wyjściowe z OutputWindow  
 W tym przykładzie przedstawiono sposób tworzenia **dane wyjściowe** okienka przy użyciu <xref:EnvDTE.OutputWindow> obiektu.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Mimo że <xref:EnvDTE.OutputWindowPanes> kolekcji umożliwia pobieranie **dane wyjściowe** okienka przez jego tytuł, tytułów okienku są nie musi być unikatowy. W przypadku wątpliwości unikatowości tytuł, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metoda pobierania okienku poprawne przez jego identyfikator GUID.  
  
 Jeśli dodasz tej metody do rozszerzenia podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony w oknie danych wyjściowych z informacją nagłówka **Pokaż dane wyjściowe z: DTEPane** i wyrazy **dodane okienku DTE** w okienku samej siebie.  
  
## <a name="deleting-an-output-window"></a>Usuwanie okno danych wyjściowych  
 W tym przykładzie pokazano, jak usunąć **dane wyjściowe** okienka.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Jeśli dodasz tej metody do rozszerzenia podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony w oknie danych wyjściowych z informacją nagłówka **Pokaż dane wyjściowe z: nowe okienko** i wyrazy **dodane okienku utworzony** w okienku samej siebie. Jeśli klikniesz przycisk **wywołania TestOutput** ponownie polecenie okienku zostanie usunięta.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Pobieranie w okienku ogólne okno danych wyjściowych  
 W tym przykładzie pokazano, jak pobrać wbudowane **ogólne** okienku **dane wyjściowe** okna.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Jeśli dodasz tej metody do rozszerzenia podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony który **dane wyjściowe** okno zawiera wyrazy **znaleźć ogólne Okienko** w okienku.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Pobieranie w okienku w oknie danych wyjściowych kompilacji  
 W tym przykładzie pokazano, jak można znaleźć w okienku kompilacji i zapisywać do niego. Ponieważ w okienku kompilacji nie została aktywowana domyślnie, zostaje uaktywniony on również.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```