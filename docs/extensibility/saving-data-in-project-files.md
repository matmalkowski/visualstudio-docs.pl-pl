---
title: Zapisywanie danych w plikach projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35514385a4ed1d28052ebb21d12ed0b053dd52dc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="saving-data-in-project-files"></a>Zapisywanie danych w plikach projektu
Podtyp projektu można zapisywać i pobrać dane specyficzne dla podtypu w pliku projektu. Zarządzany pakiet Framework (MPF) udostępnia dwa interfejsy do wykonania tego zadania:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Interfejs umożliwiający dostęp do wartości właściwości z **MSBuild** sekcji w pliku projektu. Metody dostarczone przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> może być wywoływany przez dowolnego użytkownika, w miarę potrzeb użytkowników, aby załadować lub zapisać kompilacji powiązane dane.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Służy do utrwalenia danych powiązanych z systemem innym niż kompilacji w dowolnych XML. Metody dostarczone przez <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> są wywoływane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy każdym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musi być zachowany danych powiązanych z systemem innym niż kompilacji w pliku projektu.  
  
 Aby uzyskać więcej informacji na temat sposobu utrwalić kompilacji i dane związane z systemem innym niż kompilacji, zobacz [przechowywanie danych w pliku projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="saving-and-retrieving-build-related-data"></a>Dane dotyczące zapisywania i pobierania kompilacji  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>Aby zapisać kompilacji powiązanych danych w pliku projektu  
  
-   Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodę, aby zapisać Pełna ścieżka pliku projektu.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Można pobrać kompilacji powiązane dane z pliku projektu  
  
-   Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> metody można pobrać pełnej ścieżki pliku projektu.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## <a name="saving-and-retrieving-non-build-related-data"></a>Zapisywania i pobierania z systemem innym niż kompilacji powiązane dane  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>Aby zapisać kompilacji z systemem innym niż powiązanych danych w pliku projektu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> metodę, aby ustalić, czy fragmentu XML został zmieniony od momentu jego ostatniego zapisane w jego bieżący plik.  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metody można zapisać danych XML w pliku projektu.  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Do pobierania danych powiązanych z systemem innym niż kompilacji w pliku projektu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> metodę, aby zainicjować właściwości rozszerzenia projektu i innych danych niezależny od kompilacji. Ta metoda jest wywoływana, gdy nie ma żadnych danych konfiguracji XML w pliku projektu.  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> metodę, aby załadować dane XML z pliku projektu.  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  Wszystkie przykładowych kodów podanych w tym temacie stanowią część większego przykładu w [przykłady VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Zobacz też  
 [Utrwalanie danych w pliku projektu programu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)