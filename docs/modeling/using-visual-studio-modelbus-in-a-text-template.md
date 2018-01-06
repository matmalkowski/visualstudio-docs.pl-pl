---
title: "W szablonie tekstu przy użyciu ModelBus programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 01a08ef43a344f71fe988693401c7064a902b92b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Użycie programu Visual Studio ModelBus w szablonie tekstu
Jeśli pisania szablonów tekstowych, które zapoznały modelu, który zawiera [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] odwołuje się do ModelBus, można rozwiązać odwołania do modeli docelowych dostępu. W takim przypadku należy dostosować szablony tekstowe i do którego istnieje odwołanie języków specyficznego dla domeny (DSLs):  
  
-   DSL, który jest miejscem docelowym odwołania musi mieć kartę ModelBus, która jest skonfigurowana dla dostępu z szablonów tekstowych. Jeśli również dostęp do DSL innego kodu, ponownie skonfigurowanych karta jest wymagana oprócz standardowej karty ModelBus.  
  
     Menedżer adapterów musi dziedziczyć z <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> i musi mieć atrybut `[HostSpecific(HostName)]`.  
  
-   Szablon musi dziedziczyć z <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Jeśli chcesz odczytać DSL modeli, które nie zawierają odwołań ModelBus, można użyć procesory dyrektywy, które są generowane w projektach DSL. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md).  
  
 Aby uzyskać więcej informacji na temat szablonów tekstowych, patrz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Tworzenie adaptera magistrali modelu dla dostępu z szablonów tekstowych  
 Do rozpoznania odwołania ModelBus w szablonie tekstu, element docelowy DSL musi mieć kartę zgodne. Szablony tekstowe wykonywany w oddzielnego parametru AppDomain, z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dokumentów edytory i w związku z tym karta ma można załadować modelu zamiast dostępu do niego za pośrednictwem DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Aby utworzyć karty ModelBus, która jest zgodna z szablonów tekstowych  
  
