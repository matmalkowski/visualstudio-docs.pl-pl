---
title: "Utrwalanie właściwości elementu projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61a477fa760a2ef9026b06facc8bc592706c5dd3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="persisting-the-property-of-a-project-item"></a>Utrwalanie właściwości elementu projektu
Może zajść potrzeba utrwalenia właściwości dodane do elementu projektu, takie jak autor pliku źródłowego. Można to zrobić, przechowując właściwość w pliku projektu.  
  
 Pierwszy krok w celu utrwalenia właściwość w pliku projektu jest uzyskanie hierarchii projektu jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu. Ten interfejs można uzyskać przy użyciu automatyzacji lub za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Po uzyskaniu interfejsu można go określić zaznaczonego elementu projektu. Po utworzeniu identyfikator elementu projektu, można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> można dodać właściwości.  
  
 W poniższych procedur można utrwalić właściwości VsPkg.cs `Author` z wartością `Tom` w pliku projektu.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Aby uzyskać hierarchii projektu za pomocą obiektu DTE  
  
1.  Dodaj następujący kod do VSPackage:  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Aby zachować właściwości elementu projektu o obiekt DTE  
  
1.  Dodaj następujący kod do kodu podanego w tej metodzie w poprzedniej procedurze:  
  
    ```csharp  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Aby uzyskać hierarchii projektu przy użyciu IVsMonitorSelection  
  
1.  Dodaj następujący kod do VSPackage:  
  
    ```csharp  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2.  
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Aby zachować właściwości elementu wybranego projektu, podane hierarchii projektu  
  
1.  Dodaj następujący kod do kodu podanego w tej metodzie w poprzedniej procedurze:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>Aby sprawdzić, czy właściwość jest trwały.  
  
1.  Uruchom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i otworzyć lub utworzyć rozwiązanie.  
  
2.  Wybierz projekt elementu VsPkg.cs w **Eksploratora rozwiązań**.  
  
3.  Użyj punkt przerwania lub w przeciwnym razie określenia załadowaniu VSPackage i czy SetItemAttribute jest uruchomiony.  
  
    > [!NOTE]
    >  Można automatycznie załadować pakiet VSPackage w kontekście interfejsu użytkownika <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>. Aby uzyskać więcej informacji, zobacz [ładowania VSPackages](../extensibility/loading-vspackages.md).  
  
4.  Zamknij [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , a następnie otwórz plik projektu w Notatniku. Powinny pojawić się \<autora > tagu o wartości Tomasz, w następujący sposób:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia niestandardowe](../extensibility/internals/custom-tools.md)