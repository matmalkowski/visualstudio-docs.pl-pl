---
title: "Utworzenie okna narzędzia wielu wystąpieniach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cb73a5e5f40d21a5b17faae9602e40f7cd39d48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-multi-instance-tool-window"></a>Utworzenie okna narzędzia wielu wystąpień
Można programu okna narzędzia, dzięki czemu wiele wystąpień mogą być otwarte jednocześnie. Domyślnie narzędzie windows może mieć tylko jedno wystąpienie otworzyć.  
  
 Korzystając z okna narzędzia wielu wystąpień, można wyświetlić kilka powiązanych źródeł informacji w tym samym czasie. Na przykład, możesz zaznaczyć wiele wierszy <xref:System.Windows.Forms.TextBox> kontroli w wielu wystąpieniach okna narzędzia, tak aby kilka fragmentów kodu są równocześnie dostępne podczas programowania sesji. Również na przykład można umieścić <xref:System.Windows.Forms.DataGrid> kontroli i listy rozwijanej pola w oknie narzędzia wielu wystąpień, dzięki czemu można śledzić jednocześnie kilka źródeł danych w czasie rzeczywistym.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Utworzenie okna narzędzia Basic (pojedynczego wystąpienia)  
  
1.  Tworzenie projektu o nazwie **MultiInstanceToolWindow** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okna o nazwie **MIToolWindow**.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji o tworzeniu rozszerzenie z okna narzędzia, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Tworzenie wielu wystąpieniach okna narzędzi  
  
1.  Otwórz **MIToolWindowPackage.cs** plików i Znajdź `ProvideToolWindow` atrybutu. i `MultiInstances=true` parametru, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  W pliku MIToolWindowCommand.cs znaleźć metody ShowToolWindos(). W przypadku tej metody należy wywołać <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> — metoda i zestaw jej `create` flaga `false` tak, aby go iteracji przez istniejące wystąpienia okna narzędzia do dostępnych `id` zostanie znaleziony.  
  
3.  Aby utworzyć wystąpienie okna narzędzia, należy wywołać <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> — metoda i zestaw jej `id` dostępne wartości i jego `create` flaga `true`.  
  
     Domyślnie wartość `id` parametr <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> jest metoda `0`. Dzięki temu okna narzędzia jednego wystąpienia. Aby uzyskać więcej niż jedno wystąpienie ma być obsługiwana każde wystąpienie musi mieć własny unikatowy `id`.  
  
4.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiektu, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Właściwość wystąpienia okna narzędzia.  
  
5.  Domyślnie `ShowToolWindow` metodę, która jest tworzona przez szablon elementu okna narzędzia tworzy okno narzędzi jednego wystąpienia. Poniższy przykład przedstawia sposób modyfikowania `ShowToolWindow` metodę w celu utworzenia wielu wystąpień.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```