---
title: "Uzyskiwanie dostępu do modeli z szablonów tekstowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3162350a9afbe7972c4e593049141f533517bdc3
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-models-from-text-templates"></a>Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu
Przy użyciu szablonów tekstowych, można utworzyć plików raportów, pliki kodu źródłowego i inne pliki tekstowe, które są oparte na modeli języka specyficznego dla domeny. Aby uzyskać podstawowe informacje na temat szablonów tekstowych, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Szablony tekstowe będzie działać w trybie eksperymentalne podczas debugowania programu DSL, a także będzie działać na komputerze, na którym wdrożono DSL.  
  
> [!NOTE]
>  Po utworzeniu rozwiązania DSL, przykładowy tekst szablon  **\*.TT —** pliki są generowane w debugowania projektu. Zmiana nazw klas, domeny, te szablony nie będą już działać. Niemniej jednak zawierają one podstawowe dyrektywy, które należy i podaj przykłady, których można zaktualizować do dopasowania sieci DSL.  
  
 Dostęp do modelu z szablonu tekstowego:  
  
-   Ustaw właściwość Dziedzicz dyrektywy szablonu <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Zapewnia to dostęp do sklepu.  
  
-   Określ procesory dyrektywy DSL, który chcesz uzyskać dostęp. Ładuje zestawy dla Twojego DSL, dzięki czemu można użyć jej domeny klas, właściwości i relacji w kodzie szablonu tekstowego. Ładuje plik modelu, który określisz.  
  
 A `.tt` podobny do poniższego przykładu w pliku jest tworzony w projekcie debugowanie podczas tworzenia nowego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania z szablonu DSL minimalnego języka.  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 Zwróć uwagę następujące kwestie dotyczące tego szablonu:  
  
-   Szablon można użyć klasy, właściwości i relacje zdefiniowane w definicji DSL.  
  
-   Szablon ładuje określoną w pliku modelu `requires` właściwości.  
  
-   Właściwość `this` zawiera element główny. Z tego miejsca kodu można przechodzić do innych elementów modelu. Nazwa właściwości jest zwykle taka sama jak klasa domeny katalogu głównego użytkownika DSL. W tym przykładzie jest `this.ExampleModel`.  
  
-   Mimo że język, w którym są zapisywane fragmenty kodu C#, można wygenerować tekst dowolnego rodzaju. Można również napisać kod w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] przez dodanie właściwości `language="VB"` do `template` dyrektywy.  
  
