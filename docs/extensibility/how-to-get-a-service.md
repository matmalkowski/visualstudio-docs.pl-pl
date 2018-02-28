---
title: "Porady: uzyskiwanie usługi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dd51497bb73981ca81623ad495edc9561e85d3da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-service"></a>Porady: uzyskiwanie usługi
Często muszą pobrać usługi Visual Studio, aby uzyskiwać dostęp do różnych funkcji. Ogólnie rzecz biorąc usługa Visual Studio zawiera jeden lub więcej interfejsów, które są dostępne. Większość usług można uzyskać z pakiet VSPackage.  
  
 Wszelkie pakiet VSPackage, która jest pochodną <xref:Microsoft.VisualStudio.Shell.Package> i który ma zostały prawidłowo ulokowany może poprosić o dowolnej usługi globalne. Ponieważ implementuje klasy pakietu <xref:System.IServiceProvider>, wszelkie pakiet VSPackage, który pochodzi z pakietu jest również dostawcę usług.  
  
 Załadowanie programu Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>, przekazuje on <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody podczas inicjowania. Ta metoda jest wywoływana *lokalizacji* pakiet VSPackage. Klasa pakietu zawijany ten dostawca usług i udostępnia <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodę pobierania usługi.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Pobieranie usługi z zainicjowane pakiet VSPackage  
  
1.  Każde rozszerzenie programu Visual Studio rozpoczyna się od VSIX Projekt wdrożenia, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projektu o nazwie `GetServiceExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# > rozszerzalności**.  
  
2.  Teraz Dodaj szablon elementu polecenia niestandardowych o nazwie **GetServiceCommand**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# > rozszerzalności** i wybierz **polecenia niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **GetServiceCommand.cs**. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowych poleceń [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  W GetServiceCommand.cs Usuń treść metody MenuItemCommand i Dodaj następujący kod:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Ten kod pobiera usługi SVsActivityLog i rzutuje do <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może służyć do zapisu w dzienniku aktywności. Na przykład zobacz [porady: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
5.  W menu Narzędzia w eksperymentalnym wystąpieniu znaleźć **wywołania GetServiceCommand** przycisku. Po kliknięciu tego przycisku powinien zostać wyświetlony komunikat informujący o **znaleziono działanie usługi rejestrowania.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Pobieranie usługi z narzędzia okna lub formantu kontenera  
 Czasami może być konieczne uzyskanie usługi okna narzędzia lub kontrolować kontener, który nie został ulokowany, w przeciwnym razie zostały zlokalizowane z dostawcą usługi, która nie może określić dotyczących usługi, który ma. Na przykład można zapisywać w Dzienniku działania z wewnątrz formantu.  
  
 Statycznych <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metoda zależy od dostawcy usługi z pamięci podręcznej, który został zainicjowany po raz pierwszy żadnych pakiet VSPackage pochodną <xref:Microsoft.VisualStudio.Shell.Package> jest ulokowany.  
  
 Ponieważ wywołania konstruktora pakiet VSPackage przed jest ulokowany pakiet VSPackage, usługi global services są zwykle dostępne z wewnątrz konstruktora pakiet VSPackage. Zobacz [porady: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md) obejście tego problemu.  
  
 Oto przykład sposobem uzyskania usługi w oknie narzędzia lub innych elementów innych niż pakiet VSPackage.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Pobieranie usługi z obiektu DTE  
 Można również uzyskać z usług <xref:EnvDTE.DTEClass> obiektu. Jednak należy uzyskać obiektu DTE jako usługa z pakiet VSPackage, przez wywołanie statycznych <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
 Obiekt DTE implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, którego można użyć w zapytaniu dla usługi przy użyciu <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Oto jak można pobrać usługi z obiekt DTE.  
  
```csharp  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: udostępnianie usługi](../extensibility/how-to-provide-a-service.md)   
 [Przy użyciu i świadczenia usług](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)