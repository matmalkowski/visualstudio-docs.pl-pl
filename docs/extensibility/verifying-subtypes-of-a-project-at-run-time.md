---
title: Weryfikowanie podtypów projektu w czasie wykonywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8898da6850c01c1a248b57b0fbc5f46be2a8ff4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
 [Właściwości i metody rozszerzane przez podtypy projektów](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)