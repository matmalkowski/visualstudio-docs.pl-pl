---
title: Integracja z programem Visual Studio (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
caps.latest.revision: "21"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 5aff5914d9b278b206f81abd4f28ce9f4dfa409c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-integration-msbuild"></a>Integracja z programem Visual Studio (MSBuild)
Visual Studio hostów [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do ładowania i kompilacji projektów zarządzanych. Ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest odpowiedzialny za projektu prawie każdego projektu w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mogą być pomyślnie użyć formatu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nawet wtedy, gdy projektu zostało utworzone przez innego narzędzia i ma niestandardowy proces kompilacji.  
  
 W tym temacie opisano określone aspekty [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hostingu, które należy uwzględnić podczas dostosowywanie projektów i pliki .targets, które chcesz załadować i kompilacji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Te pomoże Ci upewnij się, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funkcje, takie jak IntelliSense i debugowanie pracy niestandardowe projektu.  
  
 Informacje dla projektów C++, zobacz [pliki projektu](/cpp/ide/project-files).  
  
## <a name="project-file-name-extensions"></a>Rozszerzenia nazwy pliku projektu  
 MSBuild.exe rozpoznaje rozszerzenie nazwy pliku projektu pasujących do wzorca. * proj. Jednak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznaje tylko podzbiór tych projektu rozszerzeń nazw plików, które określają system projektu specyficzny dla języka, który zostanie załadowany projektu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nie ma niezależny od języka [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] systemu projektu.  
  
 Na przykład [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] system projektu załaduje .csproj plików, ale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie będzie mógł załadować pliku .xxproj. Plik projektu dla plików źródłowych w języku dowolnego muszą używać tego samego rozszerzenia jako [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliki, aby można było załadować projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="well-known-target-names"></a>Dobrze znane nazwy elementów docelowych  
 Kliknięcie przycisku **kompilacji** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wykona domyślnego obiektu docelowego w projekcie. Często ten element docelowy o nazwie `Build`. Wybieranie **odbudować** lub **wyczyść** polecenia spróbuje wykonać docelowego o tej samej nazwie w projekcie. Kliknięcie przycisku **publikowania** wykona docelowy o nazwie `PublishOnly` w projekcie.  
  
## <a name="configurations-and-platforms"></a>Konfiguracje i platformy  
 Konfiguracje są reprezentowane w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów za pomocą właściwości są pogrupowane w `PropertyGroup` element, który zawiera `Condition` atrybutu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]analizuje tych warunków, aby można było utworzyć listę platform do wyświetlenia i konfiguracje projektu. Aby pomyślnie wyodrębnić tej listy, warunków musi mieć format podobny do następującego:  
  
```  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]analizuje warunki `PropertyGroup`, `ItemGroup`, `Import`, właściwości i elementów w tym celu.  
  
## <a name="additional-build-actions"></a>Dodatkowe akcje kompilacji  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Pozwala zmienić nazwę elementu typu pliku w projekcie z **Akcja kompilacji** właściwość [właściwości pliku](http://msdn.microsoft.com/en-us/013c4aed-08d6-4dce-a124-ca807ca08959) okna. `Compile`, `EmbeddedResource`, `Content`, i `None` nazwy typu elementu zawsze są wyświetlane w tym menu oraz inne elementu typu nazwy już w projekcie. Aby upewnić się, wszystkie nazwy typu elementu niestandardowego są zawsze dostępne w menu, można dodać nazwy do typu elementu o nazwie `AvailableItemName`. Na przykład dodanie następujących do pliku projektu spowoduje dodanie niestandardowego typu `JScript` do tego menu dla wszystkich projektów, które go zaimportować:  
  
```xml  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
>  Niektóre nazwy typu elementu to specjalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ale nie są wymienione w tej listy rozwijanej.  
  
## <a name="in-process-compilers"></a>Kompilatory wewnątrz–procesowe  
 Jeśli to możliwe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podejmie próbę użycia wersji w trakcie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora, aby zwiększyć wydajność. (Nie dotyczy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].) W tym celu działał prawidłowo muszą być spełnione następujące warunki:  
  
-   W docelowej projektu, musi istnieć zadanie o nazwie `Vbc` dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów.  
  
-   `UseHostCompilerIfAvailable` Parametr zadania musi być ustawiony na wartość true.  
  
## <a name="design-time-intellisense"></a>Technologia IntelliSense — czas projektowania  
 Aby uzyskać pomoc techniczną IntelliSense [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przed kompilacji wygenerowała zestawu wyjściowego, muszą być spełnione następujące warunki:  
  
-   Musi być element docelowy o nazwie `Compile`.  
  
-   Albo `Compile` docelowej lub jednej z jego zależności należy wywołać zadań kompilatora dla projektu, takie jak `Csc` lub `Vbc`.  
  
-   Albo `Compile` docelowej lub jednej z jego zależności mogą powodować kompilator, aby otrzymywać wszystkie niezbędne parametry dla IntelliSense, szczególnie wszystkie odwołania.  
  
-   Muszą być spełnione warunki opisane w sekcji "W trakcie kompilatory".  
  
## <a name="building-solutions"></a>Tworzenie rozwiązań  
 W ramach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], plik rozwiązania i kolejność kompilacji projektu są kontrolowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] samej siebie. W przypadku kompilowania rozwiązania z msbuild.exe w wierszu polecenia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analizuje plik rozwiązania i ustala kolejność kompilacji projektu. W obu przypadkach projekty są tworzone oddzielnie w kolejności zależności i odwołań projektów nie jest przesunięta. Natomiast w przypadku poszczególnych projekty zostały skompilowane z msbuild.exe, odwołań projektów jest przesunięta.  
  
 Podczas kompilowania wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], właściwość `$(BuildingInsideVisualStudio)` ma ustawioną wartość `true`. To umożliwia w plikach projektu lub .targets spowodować kompilacji do zachowywać się inaczej.  
  
