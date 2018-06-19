---
title: MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26646ecef952a6f4ff761f4e7239fc6e7e920ea1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31576004"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] To platforma do tworzenia aplikacji. Ten aparat, który jest również nazywany MSBuild, udostępnia schematu XML dla pliku projektu, która kontroluje sposób platformy kompilacji przetwarza i tworzy oprogramowania. Visual Studio będzie korzystać program MSBuild, ale nie jest zależny od programu Visual Studio. Wywołując msbuild.exe w pliku projektu lub rozwiązania, możesz organizować i kompilacji produktów w środowiskach, w którym nie jest zainstalowany program Visual Studio.  
  
 Visual Studio będzie korzystać program MSBuild do ładowania i kompilacji projektów zarządzanych. Pliki projektu w programie Visual Studio (.csproj, vbproj, vcxproj i inne) zawiera kod XML programu MSBuild, który wykonuje podczas kompilowania projektu za pomocą środowiska IDE. Projektów programu Visual Studio zaimportować wszystkie niezbędne ustawienia i procesów pracy typowy programowanie kompilacji, ale można rozszerzyć lub zmodyfikować je z poziomu programu Visual Studio lub za pomocą edytora XML.  
  
 Aby uzyskać informacje o MSBuild C++, zobacz [MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp).  
  
 Poniższe przykłady przedstawiają podczas kompilacji może działać przy użyciu wiersza polecenia programu MSBuild zamiast środowiska IDE programu Visual Studio.  
  
-   Nie jest zainstalowany program Visual Studio.  
  
-   Chcesz użyć w 64-bitowej wersji programu MSBuild. Ta wersja programu MSBuild jest zazwyczaj zbędne, ale pozwala MSBuild, aby dostęp do większej ilości pamięci.  
  
-   Chcesz uruchomić kompilację w wielu procesów. Jednak można użyć IDE uzyskanie takiego samego wyniku w projektach C++ i C#.  
  
-   Chcesz zmodyfikować system kompilacji. Na przykład możesz włączyć następujące akcje:  
  
    -   Przetwarzanie wstępne plików przed dotarciem kompilatora.  
  
    -   Skopiuj pliki wyjściowe kompilacji w inne miejsce.  
  
    -   Utwórz skompresowane pliki na podstawie danych wyjściowych kompilacji.  
  
    -   Wykonaj krok przetwarzania końcowego. Na przykład możesz chcieć sygnatury zestawu za pomocą innej wersji.  
  
 W środowisku IDE programu Visual Studio można napisać kod, ale Uruchom tworzy się przy użyciu programu MSBuild. Jako kolejny alternatywny można kompilacji kodu w środowisku IDE programu na komputerze dewelopera, ale kompilacji kodu, który jest zintegrowany z wielu deweloperów za pomocą wiersza polecenia programu MSBuild.  
  