1.  Jeśli nie ma element docelowy DSL rozwiązania **ModelBusAdapter** projekt, utwórz ją za pomocą Kreatora rozszerzenia Modelbus:  
  
    1.  Pobierz i zainstaluj [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus rozszerzenia, jeśli użytkownik ma nie zostało to zrobione. Aby uzyskać więcej informacji, zobacz [wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij przycisk **włączyć Modelbus**.  
  
    3.  W oknie dialogowym wybierz **I chcesz udostępnić ten DSL do ModelBus**. Można zaznacz obie opcje, jeśli chcesz, aby ten DSL uwidaczniać jej modeli i korzystać z odwołania do innych DSLs.  
  
    4.  Kliknij przycisk **OK**. Nowy projekt "ModelBusAdapter" jest dodane do rozwiązania DSL.  
  
    5.  Kliknij przycisk **Przekształć wszystkie szablony**.  
  
    6.  Ponownie skompiluj rozwiązanie.  
  
2.  Jeśli chcesz uzyskać dostęp DSL, zarówno z szablonu tekstowego i innego kodu, takich jak polecenia, zduplikowany **ModelBusAdapter** projektu:  
  
    1.  W Eksploratorze Windows, skopiuj i Wklej folder zawierający **ModelBusAdapter.csproj**.  
  
    2.  Zmień nazwę pliku projektu (na przykład, aby **T4ModelBusAdapter.csproj**).  
  
    3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **istniejący projekt**. Zlokalizuj nowy projekt karty **T4ModelBusAdapter.csproj**.  
  
    4.  W każdym `*.tt` pliku nowego projektu, należy zmienić przestrzeni nazw.  
  
    5.  Kliknij prawym przyciskiem myszy nowy projekt w Eksploratorze rozwiązań, a następnie kliknij przycisk Właściwości. W edytorze właściwości Zmień nazwy wygenerowanym zestawie i domyślnej przestrzeni nazw.  
  
    6.  W projekcie DslPackage Dodaj odwołanie do nowego projektu karty, aby odwołuje się do obu kart.  
  
    7.  W DslPackage\source.extension.tt Dodaj wiersz, który odwołuje się do nowego projektu karty.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Przekształć wszystkie szablony** i ponownie skompiluj rozwiązanie. Jeśli wystąpią żadne błędy kompilacji.  
  
3.  W nowym projekcie karty Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  W AdapterManager.tt:  
  
    -   Zmień deklarację elementu AdapterManagerBase tak, aby dziedziczyła ona z <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Pod koniec pliku Zastąp atrybutu HostSpecific przed AdapterManager klasy. Usuń następujący wiersz:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Wstaw następujący wiersz:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Ten atrybut filtruje zestaw kart sieciowych, która jest dostępna podczas wyszukiwania z klientem modelbus dla karty.  
  
5.  **Przekształć wszystkie szablony** i ponownie skompiluj rozwiązanie. Jeśli wystąpią żadne błędy kompilacji.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Pisanie szablonu tekstowego, który może rozpoznać odwołań ModelBus  
 Zazwyczaj rozpocząć przy użyciu szablonu, który będzie odczytywać i generuje pliki z DSL "źródła". Ten szablon używa dyrektywy, które są generowane DSL projektu źródłowego do odczytu plików źródłowych modelu w sposób opisany w [podczas uzyskiwania dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md). Jednak źródła DSL zawiera ModelBus odwołania do elementu "docelowego" DSL. W związku z tym chcesz włączyć kod szablonu Rozpoznaj odwołania i dostępu do obiektu docelowego DSL. Dlatego należy dostosować szablon wykonaj następujące czynności:  
  
-   Zmiana klasy podstawowej szablonu, aby <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Obejmują `hostspecific="true"` w dyrektywie template.  
  
-   Dodaj odwołania do zestawów docelowych DSL i jej karty oraz włączyć ModelBus.  
  
-   Nie trzeba dyrektywy, które jest generowany w ramach docelowej DSL.  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let's assume they're all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 Po wykonaniu tego szablonu tekstowego `SourceDsl` dyrektywy ładuje plik `Sample.source`. Szablon mogą uzyskiwać dostęp do elementów modelu, zaczynając od `this.ModelRoot`. Kod można użyć klasy i właściwości tego DSL.  
  
 Ponadto szablon może rozpoznać odwołań ModelBus. W przypadku, gdy punkt odwołania do modelu docelowego, dyrektywy zestawu umożliwiają kodu, użyj klasy i właściwości tego modelu DSL.  
  
-   Jeśli generowany przez projekt DSL dyrektywy nie jest używany, należy także uwzględnić następujące czynności.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Użyj `this.ModelBus` uzyskać dostępu do ModelBus.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Wskazówki: Testowanie szablonu tekstowego, która używa ModelBus  
 W tym przewodniku należy wykonać następujące kroki:  
  
1.  Należy utworzyć dwa DSLs. Jeden DSL *konsumenta*, ma `ModelBusReference` właściwość, która może odwoływać się do innych DSL *dostawcy*.  
  
2.  Utwórz dwie karty ModelBus w dostawcy: Aby uzyskać dostęp przez Szablony tekstowe innych zwykłej kodu.  
  
3.  Tworzenie wystąpienia modeli DSLs w jednym projekcie eksperymentalne.  
  
4.  Ustaw właściwość domeny w jednym modelu wskaż inny model.  
  
5.  Wpisywanie obsługi kliknij dwukrotnie, którego kliknięcie spowoduje otwarcie modelu, która jest wskazywana.  
  
6.  Pisanie szablonu tekstowego, ładowanie pierwszego modelu, wykonaj odwołanie do innego modelu i odczytu innego modelu.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Konstrukcja DSL, który jest dostępny dla ModelBus  
  
1.  Utwórz nowe rozwiązanie DSL. Na przykład wybierz szablon rozwiązania przepływ zadań. Ustaw nazwę języka `MBProvider` i rozszerzenie nazwy pliku z ".provide".  
  
2.  Na diagramie definicji DSL, kliknij prawym przyciskiem myszy pustą część diagramu, który nie jest u góry, a następnie kliknij **włączyć Modelbus**.  
  
    -   Jeśli nie widzisz **włączyć Modelbus**, musisz pobrać i zainstalować rozszerzenie VMSDK ModelBus. Go znaleźć w witrynie VMSDK: [wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  W **włączyć Modelbus** wybierz pozycję **ujawnia tego DSL do ModelBus**, a następnie kliknij przycisk **OK**.  
  
     Nowy projekt, `ModelBusAdapter`, zostanie dodany do rozwiązania.  
  
 Masz teraz DSL, które są dostępne dla szablonów tekstowych przy użyciu ModelBus. Można rozwiązać odwołania do niego w kodzie poleceń, programów obsługi zdarzeń lub reguły, które działają w elemencie AppDomain edytora pliku modelu. Jednak szablony tekstowe działają w oddzielnego parametru AppDomain i nie można uzyskać dostępu modelu, gdy jest edytowany. Jeśli chcesz uzyskać dostęp ModelBus odwołania do tego DSL z szablonu tekstowego, muszą mieć osobne elementu ModelBusAdapter.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Aby utworzyć karty ModelBus, który jest skonfigurowany dla szablonów tekstowych  
  
1.  W Eksploratorze Windows skopiuj i Wklej folder zawierający ModelBusAdapter.csproj.  
  
     Nazwa folderu T4ModelBusAdapter.  
  
     Zmień nazwę pliku projektu T4ModelBusAdapter.csproj.  
  
2.  W Eksploratorze rozwiązań należy dodać do rozwiązania MBProvider T4ModelBusAdapter. Kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **istniejący projekt**.  
  
3.  Kliknij prawym przyciskiem myszy węzeł projektu T4ModelBusAdapter, a następnie kliknij przycisk Właściwości. W oknie właściwości projektu, należy zmienić **nazwy zestawu** i **domyślne Namespace** do `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  W każdym pliku *.tt w T4ModelBusAdapter wstawiać "T4" Ostatnia część obszaru nazw, aby wiersz podobny do następującego.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  W `DslPackage` projekt, Dodaj odwołanie projektu do `T4ModelBusAdapter`.  
  
6.  W DslPackage\source.extension.tt, Dodaj następujący wiersz w obszarze `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  W `T4ModelBusAdapter` projekt, Dodaj odwołanie do: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Otwórz T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  Zmień klasę podstawową AdapterManagerBase do <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Ta część pliku teraz podobny do następującego.  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  Pod koniec pliku Wstaw następujący atrybut dodatkowe przed klasy AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Wynik jest podobny do następującego.  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. Kliknij przycisk **Przekształć wszystkie szablony** w tytułu paska z Eksploratora rozwiązań.  
  
10. Ponownie skompiluj rozwiązanie. Kliknij przycisk F5.  
  
11. Sprawdź, czy działa DSL, naciskając klawisz F5. W projekcie eksperymentalne Otwórz `Sample.provider`. Zamknij eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Teraz można rozwiązać ModelBus odwołania do tego DSL w szablonach tekstowych, a także w zwykłym kodzie.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Konstrukcja DSL z właściwością domeny ModelBus odwołania  
  
1.  Utworzyć nowe DSL za pomocą szablonu rozwiązania minimalnego języka. Nazwa języka MBConsumer i Ustaw rozszerzenie nazwy pliku z ".consume".  
  
2.  W projekcie DSL Dodaj odwołanie do zestawu MBProvider DSL. Kliknij prawym przyciskiem myszy `MBConsumer\Dsl\References` , a następnie kliknij przycisk **Dodaj odwołanie**. W **Przeglądaj** zlokalizuj`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Dzięki temu można utworzyć kod, który używa innych DSL. Jeśli chcesz utworzyć odwołania do kilku DSLs, dodaj je również.  
  
3.  Na diagramie definicji DSL, kliknij prawym przyciskiem myszy diagramu, a następnie kliknij przycisk **włączyć ModelBus**. W oknie dialogowym wybierz **Włącz ten DSL zużywanie ModelBus**.  
  
4.  W klasie `ExampleElement`, Dodaj nową właściwość domeny `MBR`i w oknie właściwości ustaw typ `ModelBusReference`.  
  
5.  Kliknij prawym przyciskiem myszy właściwości domeny na diagramie, a następnie kliknij przycisk **ModelBusReference edytować właściwości określonych**. W oknie dialogowym wybierz **elementu modelu**.  
  
     Ustaw filtr okna dialogowego pliku do następującego.  
  
     `Provider File|*.provide`  
  
     Substring po "&#124;" jest filtr dla okna dialogowego wyboru pliku. Można ustawić, aby zezwolić na wszystkie pliki za pomocą *.\*  
  
     W **typ elementu modelu** listy, wpisz nazwy z jedną lub więcej domen klas w dostawcy DSL (na przykład Company.MBProvider.Task). Można je klas abstrakcyjnych. Jeśli lista pozostanie puste, użytkownik może ustawić odwołanie do każdego elementu.  
  
6.  Zamknij okno dialogowe i **Przekształć wszystkie szablony**.  
  
 Utworzono DSL, która może zawierać odwołania do elementów w innym DSL.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Utwórz ModelBus odwołanie do innego pliku w rozwiązaniu  
  
1.  W rozwiązaniu MBConsumer naciśnij kombinację klawiszy CTRL + F5. Eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otworzy się w **MBConsumer\Debugging** projektu.  
  
2.  Dodaj kopię Sample.provide do **MBConsumer\Debugging** projektu. Jest to konieczne, ponieważ odwołanie ModelBus musi odwoływać się do pliku w tym samym rozwiązaniu.  
  
    1.  Kliknij prawym przyciskiem myszy projekt debugowanie, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **istniejący element**.  
  
    2.  W **Dodaj element** okna dialogowego, ustaw filtr **wszystkie pliki (\*.\*)** .  
  
    3.  Przejdź do `MBProvider\Debugging\Sample.provide` , a następnie kliknij przycisk **Dodaj**.  
  
3.  Otwórz `Sample.consume`.  
  
4.  Kliknij jeden kształt przykładzie, a następnie kliknij w oknie właściwości **[...]**  we właściwości MBR. W oknie dialogowym kliknij **Przeglądaj** i wybierz `Sample.provide`. W oknie elementy rozwiń typ zadania i wybierz jeden z elementów.  
  
5.  Zapisz plik.  
  
     (Nie zamykaj jeszcze eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].)  
  
 Utworzono modelu, który zawiera odwołanie do elementu w modelu innym ModelBus.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Rozpoznania odwołania ModelBus w szablonu tekstowego  
  
1.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz plik przykładowy tekst szablonu. Ustaw w następujący sposób jego zawartości.  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     Zwróć uwagę następujące kwestie:  
  
    1.  `hostSpecific` i `inherits` atrybuty `template` dyrektywa musi być ustawiona.  
  
    2.  Modelu odbiorców jest dostępny w zwykły sposób za pomocą procesora dyrektywy, który został wygenerowany w tym DSL.  
  
    3.  Dyrektywy zestawu, a następnie zaimportuj musi mieć możliwość dostępu ModelBus i typy dostawcy DSL.  
  
    4.  Jeśli wiesz, że wiele MBRs są połączone z tym samym modelu, lepiej jest wywołać CreateAdapter tylko jeden raz.  
  
2.  Zapisz szablon. Sprawdź, czy wynikowy plik tekstowy podobny do następującego.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Rozpoznania odwołania ModelBus programu obsługi gestów  
  
1.  Zamknij eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], jeśli została uruchomiona.  
  
2.  Dodaj plik o nazwie MBConsumer\Dsl\Custom.cs i ustawić jej zawartości do następującego.  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Naciśnij klawisze CTRL + F5.  
  
4.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz `Debugging\Sample.consume`.  
  
5.  Kliknij dwukrotnie jeden kształt.  
  
     Jeśli ustawisz MBR w tym elemencie, otwiera przywoływanym modelem i wybrano element do którego istnieje odwołanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Integrowanie modeli przy użyciu programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
