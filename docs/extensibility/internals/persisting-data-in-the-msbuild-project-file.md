---
title: Utrwalanie danych w pliku projektu MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 324f9dfd4e381e9580e4940f06f652ef64d9d3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132082"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Utrwalanie danych w pliku projektu MSBuild
Podtyp projektu może być konieczne do utrwalenia danych specyficznych dla podtypu do pliku projektu do późniejszego użycia. Podtyp projektu używa trwałości plik projektu do spełniać następujące wymagania:  
  
1.  Utrwalenia danych używany w ramach tworzenia projektu. (Aby uzyskać więcej informacji na aparat kompilacji firmy Microsoft, zobacz [MSBuild](../../msbuild/msbuild.md).) Informacje dotyczące kompilacji wykonać jedną z następujących:  
  
    1.  Dane konfiguracji niezależny. Oznacza to, że dane przechowywane w elementów MSBuild z warunkami pusty lub Brak.  
  
    2.  Dane zależne od konfiguracji. Oznacza to, że dane przechowywane w MSBuild elementy, które są przechowywane konfiguracji określonego projektu. Na przykład:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Utrwalenia danych, która nie jest odpowiednia do kompilacji. Te dane mogą być wyrażone w dowolnych XML, który nie jest weryfikowany pod kątem schematu XML.  
  
    1.  Dane konfiguracji niezależny.  
  
    2.  Dane zależne od konfiguracji.  
  
## <a name="persisting-build-related-information"></a>Przechowywanie informacji dotyczących kompilacji  
 Trwałość danych jest przydatne w przypadku tworzenia projektu jest obsługiwana za pomocą programu MSBuild. MSBuild system obsługuje tabelę główną informacji dotyczących kompilacji. Podtypów projektu są zobowiązani do uzyskiwania dostępu do tych danych do pobierania i ustawiania wartości właściwości. Podtypów projektu można również rozszerzyć tabeli danych związanych z kompilacją przez dodanie dodatkowych właściwości utrwalenia i usuwając właściwości, więc nie są zachowywane.  
  
 Aby zmodyfikować danych MSBuild, podtypu projektu jest odpowiedzialny za pobieranie obiektu właściwości programu MSBuild z systemu podstawowego projektu za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> to interfejs została zaimplementowana na podstawowego systemu projektu i agregację kwerend podtypu projektu dla niego uruchamiając `QueryInterface`.  
  
 Poniższej procedury opisano kroki usuwanie przy użyciu właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Aby usunąć właściwości z pliku projektu programu MSBuild  
  
1.  Wywołanie `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> podtypu projektu.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> z `pszPropName` ustaw dla właściwości, które chcesz usunąć.  
  
### <a name="persisting-non-build-related-information"></a>Utrwalanie informacji powiązanych z systemem innym niż kompilacji  
 Trwałość danych w plikach projektu, który nie ma znaczenia, aby utworzyć odbywa się za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> w głównym `project subtype aggregator` obiektu `project subtype project configuration` obiektu lub oba.  
  
 Następujące punkty konspektu o pojęciach dotyczących trwałości informacji powiązanych z systemem innym niż kompilacji.  
  
-   Wywołuje podstawowego projektu na obiekcie agregatora podtyp (to znaczy podtypu projektu najbardziej zewnętrznego) głównego projektu, aby przy ładowaniu i zapisywaniu danych niezależnie od konfiguracji i wywoływanych przez nią obiektów konfiguracji projektu podtypu projektu ładowania lub Zapisz konfigurację zależne dane.  
  
-   Podstawowy projekt wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wiele razy dla każdego poziomu agregacji podtypu projektu i przekazuje identyfikatora GUID dla każdego poziomu.  
  
-   Podstawowy projekt przekazuje lub odbiera fragment XML, przeznaczona dla podtypu określonego projektu i używa ten mechanizm sposób utrwalanie stanu między poziomami agregacji.  
  
-   Podstawowy projekt wymaga podtypu projektu najbardziej zewnętrznego <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementacji, przekazując identyfikatorem GUID. Jeśli identyfikator GUID należy do podtypu projektu najbardziej zewnętrznego, obsługuje on wywołania. w przeciwnym razie deleguje ona wywołanie podtypu projektu wewnętrzny i tak dalej, aż do znalezienia podtyp projektu, którego identyfikator GUID odpowiada.  
  
-   Podtyp projektu można również zmodyfikować XML fragment przed lub po deleguje ona wywołanie podtypu projektu wewnętrzny. W poniższym przykładzie przedstawiono fragment pliku projektu, w którym nazwę pliku, który zawiera właściwości specyficzne dla podtypu projektu jest przekazywana do tego podtypu projektu.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)