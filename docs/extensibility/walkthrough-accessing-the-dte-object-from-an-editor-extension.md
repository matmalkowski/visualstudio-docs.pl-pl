---
title: 'Wskazówki: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia Edytora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b888136f51e7893c6ad44ab888d8079ee92d8edf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139643"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Wskazówki: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia Edytora
W VSPackages, można uzyskać obiektu DTE przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody z typem obiektu DTE. Rozszerzenia Managed Extensibility Framework (MEF), umożliwia importowanie <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , a następnie wywołać <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody z typem <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Pobieranie obiektu DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Aby uzyskać obiektu DTE z element ServiceProvider  
  
1.  Tworzenie projektu VSIX C# o nazwie `DTETest`. Dodaj szablon elementu klasyfikatora edytora i nadaj mu nazwę `DTETest`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Dodaj następujące odwołania do zestawów do projektu:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Przejdź do pliku DTETest.cs i dodaj następującą `using` dyrektywy:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  W `GetDTEProvider` klasy, zaimportuj <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  W `GetClassifier()` metody, Dodaj następujący kod.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Jeśli użytkownik musi używać <xref:EnvDTE80.DTE2> interfejsu, można rzutować obiektu DTE do niego.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)