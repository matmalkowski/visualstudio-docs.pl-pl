---
title: "Weryfikowanie podtypów projektu w czasie wykonywania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e4ebcf8ca85c0ed6face82dfd91f8c5266013f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Weryfikowanie podtypów projektu w czasie wykonywania
Pakiet VSPackage, który jest zależny od podtypu projektu niestandardowych powinna zawierać logiki do wyszukania podtypu tak, aby go może zakończyć się niepowodzeniem bezpiecznie Jeśli podtyp nie istnieje. Poniższa procedura przedstawia sposób sprawdzić, czy z określonym podtypem.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Aby sprawdzić obecność podtypu  
  
1.  Uzyskaj hierarchii projektu z projektu i rozwiązania obiektów jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektów przez dodanie poniższego kodu do VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Rzutowanie hierarchia <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfejsu.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Pobierz listę identyfikatorów GUID typu projektu w wywołując <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Sprawdź listę dla identyfikatora GUID z określonym podtypem.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Podtypów projektu](../extensibility/internals/project-subtypes.md)   
 [Podtypów projektu](../extensibility/internals/project-subtypes-design.md)   
 [Właściwości i metody przedłużony podtypów projektu](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)