## <a name="displaying-properties-and-items"></a>Wyświetlanie właściwości i elementów  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]rozpoznaje niektóre nazwy i wartości właściwości. Na przykład następującą właściwość w projekcie spowoduje, że **aplikacji systemu Windows** pojawią się w **typu aplikacji** polu **projektanta projektu**.  
  
```xml  
<OutputType>WinExe</OutputType>  
```  
  
 Wartość właściwości można edytować w **projektanta projektu** i zapisane w pliku projektu. Jeśli taka właściwość podano nieprawidłową wartość, edytując ręcznie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] będzie Pokaż ostrzeżenie po załadowaniu projektu i zastąp wartość domyślną nieprawidłową wartość.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]rozumie, wartości domyślne dla niektórych właściwości. Te właściwości nie zostaną utrwalone w pliku projektu, jeśli nie mają wartości innych niż domyślne.  
  
 Właściwości z dowolnych nazw nie są wyświetlane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby zmodyfikować dowolne właściwości w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], należy otworzyć plik projektu w edytorze XML i edytować je ręcznie. Aby uzyskać więcej informacji, zobacz [edytowanie plików projektu w programie Visual Studio](#BKMK_EditingProjects) później w tym temacie.  
  
 Elementy zdefiniowane w projekcie z dowolnego elementu nazwy typów są domyślnie wyświetlana w Eksploratorze rozwiązań, ich węźle projektu. Aby ukryć element z ekranu, należy ustawić `Visible` metadanych do `false`. Na przykład następujący element będzie uczestniczyć w procesie kompilacji, ale nie można wyświetlić w Eksploratorze rozwiązań.  
  
```xml  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Elementy zadeklarowane w importowanych do projektu nie są wyświetlane domyślnie. Elementy utworzone podczas procesu kompilacji nigdy nie są wyświetlane w Eksploratorze rozwiązań.  
  
## <a name="conditions-on-items-and-properties"></a>Postanowienia dot. elementów i właściwości  
 Podczas kompilacji wszystkie warunki pełni są przestrzegane.  
  
 Podczas określania wartości właściwości, aby wyświetlić właściwości który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uwzględnia konfiguracji zależne są oceniane inaczej niż właściwości traktuje konfiguracji niezależne. Dla właściwości traktuje konfiguracji zależnych, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ustawia `Configuration` i `Platform` właściwości odpowiednio i instruuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ponownej oceny projektu. Dla właściwości traktuje konfiguracji niezależnie, jest nieokreślony, w jak warunki zostaną ocenione.  
  
 Wyrażenia warunkowe na elementach zawsze są ignorowane na potrzeby podejmowania decyzji o tym, czy element ma być wyświetlany w Eksploratorze rozwiązań.  
  
## <a name="debugging"></a>Debugowanie  
 Aby odnaleźć i uruchom zestawu wyjściowego i dołączyć debuger, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wymaga właściwości `OutputPath`, `AssemblyName`, i `OutputType` poprawnie zdefiniowany. Debuger nie będzie można dołączyć, jeśli proces kompilacji nie spowodowało kompilator, aby wygenerować plik PDB.  
  
## <a name="design-time-target-execution"></a>Wykonanie docelowego czasu projektowania  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]próbuje wykonać obiektów docelowych z niektórych nazw ładuje projekt. Następujących elementów docelowych zawierać `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`, i `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Uruchamia następujących elementów docelowych, dzięki czemu kompilatora mogą być inicjowane w celu zapewnienia funkcji IntelliSense, można zainicjować debugera i wyświetlana w Eksploratorze rozwiązań odwołania mogą zostać rozwiązane. Jeśli nie podano tych celów, projekt zostanie obciążenia i kompilacji poprawnie, ale środowisko czasu projektowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie będzie w pełni funkcjonalne.  
  
##  <a name="BKMK_EditingProjects"></a>Edytowanie plików projektu w programie Visual Studio  
 Aby edytować [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu bezpośrednio, można otworzyć pliku projektu w edytorze programu Visual Studio XML.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Aby rozładować i edytować plik projektu w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **Zwolnij projekt**.  
  
     Projekt jest oznaczony jako **(niedostępne)**.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu niedostępne, a następnie wybierz **Edytuj \<pliku projektu >**.  
  
     Plik projektu zostanie otwarty w edytorze XML programu Visual Studio.  
  
3.  Edytuj, Zapisz i zamknij plik projektu.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu niedostępne, a następnie wybierz **Załaduj ponownie projekt**.  
  
## <a name="intellisense-and-validation"></a>Technologia IntelliSense i walidacja  
 Edytowanie plików projektu za pomocą edytora XML, IntelliSense i sprawdzanie poprawności jest wymuszany przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] plików schematów. Te pliki zostaną zainstalowane w pamięci podręcznej schematu, która znajduje się w  *\<katalogu instalacyjnego programu Visual Studio >*\Xml\Schemas\1033\MSBuild.  
  
 Podstawowe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] typy są definiowane w Microsoft.Build.Core.xsd i popularne typy używane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są zdefiniowane w Microsoft.Build.CommonTypes.xsd. Aby dostosować schematów, tak aby było możliwe IntelliSense i sprawdzanie poprawności dla nazwy typu elementu niestandardowego, właściwości i zadań, możesz edytować Microsoft.Build.xsd lub utworzyć własny schemat, który zawiera schematów CommonTypes lub Core. Jeśli utworzysz własny schemat, należy przekierować XML edytora, aby znaleźć za pomocą **właściwości** okna.  
  