> [!NOTE]
>  Umożliwia Team Foundation Build automatycznie Kompiluj, testowania i wdrażania aplikacji. Możesz system kompilacji automatycznie uruchomić kompilacji, gdy deweloperzy zaewidencjonowaniu kodu (na przykład w ramach strategii ciągłej integracji) lub zgodnie z harmonogramem (na przykład co noc kompilacji testu weryfikacji kompilacji). Team Foundation Build kompiluje kod przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz [kompilacji i wydania](/vsts/build-release/index).  
  
 Ten temat zawiera omówienie programu MSBuild. Samouczek wprowadzający, zobacz [wskazówki: przy użyciu programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 **W tym temacie**  
  
-   [Przy użyciu programu MSBuild w wierszu polecenia](#BKMK_CommandPrompt)  
  
-   [Plik projektu](#BKMK_ProjectFile)  
  
    -   [Właściwości](#BKMK_Properties)  
  
    -   [Elementy](#BKMK_Items)  
  
    -   [Zadania](#BKMK_Tasks)  
  
    -   [Docelowe elementy](#BKMK_Targets)  
  
-   [Dzienniki kompilacji](#BKMK_BuildLogs)  
  
-   [Przy użyciu programu MSBuild w programie Visual Studio](#BKMK_VisualStudio)  
  
-   [Przeznaczanie dla wielu platform](#BKMK_Multitargeting)  
  
##  <a name="BKMK_CommandPrompt"></a> Przy użyciu programu MSBuild w wierszu polecenia  
 Aby uruchomić [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] w wierszu polecenia, przekazać plik projektu do MSBuild.exe, wraz z niej odpowiednie opcje wiersza polecenia. Opcje wiersza polecenia umożliwiają ustawianie właściwości, wykonywanie określonych elementów docelowych i ustaw inne opcje, które kontrolują proces kompilacji. Na przykład czy użyć następującej składni wiersza polecenia do tworzenia pliku `MyProj.proj` z `Configuration` ustawioną właściwość `Debug`.  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] opcji wiersza polecenia, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
>  Przed pobraniem projektu określają wiarygodności kodu.  
  
##  <a name="BKMK_ProjectFile"></a> Plik projektu  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wykorzystuje format pliku projektu opartego na formacie XML, który jest bardzo proste i rozszerzalny. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Format pliku projektu umożliwia deweloperom opisano elementy, które mają zostać skompilowane, a także, jak są ma zostać utworzony dla różnych systemów operacyjnych i konfiguracji. Ponadto format pliku projektu umożliwia deweloperom autora wielokrotnego użytku kompilacji reguł, które mogą być brana pod uwagę w oddzielnych plików tak, aby kompilacje mogą być wykonywane stale w wielu różnych projektów w produkcie.  
  
 W poniższych sekcjach opisano niektóre podstawowe elementy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] format pliku projektu. Samouczek dotyczący sposobu tworzenia pliku podstawowego projektu, zobacz [wskazówki: Tworzenie pliku projektu MSBuild od początku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
###  <a name="BKMK_Properties"></a> właściwości  
 Właściwości reprezentują pary klucz wartość, które mogą służyć do konfigurowania kompilacji. Właściwości są zadeklarowane, tworząc element, który ma nazwę właściwości jako element podrzędny [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elementu. Na przykład poniższy kod tworzy właściwość o nazwie `BuildDir` , który ma wartość `Build`.  
  
```xml  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Definiuje właściwości warunkowo przez umieszczenie `Condition` atrybutu w elemencie. Zawartość warunkowego elementy są ignorowane, chyba że wyrażenie `true`. W poniższym przykładzie `Configuration` jest zdefiniowany element, jeśli jeszcze nie został zdefiniowany.  
  
```xml  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 Właściwości można odwoływać się w pliku projektu przy użyciu składni $(*PropertyName*). Na przykład możesz odwoływać się do właściwości w poprzednich przykładach przy użyciu `$(BuildDir)` i `$(Configuration)`.  
  
 Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
###  <a name="BKMK_Items"></a> Elementy  
 Elementy są dane wejściowe w systemie kompilacji i zwykle odpowiadają pliki. Elementy są pogrupowane w typy elementów, na podstawie nazw elementów zdefiniowanych przez użytkownika. Te typy elementów może być używane jako parametry dla zadania, które umożliwia poszczególne elementy wykonaj kroki procesu kompilacji.  
  
 Elementy są zadeklarowane w pliku projektu, tworząc element, który ma nazwę typu elementu jako elementu podrzędnego [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Na przykład poniższy kod tworzy typ elementu o nazwie `Compile`, która obejmuje dwa pliki.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Typy elementów można odwoływać się w pliku projektu przy użyciu składni @(*ItemType*). Na przykład typ elementu w tym przykładzie będzie odwoływać się przy użyciu `@(Compile)`.  
  
 W programie MSBuild nazw elementów i atrybutów jest rozróżniana wielkość liter. Jednak nazwy właściwości, element i metadanych nie są. W poniższym przykładzie tworzony typ elementu `Compile`, `comPile`, lub innych przypadków zmiany i zwraca wartość "one.cs;two.cs" typ elementu.  
  
```xml  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Elementy mogą być deklarowane przy użyciu symboli wieloznacznych i może zawierać dodatkowe metadane dla bardziej zaawansowanych scenariuszy kompilacji. Aby uzyskać więcej informacji na temat elementów, zobacz [elementów](../msbuild/msbuild-items.md).  
  
###  <a name="BKMK_Tasks"></a> Zadania  
 Zadania są jednostki plik wykonywalny jest kod [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów służy do wykonywania operacji kompilacji. Na przykład zadanie może skompilować plików wejściowych lub uruchomić narzędzia zewnętrznego. Zadania mogą być ponownie używane, i mogą być współużytkowane przez różnych deweloperów w różnych projektów.  
  
 Logiki wykonywania zadania jest zapisywane w kodzie zarządzanym i mapować do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] za pomocą [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Można pisać własne zadania przy tworzenia zarządzanego typu, który implementuje <xref:Microsoft.Build.Framework.ITask> interfejsu. Aby uzyskać więcej informacji na temat tworzenia zadania, zobacz [wpisywanie zadania](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zawiera typowe zadania, które można dostosować do własnych wymagań.  Przykłady [kopiowania](../msbuild/copy-task.md), który kopiuje pliki, [makedir —](../msbuild/makedir-task.md), co powoduje katalogów, i [Csc](../msbuild/csc-task.md), który kompiluje pliki kodu źródłowego języka Visual C#. Aby uzyskać listę dostępnych zadań wraz z informacjami użycia, zobacz [odwołanie do zadania](../msbuild/msbuild-task-reference.md).  
  
 Zadania są wykonywane w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu, tworząc element, który ma nazwę zadania jako element podrzędny [docelowej](../msbuild/target-element-msbuild.md) elementu. Zadania zazwyczaj zaakceptować parametrów, które są przekazywane jako atrybuty elementu. Zarówno [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] właściwości i elementów, które mogą być używane jako parametry. Na przykład poniższy kod wywołania [makedir —](../msbuild/makedir-task.md) zadań i przekazuje jego wartość `BuildDir` właściwość, która została zadeklarowana w poprzedniego przykładu.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Aby uzyskać więcej informacji o zadaniach, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
###  <a name="BKMK_Targets"></a> Obiekty docelowe  
 Obiekty docelowe grupowania zadań w określonej kolejności i udostępnić sekcji w pliku projektu jako punkty wejścia do procesu kompilacji. Obiekty docelowe często są pogrupowane w logiczne sekcje, aby zwiększyć czytelność, a Zezwalaj na rozszerzenia. Fundamentalne kroki procesu kompilacji w docelowych elementach umożliwia wywołanie jedną część procesu kompilacji z innymi celami bez kopiowania tej sekcji kodu do każdego obiektu docelowego. Na przykład jeśli kilka punktów wejścia z procesem kompilacji wymaga odwołania ma zostać utworzony, można utworzyć obiektu docelowego, który tworzy odwołania, a następnie uruchom przeznaczonych z każdego punktu wejścia, gdzie są wymagane.  
  
 Obiekty docelowe są zadeklarowane w pliku projektu za pomocą [docelowej](../msbuild/target-element-msbuild.md) elementu. Na przykład poniższy kod tworzy element docelowy o nazwie `Compile`, które następnie wywołuje [Csc](../msbuild/csc-task.md) zadania, które ma listy elementów, który został zadeklarowany w poprzedniego przykładu.  
  
```xml  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 W bardziej zaawansowanych scenariuszy elementy docelowe może służyć do opisano relacje między sobą i wykonywać analizy zależności, dzięki czemu można był pomijany sekcje całego procesu kompilacji, jeśli ten cel jest aktualny. Aby uzyskać więcej informacji na temat elementów docelowych, zobacz [cele](../msbuild/msbuild-targets.md).  
  
##  <a name="BKMK_BuildLogs"></a> Dzienniki kompilacji  
 Może rejestrować błędy kompilacji, ostrzeżenia i komunikaty do konsoli lub innego urządzenia wyjściowego. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) i [rejestrowania w programie MSBuild](../msbuild/logging-in-msbuild.md).  
  
##  <a name="BKMK_VisualStudio"></a> Przy użyciu programu MSBuild w programie Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] używa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] format pliku projektu do przechowywania informacji o kompilacji o zarządzanych projektów. Projekt ustawień, które zostały dodane lub zmienione za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu są uwzględniane w. * proj pliku, który jest generowany dla każdego projektu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] używa hostowanej wystąpienia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do tworzenia projektów zarządzanych. Oznacza to, że zarządzanego projektu mogą być wbudowane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub w wierszu polecenia (nawet jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest zainstalowany), a wyniki musi być taka sama.  
  
 Samouczek dotyczący sposobu używania programu MSBuild w programie Visual Studio, zobacz [wskazówki: przy użyciu programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
##  <a name="BKMK_Multitargeting"></a> Przeznaczanie dla wielu platform  
 Za pomocą programu Visual Studio, można skompilować aplikację do uruchamiania na jednym z kilku wersji programu .NET Framework. Na przykład można skompilować aplikację do uruchamiania na .NET Framework 2.0 na platformie 32-bitowe i można kompilować tej samej aplikacji do uruchamiania na na 64-bitowej platformy .NET Framework 4.5. Zdolność do kompilowania więcej niż jeden Framework nosi nazwę przeznaczanie dla wielu platform.  
  
 Oto niektóre zalety przeznaczanie dla wielu platform:  
  
-   Można programować aplikacje, które odnoszą się do wcześniejszych wersji programu .NET Framework, na przykład, w wersjach 2.0, 3.0 i 3.5.  
  
-   Możesz zastosować struktur niż programu .NET Framework, na przykład Silverlight.  
  
-   Celem może być *profilu framework*, który jest wstępnie zdefiniowanych podzbiór platformy docelowej.  
  
-   Jeśli zostanie zwolniony z dodatkiem Service pack dla bieżącej wersji programu .NET Framework, można stosowanie ich.  
  
-   Przeznaczanie dla wielu platform gwarantuje, że aplikacja używa tylko funkcje dostępne w docelowy framework i platformę.  
  
 Aby uzyskać więcej informacji, zobacz [przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Przedstawiono sposób tworzenia pliku podstawowego projektu przyrostowo, używając tylko tekstowy edytora.|  
|[Przewodnik: Używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md)|Wprowadza blokami konstrukcyjnymi elementów MSBuild oraz sposób zapisu, manipulowanie nimi oraz debugowania projektów MSBuild bez zamykania programu Visual Studio IDE.|  
|[Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)|Przedstawia informacje o czterech bloków konstrukcyjnych programu MSBuild: właściwości, elementów docelowych i zadań.|  
|[Elementy](../msbuild/msbuild-items.md)|W tym artykule opisano ogólne pojęcia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] plik formatu i sposób elementy dopasowania.|  
|[Właściwości programu MSBuild](../msbuild/msbuild-properties.md)|Wprowadza właściwości i kolekcji właściwości. Właściwości są kompilacje pary klucz wartość, które mogą służyć do konfigurowania.|  
|[Docelowe elementy](../msbuild/msbuild-targets.md)|Wyjaśniono, jak grupy zadań w określonej kolejności i Włącz sekcje proces kompilacji ma być wywoływana w wierszu polecenia.|  
|[Zadania](../msbuild/msbuild-tasks.md)|Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, który może być używany przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania operacji niepodzielnych kompilacji.|  
|[Warunki](../msbuild/msbuild-conditions.md)|W tym artykule omówiono sposób użycia `Condition` w elemencie MSBuild.|  
|[Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)|Przedstawia informacje o liczbie przetwarzanie wsadowe, wykonywania transformacji przeznaczanie dla wielu platform i innych zaawansowanych technik.|  
|[Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md)|Opisuje sposób rejestrowania zdarzeń kompilacji, wiadomości i błędów.|  
|[Dodatkowe zasoby](../msbuild/additional-msbuild-resources.md)|Zawiera listę zasobów społeczności i pomocy technicznej, aby uzyskać więcej informacji o programie MSBuild.|  
  
## <a name="reference"></a>Tematy pomocy  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)  
 Łącza do tematów, które zawierają informacje o odwołaniu.  
  
 [Słownik](msbuild-glossary.md) definiuje typowe warunki MSBuild.
