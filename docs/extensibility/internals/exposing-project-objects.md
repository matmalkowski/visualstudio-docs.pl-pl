---
title: "Udostępnianie obiektów projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f29ca84669f563da5733c8c07b219d498ccf6ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-project-objects"></a>Udostępnianie obiektów projektu
Typy projektów niestandardowych może zapewnić obiekty automatyzacji, aby zezwolić na dostęp do projektu przy użyciu interfejsów automatyzacji. Każdy typ projektu powinien zapewniać standardowego <xref:EnvDTE.Project> obiektu automatyzacji, który jest dostępny z <xref:EnvDTE.Solution>, który zawiera zbiór wszystkich projektów, które są otwarte w IDE. Oczekiwano każdego elementu w projekcie mają być uwidaczniane przez <xref:EnvDTE.ProjectItem> umożliwia uzyskanie dostępu do obiektu `Project.ProjectItems`. Oprócz tych obiektów automatyzacji w wersji standard projekty można zaoferować obiekty automatyzacji określonego projektu.  
  
 Możesz tworzyć niestandardowe automatyzacji poziomu głównego obiektów, których masz dostęp późnym wiązaniem z głównego DTE obiektu przy użyciu `DTE.<customeObjectName>` lub `DTE.GetObject("<customObjectName>")`. Na przykład Visual C++ Tworzy kolekcję projektów specyficznego dla projektu C++ o nazwie "VCProjects", której będziesz mieć dostęp DTE. VCProjects lub DTE. GetObject("VCProjects"). Można również utworzyć Project.Object, która jest unikatowa dla typu projektu, Project.CodeModel, które można wykonać zapytania dla jego obiektu pochodnego większość, ProjectItem, który udostępnia ProjectItem.Object i ProjectItem.FileCodeModel.  
  
 Jest typowe Konwencji dla projektów do udostępnienia kolekcję projektów niestandardowych, specyficzne dla projektu. Na przykład [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tworzy kolekcję określonego projektu C++, który można następnie uzyskać dostęp za pomocą `DTE.VCProjects` lub `DTE.GetObject("VCProjects")`. Można również utworzyć `Project.Object`, która jest unikatowa dla typu projektu `Project.CodeModel`, może być badana jego obiektu pochodnego większość `ProjectItem`, który ujawnia `ProjectItem.Object`, a `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Do ich współtworzenia obiektu pakiet VSPackage specyficzne dla projektu  
  
1.  Dodaj odpowiednie klucze do pliku .pkgdef VSPackage.  
  
     Na przykład poniżej przedstawiono ustawienia .pkgdef dla projektów języka C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementowania kodu w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody, jak w poniższym przykładzie.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     W kodzie `g_wszAutomationProjects` to nazwa kolekcji projektów. `GetAutomationProjects` Metoda tworzy obiekt, który implementuje `Projects` interfejsu i zwraca `IDispatch` wskaźnik do obiektu wywołującego, jak pokazano w poniższym przykładzie kodu.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Należy wybrać unikatową nazwę dla obiekt automatyzacji. Konflikty nazw są nieprzewidywalne i kolizji spowodować konflikt nazwy obiektów arbitralnie zostanie wygenerowany, jeśli wiele typów projektów, użyj takiej samej nazwy. Należy uwzględnić nazwę firmy lub unikatowy aspektów jego nazwę produktu obiektu automatyzacji.  
  
     Niestandardowa `Projects` obiektu kolekcji jest punktem wejścia wygody dla pozostałej części projektu modelu automatyzacji. Obiekt projektu jest również dostępny z <xref:EnvDTE.Solution> kolekcji projektów. Po utworzeniu odpowiedni kod i wpisy rejestru zapewniające konsumentom `Projects` kolekcji obiektów, podać implementacji pozostałych standardowymi obiektami modelu projektu. Aby uzyskać więcej informacji, zobacz [projektu modelowania](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>