-   Aby debugować szablonu, Dodaj `debug="true"` do `template` dyrektywy. Szablon zostanie otwarty w innym wystąpieniu programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przypadku wystąpienia wyjątku. Jeśli chcesz przerwać w debugerze w określonym w kodzie, Wstaw instrukcję`System.Diagnostics.Debugger.Break();`  
  
     Aby uzyskać więcej informacji, zobacz [debugowanie szablonu tekstowego T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Temat procesora dyrektywy DSL  
 Szablon można użyć klasy domeny, które zdefiniowano w definicji DSL. To jest spowodowanych dyrektywy zwykle wyświetlany w pobliżu początku szablonu. W poprzednim przykładzie jest poniżej.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Nazwy dyrektywy ( `MyLanguage`, w tym przykładzie) jest określana na podstawie nazwy użytkownika DSL. Wywołuje *procesora dyrektywy* wygenerowanych w ramach Twojej DSL. Można znaleźć jego kod źródłowy w **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 Procesor dyrektywy DSL wykonuje dwa podstawowe zadania:  
  
-   Wstawia skutecznie zestawu, a następnie zaimportuj dyrektywy do szablonu, który odwołuje się do Twojego DSL. Dzięki temu można używać klas Twojej domeny w kodzie szablonu.  
  
-   Ładuje określony w pliku `requires` parametru i ustawia właściwość `this` odwołujący się do elementu głównego załadować modelu.  
  
## <a name="validating-the-model-before-running-the-template"></a>Sprawdzanie poprawności modelu przed uruchomieniem szablonu  
 Może spowodować model do weryfikacji przed wykonaniem tego szablonu.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Zwróć uwagę, że:  
  
1.  `filename` i `validation` parametry są oddzielone znakiem ";" oraz nie może być nie separatorów ani spacji.  
  
2.  Lista kategorii weryfikacji Określa, które metody sprawdzania poprawności zostanie wykonane. Wiele kategorii powinny być oddzielone z "&#124;" oraz nie może być nie separatorów ani spacji.  
  
 Jeśli zostanie znaleziony błąd, będzie zgłaszane w oknie błędy, a plik wyników będzie zawierać komunikat o błędzie.  
  
##  <a name="Multiple"></a>Uzyskiwanie dostępu do wielu modeli z szablonu tekstowego  
  
> [!NOTE]
>  Ta metoda umożliwia wyświetlenie wielu modeli w tym samym szablonie, ale nie obsługuje odwołań ModelBus. Modele, które są powiązane przez odwołania ModelBus zamieszczono [przy użyciu programu Visual Studio ModelBus w szablonu tekstowego](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Chcesz uzyskiwać dostęp do więcej niż jednego modelu z tym samym szablonie tekstu, należy wywołać wygenerowanego procesora dyrektywy jeden raz dla każdego modelu. Należy określić nazwę pliku każdego modelu w `requires` parametru. Należy określić nazwy, które ma być używany dla klasy głównym domeny w `provides` parametru. Należy określić różne wartości `provides` parametrów każdego wywołania dyrektywy. Załóżmy na przykład, że masz trzy pliki modelu o nazwie Library.xyz, School.xyz i Work.xyz. Dostęp do nich z tego samego szablonu tekstu, należy napisać trzy wywołania dyrektywy, które przypominają te następujące.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Ten przykładowy kod jest dla języka, który jest oparty na szablonie rozwiązania minimalnego języka.  
  
 Aby uzyskać dostęp do modeli w szablonie tekstu, można teraz napisać kod podobny do kodu w poniższym przykładzie.  
  
```csharp  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>Dynamiczne ładowanie modeli  
 Jeśli chcesz określić w czasie wykonywania modeli można załadować pliku modelu można załadować dynamicznie w kodzie programu zamiast dyrektywy specyficzne dla DSL.  
  
 Jednak jednej z funkcji specyficznych dla DSL dyrektywy jest importowane DSL przestrzeni nazw, dzięki czemu kod szablonu może używać domeny klas zdefiniowanych w tym DSL. Ponieważ dyrektywy nie jest używana, należy dodać  **\<zestawu >** i  **\<zaimportować >** dyrektywy dla wszystkich modeli, które mogą być ładowane. Jest to łatwe, jeśli różne modele, które mogą być ładowane są wszystkie wystąpienia tej samej DSL.  
  
 Aby załadować plik, najbardziej skutecznych metodą jest użycie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. W typowy scenariusz szablon tekstu używa dyrektywy DSL specyficzne załadować pierwszego modelu w zwykły sposób. Ten model zawiera ModelBus odwołania do innego modelu. Można użyć ModelBus Otwórz przywoływanym modelem i dostępu do określonego elementu. Aby uzyskać więcej informacji, zobacz [przy użyciu programu Visual Studio ModelBus w szablonu tekstowego](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 W scenariuszu z mniej zwykle można otworzyć pliku modelu, dla którego masz tylko nazwę pliku, który może nie być w bieżącym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. W takim przypadku można otworzyć pliku przy użyciu techniki opisane w [porady: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Generowanie wielu plikach na podstawie szablonu  
 Jeśli chcesz wygenerować kilka plików — na przykład można wygenerować pliku dla każdego elementu w modelu, istnieje kilka możliwych rozwiązań. Domyślnie tylko jeden plik jest tworzony dla każdego pliku szablonu.  
  
### <a name="splitting-a-long-file"></a>Podział pliku długa  
 W przypadku tej metody Użyj szablonu do generowania pojedynczy plik, oddzielonych ogranicznikiem. Następnie plik zostanie podzielony na części. Istnieją dwa szablony, jedna, aby wygenerować plik jednego i drugiego podziału.  
  
 **LoopTemplate.t4** generuje długi jednoplikowe. Zauważ, że rozszerzenie pliku jest ".t4", ponieważ nie powinny być przetworzone bezpośrednio po kliknięciu **Przekształć wszystkie szablony**. Ten szablon przyjmuje parametr, który określa ciąg ogranicznik, który rozdziela segmentami:  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt`wywołuje `LoopTemplate.t4`, a następnie dzieli wynikowy plik na jego segmentów. Zwróć uwagę, że ten szablon nie trzeba być modelowania szablonu, ponieważ nie odczytu modelu.  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```