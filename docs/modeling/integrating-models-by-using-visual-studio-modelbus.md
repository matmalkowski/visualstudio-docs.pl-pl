---
title: "Integrowanie modeli przy użyciu programu Visual Studio Modelbus | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e590b0b0451864c69d548bb643ed4e915f08ad96
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Integrowanie modeli za pomocą Visual Studio Modelbus
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ModelBus udostępnia metody do tworzenia łączy między modelami i z innych narzędzi do modeli. Na przykład możesz połączyć modeli języka specyficznego dla domeny (DSL) i modeli UML. Można utworzyć zintegrowany zestaw DSLs.  
  
 ModelBus pozwala utworzyć unikatową odwołania do modelu lub konkretnego elementu w modelu. To odwołanie mogą być przechowywane poza modelu, na przykład w elemencie w innego modelu. Gdy w przypadku nowszych, narzędzie chce uzyskać dostęp do elementu, infrastruktury magistrali modelu będzie załadować odpowiedni model i zwracać element. Jeśli chcesz, można wyświetlić modelu dla użytkownika. Jeśli plik nie jest dostępny w poprzedniej lokalizacji, ModelBus poprosi użytkownika o znalezienie go. Jeśli użytkownik znajduje się plik, ModelBus naprawi wszystkie odwołania do tego pliku.  
  
> [!NOTE]
>  W bieżącym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementacji ModelBus, połączone modele musi być elementów w tym samym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania.  
  
 Aby uzyskać dodatkowe informacje i przykładowy kod zobacz:  
  
