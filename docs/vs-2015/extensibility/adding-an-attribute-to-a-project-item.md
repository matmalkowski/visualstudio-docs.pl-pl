---
title: Dodawanie atrybutu do elementu projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55f7c296f79b020b4c5549c8c9103205cc04d009
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676756"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Dodawanie atrybutu do elementu projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Dodawanie atrybutu do elementu projektu](https://docs.microsoft.com/visualstudio/extensibility/adding-an-attribute-to-a-project-item).  
  
Metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pobieranie i ustawianie wartości atrybutów elementu projektu. SetItemAttribute tworzy atrybut, jeśli go jeszcze nie istnieje, dodając go do metadanych elementu projektu.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Dodawanie atrybutu do elementu projektu  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Dodawanie atrybutu do elementu projektu  
  
-   Poniższy kod używa <xref:EnvDTE.DTE> obiektu automatyzacji i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodę, aby dodać atrybut do elementu projektu. Identyfikator elementu projektu jest uzyskiwany z nazwy elementu projektu "program.cs". Atrybut "MyAttribute" zostanie dodany do tego elementu projektu i danej wartości "MyValue".  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Utrwalanie danych w pliku projektu programu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