## <a name="editing-loaded-project-files"></a>Edytowanie wczytanych plików projektu  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]buforuje zawartość plików projektu i plików zaimportowanych przez pliki projektu. Po zmodyfikowaniu pliku załadowanego projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie wyświetli monit ponownie załadować projekt tak, aby zmiany zostały wprowadzone. Jednak po zmodyfikowaniu pliku zaimportowanej przez załadowanego projektu nie będzie żadnego monitu o ponowne załadowanie i musi zwolnić i ponownie Załaduj projekt ręcznie, aby zmiany zostały wprowadzone.  
  
## <a name="output-groups"></a>Grupy danych wyjściowych  
 Kilka zdefiniowanego w Microsoft.Common.targets mają nazwy kończy się rozszerzeniem `OutputGroups` lub `OutputGroupDependencies`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]wymaga następujących elementów docelowych, można pobrać określone listy wyjścia projektu. Na przykład `SatelliteDllsProjectOutputGroup` docelowej tworzy listę wszystkie zestawy satelickie utworzy kompilacji. Grupy te dane wyjściowe są używane przez funkcje, takie jak publikowanie, wdrożenia i odwołania do projektu do projektu. Projekty, które nie określają je będzie obciążenia i kompilacji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale niektóre funkcje mogą nie działać poprawnie.  
  