-   [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Modelowanie zestawu SDK dla programu Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
##  <a name="provide"></a>Zapewnianie dostępu do DSL  
 Przed utworzeniem ModelBus odwołania do modelu lub swoich elementów, należy najpierw zdefiniować element ModelBusAdapter DSL. Najprostszym sposobem, w tym celu jest użycie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenie magistrali modelu, który dodaje polecenia do DSL projektanta.  
  
###  <a name="expose"></a>Aby udostępnić definicji magistrali modelu DSL  
  
1.  Pobierz i zainstaluj rozszerzenie magistrali modelu w usłudze Visual Studio, chyba że już zostały zainstalowane. Aby uzyskać więcej informacji, zobacz [wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
2.  Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij przycisk **włączyć Modelbus**.  
  
3.  W oknie dialogowym wybierz **I chcesz udostępnić ten DSL do ModelBus**. Można wybrać obu opcji, jeśli ma to DSL uwidaczniać jej modeli i korzystać z odwołania do innych DSLs.  
  
4.  Kliknij przycisk **OK**. Nowy projekt "ModelBusAdapter" jest dodane do rozwiązania DSL.  
  
5.  Jeśli chcesz uzyskać dostęp DSL z szablonu tekstowego, należy zmodyfikować AdapterManager.tt w nowym projekcie. Pomiń ten krok, jeśli chcesz uzyskać dostęp do DSL z innego kodu, takich jak polecenia i procedury obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [przy użyciu programu Visual Studio ModelBus w szablonu tekstowego](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
    1.  Zmień klasę podstawową AdapterManagerBase do <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
    2.  Pod koniec pliku Wstaw ten atrybut dodatkowe przed klasy AdapterManager:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  W projekcie odwołuje się do elementu ModelBusAdapter, Dodaj **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.  
  
     Jeśli chcesz uzyskać dostęp DSL, zarówno z szablonów tekstowych i innego kodu, należy dwie karty: jeden zmodyfikowany, a drugi nie mają być modyfikowane.  
  
6.  Kliknij przycisk **Przekształć wszystkie szablony**.  
  
7.  Ponownie skompiluj rozwiązanie.  
  
 Teraz istnieje możliwość ModelBus otworzyć wystąpień tego DSL.  
  
 Folder `ModelBusAdapters\bin\*` zawiera zestawy utworzony przez `Dsl` projektu i `ModelBusAdapters` projektu. Aby odwołać tego DSL z innego DSL, należy zaimportować tych zestawów.  
  
### <a name="making-sure-that-elements-can-be-referenced"></a>Upewniając się, że można odwoływać się elementy  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Karty ModelBus umożliwia identyfikację domyślnie identyfikator guid elementu. Te identyfikatory, dlatego musi zostać utrwalony w pliku modelu.  
  
##### <a name="to-ensure-that-element-ids-are-persisted"></a>Aby upewnić się, że element identyfikatory są zachowywane  
  
1.  Otwórz DslDefinition.dsl.  
  
2.  W Eksploratorze DSL rozwiń **zachowanie serializacji Xml**, następnie **dane klasy**.  
  
3.  Dla każdej klasy, do której chcesz utworzyć magistrali modelu odwołuje się:  
  
     Kliknij węzeł klasy i upewnij się, że w oknie właściwości **serializować identyfikator** ma ustawioną wartość `true`.  
  
 Alternatywnie Jeśli chcesz użyć nazwy elementów, aby zidentyfikować elementy zamiast identyfikatorów GUID, można zastąpić części wygenerowanego kart. Zastąp następujące metody w klasie karty:  
  
-   Zastąpienie `GetElementId` do zwrócenia identyfikator, którego chcesz użyć. Ta metoda jest wywoływana podczas tworzenia odwołań.  
  
-   Zastąpienie `ResolveElementReference` aby zlokalizować prawidłowe elementu z odwołania magistrali modelu.  
  
##  <a name="editRef"></a>Uzyskiwanie dostępu do DSL z innego DSL  
 Odwołania magistrali modelu można przechowywać we właściwości domeny w DSL i pisania kodu niestandardowego, który używa ich. Można także pozwolić użytkownikowi utworzenia odwołania magistrali modelu przez pobranie pliku modelu i w jego elemencie.  
  
 Aby włączyć DSL można używać odwołań do innego DSL, najpierw należy go *konsumenta* z odwołania magistrali modelu.  
  
#### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Aby włączyć DSL zużywanie odwołania do narażonych DSL  
  
1.  Na diagramie definicji DSL, kliknij prawym przyciskiem myszy główna część diagramu, a następnie kliknij przycisk **włączyć Modelbus**.  
  
2.  W oknie dialogowym wybierz **chcę włączyć ten model korzystać z odwołania magistrali modelu**.  
  
3.  W projekcie Dsl odbierającą DSL należy dodać następujące zestawy do odwołań projektu. Te zestawy (pliki dll) znajduje się w ModelBusAdapter\bin\\* katalog narażonych DSL.  
  
    -   Zestaw narażonych DSL, na przykład **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   Na przykład zestaw adaptera magistrali modelu narażonych **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  Dodaj następujące zestawy .NET do odwołań projektu odbierającą projektu DSL.  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Do przechowywania odwołania magistrali modelu we właściwości domeny  
  
1.  W definicji DSL odbierającą DSL Dodaj właściwość domeny do klasy domeny, a następnie ustaw jej nazwę.  
  
2.  W oknie właściwości z właściwością domeny zaznaczone, ustaw **typu** do `ModelBusReference`.  
  
 Na tym etapie kod programu można ustawić wartości właściwości, ale jest tylko do odczytu w oknie właściwości.  
  
 Można zezwolić użytkownikom można ustawić właściwości w edytorze specjalne odwołanie ModelBus. Istnieją dwie wersje tego edytora lub *selektora:* jeden umożliwia użytkownikom wybór plik modelu, a drugi użytkownikom wybrać plik modelu i elementu w modelu.  
  
#### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Aby zezwolić użytkownikowi na ustawienie odwołania magistrali modelu we właściwości domeny  
  
1.  Kliknij prawym przyciskiem myszy właściwości domeny, a następnie kliknij przycisk **ModelBusReference edytować właściwości określonych**. Zostanie otwarte okno dialogowe. Jest to *selektora magistrali modelu*.  
  
2.  Wybierz odpowiednie **rodzaj ModelBusReference**: element wewnątrz modelu lub modelu.  
  
3.  W ciągu filtru okna dialogowego pliku, wprowadź ciąg takich jak `Family Tree files |*.ftree`. Subsitute rozszerzenie pliku z narażonych DSL.  
  
4.  Jeśli wybrano opcję odwoływać się do elementu w modelu, można dodać listę typów, które użytkownik może wybrać, na przykład Company.FamilyTree.Person.  
  
5.  Kliknij przycisk **OK**, a następnie kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań.  
  
    > [!WARNING]
    >  Jeśli nie wybrano prawidłowego modelu lub jednostce przycisku OK nie wpłyną, chociaż może się pojawić włączone.  
  
6.  Jeśli określono listę typów docelowego, takich jak Company.FamilyTree.Person, trzeba dodać odwołania do zestawu do projektu DSL odwołuje się do elementu docelowego DSL, na przykład Company.FamilyTree.Dsl.dll biblioteki DLL  
  
#### <a name="to-test-a-model-bus-reference"></a>Aby przetestować odwołania magistrali modelu  
  
1.  Tworzenie DSLs narażonych i spójniejsze.  
  
2.  Uruchom jedno z DSLs w trybie eksperymentalne, naciskając klawisz F5 lub CTRL + F5.  
  
3.  W projekcie debugowanie w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Dodaj pliki, które są wystąpieniami klasy każdego DSL.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ModelBus tylko można rozpoznać odwołania do modeli, które są elementy w tym samym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania. Na przykład nie można utworzyć odwołanie do pliku modelu w innej części systemu plików.  
  
4.  Tworzenie niektórych elementów i łączy w wystąpieniu narażonych DSL i zapisz go.  
  
5.  Otwórz wystąpienie odbierającą DSL i wybierz element modelu, który ma właściwość odwołania magistrali modelu.  
  
6.  W oknie właściwości kliknij dwukrotnie właściwość odwołania magistrali modelu. Zostanie otwarte okno dialogowe selektora.  
  
7.  Kliknij przycisk **Przeglądaj** i wybierz wystąpienie narażonych DSL.  
  
     Selektor również umożliwi wybranie elementu w modelu, jeśli określony element określonego rodzaju odwołania magistrali modelu.  
  
## <a name="creating-references-in-program-code"></a>Tworzenie odwołań w kodzie programu  
 Do przechowywania odwołania do modelu lub elementu w modelu, należy utworzyć `ModelBusReference`. Istnieją dwa rodzaje z `ModelBusReference`: model odwołań i odwołania do elementu.  
  
 Aby utworzyć odwołanie do modelu, należy że element DSL, w którym model jest wystąpienia i nazwa pliku lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elementu projektu modelu.  
  
 Aby utworzyć odwołanie do elementu, należy karty dla pliku modelu, a element, którego ma dotyczyć.  
  
> [!NOTE]
>  Z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, można utworzyć odwołania tylko do elementów w tym samym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania.  
  
### <a name="import-the-exposed-dsl-assemblies"></a>Importuj narażonych zestawy DSL  
 W projekcie odbierającą dodać odwołania do DSL i elementu ModelBusAdapter zestawy narażonych DSL.  
  
 Załóżmy na przykład, że chcesz przechowywać ModelBus odwołań w elementach MusicLibrary DSL. Odwołania ModelBus będzie odnosić się do elementów FamilyTree DSL. W `Dsl` projektu rozwiązania MusicLibrary, w węźle odwołania Dodaj odwołania do następujących zestawów:  
  
-   Fabrikam.FamilyTree.Dsl.dll - narażonych DSL.  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll — karta ModelBus narażonych DSL.  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 Te zestawy można znaleźć w `ModelBusAdapters` projektu narażonych DSL, w obszarze `bin\*`.  
  
 W pliku kodu, gdy utworzysz odwołań zazwyczaj konieczne będzie importowania tych przestrzeni nazw:  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### <a name="to-create-a-reference-to-a-model"></a>Można utworzyć odwołania do modelu  
 Aby utworzyć odwołanie do modelu, dostępu AdapterManager dla narażonych DSL i umożliwia utworzenie odwołania do modelu. Można określić albo ścieżkę pliku, lub `EnvDTE.ProjectItem`.  
  
 Z AdapterManager możesz uzyskać karty, która zapewnia dostęp do poszczególnych elementów w modelu.  
  
> [!NOTE]
>  Karta musi dysponować po zakończeniu z nim. Jak najdogodniejszy sposobów osiągnięcia tego jest z `using` instrukcji. Ilustruje to poniższy przykład.  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 Jeśli chcesz można było użyć `modelReference` później, można przeznaczyć go we właściwości domeny, która ma typ zewnętrznej `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 Aby umożliwić użytkownikom edytowanie tej właściwości domeny, należy użyć `ModelReferenceEditor` jako parametru w atrybucie edytora. Aby uzyskać więcej informacji, zobacz [Zezwalaj użytkownikowi na edycję odwołanie](#editRef).  
  
### <a name="to-create-a-reference-to-an-element"></a>Aby utworzyć odwołanie do elementu  
 Karty, który został utworzony dla modelu może służyć do tworzenia i rozpoznawania odwołań.  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 Jeśli chcesz można było użyć `elementReference` później, można przeznaczyć go we właściwości domeny, która ma typ zewnętrznej `ModelBusReference`. Aby użytkownicy mogli go edytować, użyj `ModelElementReferenceEditor` jako parametru w atrybucie edytora. Aby uzyskać więcej informacji, zobacz [Zezwalaj użytkownikowi na edycję odwołanie](#editRef).  
  
### <a name="resolving-references"></a>Rozpoznawanie odwołania  
 Jeśli masz `ModelBusReference` (MBR) można uzyskać modelu lub element modelu, do którego się odwołuje. Jeśli element jest wyświetlane na diagramie lub w innym widoku, można otworzyć widoku i wybierz element.  
  
 Z MBR można utworzyć adaptera. Z karty można uzyskać katalogu głównego modelu. Można także rozwiązać MBRs, które odwołują się do określonych elementów w modelu.  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Aby rozwiązać odwołania ModelBus w szablonu tekstowego  
  
1.  DSL, który ma dostęp do musi mieć kartę ModelBus, która została skonfigurowana dla dostępu przez szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [zapewnianie dostępu do DSL](#provide).  
  
2.  Zazwyczaj należy będą uzyskiwać dostęp do obiektu docelowego, który DSL przy użyciu odwołania magistrali modelu (MBR) przechowywanych w źródle DSL. Szablon zawiera w związku z tym dyrektywy źródła DSL, a także kod rozwiązać główny rekord rozruchowy. Aby uzyskać więcej informacji na temat szablonów tekstowych, patrz [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 Więcej informacji oraz wskazówki, zobacz [przy użyciu programu Visual Studio ModelBus w szablonu tekstowego](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## <a name="serializing-a-modelbusreference"></a>Serializacja ModelBusReference  
 Jeśli chcesz przechowywać `ModelBusReference` (MBR) w postaci ciągu, można go serializować:  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 MBR, który jest serializowany w ten sposób jest niezależna od kontekstu. Jeśli używasz prostego karty magistrali na podstawie pliku modelu główny rekord rozruchowy zawiera bezwzględną ścieżkę do pliku. To jest wystarczająca, jeśli nie zostanie przeniesiona pliki modelu wystąpienia. Jednak plików modelu zazwyczaj będzie elementów w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Użytkownicy będą oczekiwać możliwość przeniesienia całego projektu do różnych części systemu plików. Zostanie również oczekiwane można zachować zgodność projektu pod kontrolą źródła, a następnie otwórz go na różnych komputerach. Nazwy ścieżek powinny być serializowane w związku z tym względną wobec lokalizacji projektu, który zawiera pliki.  
  
### <a name="serializing-relative-to-a-specified-file-path"></a>Określona ścieżka pliku względem serializacji  
 A `ModelBusReference` zawiera `ReferenceContext`, która jest słownika, w którym można przechowywać informacje, takie jak ścieżka pliku, względem którego powinny być serializowane.  
  
 Do serializacji względem ścieżki:  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 Aby pobrać odwołanie z ciągu:  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### <a name="modelbusreferences-created-by-other-adapters"></a>ModelBusReferences utworzonych przez inne karty  
 Następujące informacje są przydatne, jeśli chcesz tworzyć własne karty.  
  
 A `ModelBusReference` (MBR) składa się z dwóch części: nagłówka MBR, który jest deserializacji przez magistrali modelu, karty specyficzne i który jest obsługiwany przez Menedżera określonej karty. Dzięki temu można podać własne format serializacji karty. Na przykład można odwoływać się bazy danych zamiast pliku lub uzyskać dodatkowe informacje można przechowywać w odwołaniu do karty. Własne karty można umieścić dodatkowe informacje w `ReferenceContext`.  
  
 Podczas deserializacji MBR, należy podać ReferenceContext, który następnie jest przechowywany w obiekcie MBR. Podczas MBR, przechowywane ReferenceContext ułatwiają przez kartę Generowanie ciągu. Zdeserializowana ciąg nie zawiera wszystkie informacje w ReferenceContext. Na przykład prosty karty opartych na plikach, ReferenceContext zawiera główny ścieżki pliku, która nie znajduje się w ciągu MBR serializacji.  
  
 Główny rekord rozruchowy jest rozszeregować w dwóch etapach:  
  
-   `ModelBusReferencePropertySerializer`jest serializator standardowe, która zajmuje się nagłówka MBR. Używa standardowych DSL `SerializationContext` zbioru właściwości, który jest przechowywany w `ReferenceContext` przy użyciu klucza `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. W szczególności `SerializationContext` powinien zawierać wystąpienie `ModelBus`.  
  
-   Karta ModelBus dotyczy określonej karty część główny rekord rozruchowy. Może używać dodatkowych informacji przechowywanych w ReferenceContext z główny rekord rozruchowy. Proste karty opartych na plikach śledzi główny ścieżki plików przy użyciu kluczy `FilePathLoadContextKey` i `FilePathSaveContextKey`.  
  
     Odwołanie do karty w pliku modelu deserializowany jest tylko wtedy, gdy jest używany.  
  
## <a name="to-create-a-model"></a>Aby utworzyć Model  
  
### <a name="creating-opening-and-editing-a-model"></a>Tworzenia, otwierania i edytowania modelu  
 Poniższy fragment jest pobierana z przykładowych automatu stanów w witrynie sieci Web VMSDK. Przedstawia on użycie ModelBusReferences do tworzenia i otwierania modelu i uzyskać diagramu skojarzonego z tym modelem.  
  
 W tym przykładzie nazwa docelowego DSL jest StateMachine. Kilka nazw pochodne, takie jak nazwa klasy modelu i nazwę elementu ModelBusAdapter.  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## <a name="validating-references"></a>Sprawdzanie poprawności odwołania  
 BrokenReferenceDetector testy właściwości domeny w magazynie, który może posiadać ModelBusReferences. Wywołuje akcję użytkownika Podaj, gdzie znajduje się żadnych działań. Jest to szczególnie przydatne dla metod weryfikacji. Następujące metody weryfikacji testów magazynu podczas próby zapisania modelu, a następnie raportuje uszkodzenie odwołań w oknie błędów:  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## <a name="actions-performed-by-the-modelbus-extension"></a>Akcje wykonywane przez rozszerzenie ModelBus  
 Następujące informacje nie jest konieczne, ale mogą być przydatne, jeśli wprowadzisz zwiększone użycie ModelBus.  
  
 Rozszerzenie ModelBus wprowadza następujące zmiany w rozwiązaniu DSL.  
  
 Po kliknięciu prawym przyciskiem myszy na diagramie DSL definicji, kliknij przycisk **włączyć Modelbus**, a następnie wybierz **Włącz ten DSL zużywanie ModelBus**:  
  
-   W projekcie DSL odwołanie jest dodawany do **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   W definicji DSL dodaniu odwołania do typu zewnętrznego: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.  
  
     Widać odwołania w **DSL Explorer**w obszarze **typów domeny**. Aby ręcznie dodać odwołania do typu zewnętrznego, kliknij prawym przyciskiem myszy węzeł główny.  
  
-   Zostanie dodany nowy plik szablonu, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.  
  
 Gdy można ustawić typ właściwości domeny ModelBusReference, a następnie kliknij prawym przyciskiem myszy właściwości i kliknij **ModelBusReference Włącz określone właściwości**:  
  
-   Kilka atrybutów CLR są dodawane do właściwości domeny. Widać je w polu atrybutów niestandardowych, w oknie właściwości. W **Dsl\GeneratedCode\DomainClasses.cs**, widzą atrybutów w deklaracji właściwości:  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 Po kliknięciu prawym przyciskiem myszy na diagramie definicji DSL, kliknij przycisk **włączyć ModelBus**i wybierz **ujawnia tego DSL do ModelBus**:  
  
-   Nowy projekt `ModelBusAdapter` zostanie dodany do rozwiązania.  
  
-   Odwołanie do `ModelBusAdapter` jest dodawany do `DslPackage` projektu. `ModelBusAdapter`odwołuje się do `Dsl` projektu.  
  
-   W **DslPackage\source.extention.tt**, `|ModelBusAdapter|` jest dodawana jako składników MEF.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Użycie programu Visual Studio ModelBus w szablonie tekstu](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
