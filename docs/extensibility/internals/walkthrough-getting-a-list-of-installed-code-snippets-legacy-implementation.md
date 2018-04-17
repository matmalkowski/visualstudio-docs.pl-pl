---
title: Pobieranie listy zainstalowanych fragmentów kodu (starsze) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ec48ee8ec7beffd66cec4266bc038b17a08a202
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Wskazówki: Pobieranie listy fragmentów kodu zainstalowanych (wykonanie starsza wersja)
Fragment kodu jest fragment kodu, który można wstawiać do bufora źródłowego za pomocą polecenia menu, (co pozwala wybierania listę zainstalowanych wstawki) lub przez wybranie skrótów fragmentu w liście uzupełniania IntelliSense.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Metoda pobiera wszystkie fragmenty kodu języka określonego identyfikatora GUID. Skróty do tych fragmentów można wstawiać do listy uzupełniania IntelliSense.  
  
 Zobacz [obsługę wstawki kodu za pośrednictwem usługi języka starszych](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) Aby uzyskać więcej informacji o implementacji wstawki kodu za pośrednictwem usługi języka framework (MPF) zarządzanego pakietu.  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Aby pobrać listę wstawki kodu  
  
1.  Poniższy kod przedstawia sposób uzyskać listę wstawki kodu dla danego języka. Wyniki są przechowywane w tablicy <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> struktury. Ta metoda używa statycznych <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metodę, aby pobrać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> interfejsu z <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> usługi. Jednak można również używać dostawcy usług podany pakiet VSPackage i wywołanie <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> metody.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Aby wywołać metodę GetSnippets  
  
1.  Następująca metoda, pokazuje sposób wywoływania `GetSnippets` metody po ukończeniu operacji przetwarzania. <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Metoda jest wywoływana po wykonaniu operacji analizy, które zostało uruchomione z powodu <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  `expansionsList` Tablicy listis pamięci podręcznej ze względu na wydajność. Fragmenty kodu zmiany zostaną odzwierciedlone na liście zatrzymana i ponownie załadować usługi języka (na przykład przez zatrzymanie i ponowne uruchomienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Aby użyć informacji fragment kodu  
  
1.  Poniższy kod przedstawia sposób użycia fragment informacje zwracane przez `GetSnippets` metody. `AddSnippets` Metoda jest wywoływana z analizatora w odpowiedzi na jakiegokolwiek powodu analizy, który jest używany do wypełnienia listy fragmentów kodu. Powinno to mieć miejsce, po pełnej analizy zostały wykonane po raz pierwszy.  
  
     `AddDeclaration` Metoda tworzy listę deklaracje później wyświetlany na liście uzupełniania.  
  
     `TestDeclaration` Klasa zawiera wszystkie informacje, które mogą być wyświetlane na liście uzupełniania, a także deklaracji typu.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)