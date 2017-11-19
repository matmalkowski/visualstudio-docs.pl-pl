---
title: "Rozszerzanie filtru Eksploratora rozwiązań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f34f19d41f3d624c57cc6c92d51b5c19ddb2137
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-solution-explorer-filter"></a>Rozszerzanie filtru Eksploratora rozwiązań
Można rozszerzyć **Eksploratora rozwiązań** filtrować funkcji, aby wyświetlić lub ukryć różne pliki. Na przykład można utworzyć filtr, który pokazuje tylko pliki C# klasy fabryki w **Eksploratora rozwiązań**, jak pokazano w tym przewodniku.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Tworzenie projektu pakietu programu Visual Studio  
  
1.  Tworzenie projektu VSIX o nazwie `FileFilter`. Dodawanie polecenia niestandardowego szablonu elementu o nazwie **obiektu FileFilter**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Dodaj odwołanie do `System.ComponentModel.Composition` i `Microsoft.VisualStudio.Utilities`.  
  
3.  Polecenie menu są wyświetlane na **Eksploratora rozwiązań** paska narzędzi. Otwórz plik FileFilterPackage.vsct.  
  
4.  Zmień `<Button>` bloku do następującego:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>Aktualizacja pliku manifestu  
  
1.  W pliku source.extension.vsixmanifest Dodaj zasób, który jest składników MEF.  
  
2.  Na **zasoby** , wybierz pozycję **nowy** przycisku.  
  
3.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
5.  W **projektu** wybierz **obiektu FileFilter**, a następnie wybierz pozycję **OK** przycisku.  
  
### <a name="add-the-filter-code"></a>Dodaj kod filtru  
  
1.  Niektóre identyfikatory GUID należy dodać do pliku FileFilterPackageGuids.cs:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Dodaj plik klasy do obiektu FileFilter projektu o nazwie FileNameFilter.cs.  
  
3.  Zamień na pustej przestrzeni nazw i klasy pusty poniższy kod.  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Metoda pobiera kolekcję zawierającą głównego rozwiązania (`rootItems`) i zwraca kolekcję elementów, które mają być uwzględnione w filtrze.  
  
     `ShouldIncludeInFilter` Metody filtruje elementy w **Eksploratora rozwiązań** oparte na pod warunkiem, że możesz określić hierarchii.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4.  W FileFilter.cs Usuń kod umieszczania i obsługa polecenia z konstruktora obiektu FileFilter. Wynik powinien wyglądać następująco:  
  
    ```csharp  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Usuń metodę ShowMessageBox() również.  
  
5.  W FileFilterPackage, cs, Zastąp kod w metodzie Initialize() następujące czynności:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Testowanie kodu  
  
1.  Tworzenie i uruchamianie projektu. Zostanie wyświetlone drugie wystąpienie programu Visual Studio. Jest to eksperymentalne wystąpienie.  
  
2.  Eksperymentalne wystąpienie programu Visual Studio Otwórz projekt C#.  
  
3.  Poszukaj przycisku dodane na pasku narzędzi Eksplorator rozwiązań. Należy go czwarty przycisk z lewej strony.  
  
4.  Po kliknięciu przycisku zostać odfiltrowane wszystkie pliki i powinna zostać wyświetlona "wszystkie elementy zostały wyfiltrowane z widoku." w Eksploratorze rozwiązań.