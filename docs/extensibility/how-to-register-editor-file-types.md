---
title: "Porady: Rejestrowanie typów plików Edytor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9f2837dff6c5dd62c03da2ab340fca287a1da56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-register-editor-file-types"></a>Porady: Rejestrowanie typów plików edytora
Najprostszym sposobem zarejestrować Edytor typów plików jest za pomocą atrybutów rejestracji w ramach [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] zarządzanych klas framework (MPF) pakietu. W przypadku wdrażania pakietu w trybie macierzystym [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], można również napisać skrypt rejestru, który rejestruje w edytorze i skojarzonych rozszerzeń.  
  
## <a name="registration-using-mpf-classes"></a>Rejestracja przy użyciu klasy MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Aby zarejestrować Edytor typów plików przy użyciu klasy MPF  
  
1.  Podaj <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> klasy przy użyciu odpowiednich parametrów dla edytora w klasie VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Gdzie ". Rozszerzenia, które jest zarejestrowane dla tego edytora jest przykładowe"i"32"jest jej priorytet.  
  
     `projectGuid` Jest identyfikator GUID dla typów plików dodatkowych, zdefiniowanych w <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>. Dostępne są typem dodatkowych plików, dzięki czemu wynikowy plik nie ma być częścią procesu kompilacji.  
  
     `TemplateDir`reprezentuje folder zawierający plików szablonów, które znajdują się przykładowe zarządzanych podstawowego edytora.  
  
     `NameResourceID`jest zdefiniowana w pliku Resources.h projektu BasicEditorUI i identyfikuje Edytor edytorem"My".  
  
2.  Zastąpienie <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
     W implementacji <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody, wywołaj <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> — metoda i przekazać wystąpienia fabryką edytora, jak przedstawiono poniżej.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Ten krok rejestruje zarówno fabryki edytora i rozszerzenia plików edytora.  
  
3.  Wyrejestruj fabryki edytora.  
  
     Fabryki edytora są automatycznie wyrejestrować, jeśli pakiet VSPackage zostanie usunięty. Jeśli obiekt fabryki edytora implementuje <xref:System.IDisposable> interfejsu, jego `Dispose` metoda jest wywoływana po fabryka został wyrejestrowany z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Rejestracja przy użyciu skryptu rejestru  
 Zarejestrowanie fabryki edytora i typów plików w macierzystym [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] odbywa się za pomocą skryptu rejestru do zapisu do rejestru systemu windows, jak pokazano poniżej.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Aby zarejestrować Edytor typy plików za pomocą skryptu rejestru  
  
1.  W skrypcie rejestru, zdefiniuj fabryki edytora i ciąg identyfikatora GUID fabryki edytora jak pokazano w `GUID_BscEditorFactory` sekcji poniższy skrypt rejestru. Ponadto można zdefiniować, rozszerzenia i priorytet rozszerzenia edytora:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     Rozszerzenie pliku edytora w tym przykładzie zostanie zidentyfikowana jako ".rtf" i "50" jest jej priorytet. Parametry identyfikatora GUID są zdefiniowane w pliku Resource.h BscEdit przykładowy projekt.  
  
2.  Zarejestruj pakiet VSPackage.  
  
3.  Zarejestruj fabrykę edytora.  
  
     Fabryka edytora jest zarejestrowana w <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementacji.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Parametry identyfikatora GUID są zdefiniowane w pliku Resource.h BscEdit projektu.