## <a name="reference-resolution"></a>Rozpoznawanie odwołania  
 Rozpoznawanie odwołania to proces do lokalizowania zestawów rzeczywiste przy użyciu odwołania elementy przechowywane w pliku projektu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]należy wywołać Rozpoznawanie odwołania, aby wyświetlić szczegółowe właściwości dla każdego odwołania w **właściwości** okna. Poniżej opisano trzy typy odwołań i jak są rozwiązywane.  
  
-   Odwołania do zestawów:  
  
     System projektu wywołuje element docelowy z dobrze znanej nazwy `ResolveAssemblyReferences`. Ten element docelowy powinny wywoływać elementy z nazwą typu elementu `ReferencePath`. Każdy z tych elementów powinien mieć określenie elementu (wartość `Include` atrybutu element) zawierający pełną ścieżkę do odwołania. Elementy powinny mieć wszystkich metadanych z elementy wejściowe przekazywane oprócz następujących nowych metadanych:  
  
    -   `CopyLocal`, wskazującą, czy zestaw powinny być kopiowane do folderu wyjściowego, ustaw wartość true lub false.  
  
    -   `OriginalItemSpec`, zawierający specyfikację oryginalnego elementu odwołania.  
  
    -   `ResolvedFrom`, ustawiona na "{TargetFrameworkDirectory}", jeśli jest rozwiązany z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] katalogu.  
  
-   Odwołania COM:  
  
     System projektu wywołuje element docelowy z dobrze znanej nazwy `ResolveCOMReferences`. Ten element docelowy powinny wywoływać elementy z nazwą typu elementu `ComReferenceWrappers`. Każdy z tych elementów powinien mieć określenie elementu zawierającego Pełna ścieżka do zestawu międzyoperacyjnego dla odwołania COM. Elementy powinny mieć wszystkich metadanych z elementów wejściowych przekazany za pośrednictwem, oprócz na nowy metadanych o nazwie `CopyLocal`, wskazującą, czy zestaw powinny być kopiowane do folderu wyjściowego, ustaw wartość true lub false  
  
-   Natywny odwołań  
  
     System projektu wywołuje element docelowy z dobrze znanej nazwy `ResolveNativeReferences`. Ten element docelowy powinny wywoływać elementy z nazwą typu elementu `NativeReferenceFile`. Elementy powinny mieć wszystkich metadanych z elementy wejściowe przekazywane oprócz nową metadanych o nazwie `OriginalItemSpec`, zawierający specyfikację oryginalnego elementu odwołania.  
  
## <a name="performance-shortcuts"></a>Skróty wydajności  
 Po rozpoczęciu debugowania w Interfejsie użytkownika programu Visual Studio (przez wybranie klawisz F5 lub wybierając **debugowania**, **Rozpocznij debugowanie** na pasku menu), proces kompilacji używa wyboru szybkiego aktualizacji do zwiększenia wydajności. W niektórych przypadkach, w których dostosowane kompilacje utworzone pliki, które uzyskać skompilowane z kolei sprawdzanie aktualizacji szybkiego niepoprawnie identyfikować zmienionych plików. Projekty, które wymagają dokładniejszej kontroli aktualizacji można wyłączyć szybkie sprawdzanie przez ustawienie zmiennej środowiskowej `DISABLEFASTUPTODATECHECK=1`. Alternatywnie projektów tę można skonfigurować jako właściwość MSBuild projektu lub w pliku, który importuje projektu.  
  
 Regularne kompilacji w programie Visual Studio sprawdzanie aktualizacji szybkiego nie ma zastosowania i projekt zostanie skompilowany, tak jakby wywoływane kompilacji w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: rozszerzanie procesu kompilacji programu Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [Uruchamianie kompilacji w środowisku IDE](../msbuild/starting-a-build-from-within-the-ide.md)   
 [Rejestrowanie rozszerzeń środowiska .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Item — Element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Property — Element (MSBuild)](../msbuild/property-element-msbuild.md)   
 [TARGET — Element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Vbc — zadanie](../msbuild/vbc-task.md)