---
title: Zadania wbudowane programu MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/21/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39bc1acd059c9a915f330c74140c89d5f4fa40ff
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31574643"
---
# <a name="msbuild-inline-tasks"></a>Zadania wbudowane programu MSBuild
Zadania programu MSBuild są zazwyczaj tworzone przez kompilowanie klasy, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejsu. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
 Uruchamianie programu .NET Framework w wersji 4, można utworzyć zadania wbudowanego w pliku projektu. Nie masz Utwórz osobny zestaw do obsługi zadań. Dzięki temu łatwiejsze do śledzenia kodu źródłowego i łatwiejsze do wdrożenia zadania. Kod źródłowy jest zintegrowany skryptu.  
  
## <a name="the-structure-of-an-inline-task"></a>Struktura zadania wbudowanego  
 Zadania wbudowanego jest zawarty w [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Zadania wbudowane i `UsingTask` element, który go zawiera zwykle są zawarte w pliku .targets i importowane do innych plików projektu, zgodnie z wymaganiami. Poniżej przedstawiono podstawowe wbudowanego zadania. Zwróć uwagę, że nie działają.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="" />  
      <Using Namespace="" />  
      <Code Type="Fragment" Language="cs">  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 `UsingTask` Element w przykładzie ma trzy atrybuty, które opisano zadania i fabryki zadań wbudowany, który kompiluje go.  
  
-   `TaskName` Atrybutu nazwy zadania, w tym przypadku `DoNothing`.  
  
-   `TaskFactory` Atrybut nazwy klasy, która implementuje fabryki zadań w tekście.  
  
-   `AssemblyFile` Atrybut podaje lokalizację wbudowanego fabryki zadań. Alternatywnie można użyć `AssemblyName` atrybutu, aby określić w pełni kwalifikowana nazwa klasy fabryki zadań wbudowany, która znajduje się w globalnej pamięci podręcznej zestawów (GAC).  
  
 Pozostałe elementy `DoNothing` zadań są puste, znajdują się w celu zilustrowania kolejności i struktura zadania wbudowanego. Bardziej niezawodna w przykładzie przedstawiono w dalszej części tego tematu.  
  
-   `ParameterGroup` Element jest opcjonalny. W przypadku deklaruje parametry dla zadania. Aby uzyskać więcej informacji na temat parametrów wejściowych i wyjściowych zobacz "Wejściowych i wyjściowych parametry" w dalszej części tego tematu.  
  
-   `Task` Elementu opisuje i zawiera kod źródłowy zadań.  
  
-   `Reference` Element określa odwołania do zestawów platformy .NET, które są używane w kodzie. Jest to równoważne dodania odwołania do projektu programu Visual Studio. `Include` Atrybut ścieżka przywoływanego zestawu.  
  
-   `Using` Element zawiera przestrzenie nazw, które chcesz uzyskać dostęp. Przypomina to `Using` instrukcji języka Visual C#. `Namespace` Atrybut określa przestrzeń nazw do uwzględnienia.  
  
 `Reference` i `Using` elementy są niezależne od języka. Zadania wbudowane można pisać w jednym z obsługiwanych języków .NET CodeDom, na przykład Visual Basic lub Visual C#.  
  
> [!NOTE]
>  Elementy zawarte `Task` elementu są specyficzne dla fabryki zadań, w tym przypadku fabryki zadań kodu.  
  
### <a name="code-element"></a>Element Code  
 Ostatni element podrzędny pojawił się w `Task` jest element `Code` elementu. `Code` Element zawiera lub lokalizuje kod, który ma być kompilowana w zadanie. Umieść w `Code` elementu zależy od tego, jak chcesz zapisać zadania.  
  
 `Language` Atrybut określa język, w którym napisano kodu. Dopuszczalne wartości to `cs` dla C# `vb` dla języka Visual Basic.  
  
 `Type` Atrybut określa typ kodu, który można znaleźć w `Code` elementu.  
  
-   Jeśli wartość `Type` jest `Class`, a następnie `Code` element zawiera kod klasy, która pochodzi z <xref:Microsoft.Build.Framework.ITask> interfejsu.  
  
-   Jeśli wartość `Type` jest `Method`, kod definiuje zastępująca `Execute` metody <xref:Microsoft.Build.Framework.ITask> interfejsu.  
  
-   Jeśli wartość `Type` jest `Fragment`, a następnie kod definiuje zawartość `Execute` metody, ale nie podpisu lub `return` instrukcji.  
  
 Kodu pojawia się zwykle między `<![CDATA[` znacznika i `]]>` znacznika. Ponieważ kod znajduje się w sekcji CDATA, nie trzeba martwić się o anulowanie zarezerwowanych znaków, na przykład "\<" lub ">".  
  
 Alternatywnie można użyć `Source` atrybutu `Code` element, aby określić lokalizację pliku, który zawiera kod dla zadania. Kod w pliku źródłowym musi być typu, który jest określony przez `Type` atrybutu. Jeśli `Source` jest obecny, atrybut wartość domyślną `Type` jest `Class`. Jeśli `Source` jest nieobecna, wartością domyślną jest `Fragment`.  
  
> [!NOTE]
>  Podczas definiowania klasy zadań w pliku źródłowym, nazwa klasy należy uzgodnić z `TaskName` atrybutu odpowiadającego [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu.  
  
## <a name="hello-world"></a>Witaj Świecie  
 Poniżej przedstawiono bardziej niezawodne zadania wbudowanego. Wyświetla zadania HelloWorld "Hello, world!" na domyślnego urządzenia rejestrowania błędów, który jest zwykle konsoli systemu lub Visual Studio **dane wyjściowe** okna. `Reference` Element w tym przykładzie jest on dołączony tylko do ilustracji.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>  
      <Using Namespace="System.IO"/>  
      <Code Type="Fragment" Language="cs">  
<![CDATA[  
// Display "Hello, world!"  
Log.LogError("Hello, world!");  
]]>  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 Można zapisać zadania HelloWorld w pliku o nazwie HelloWorld.targets, a następnie wywołać go z projektu w następujący sposób.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Dane wejściowe i parametry wyjściowe  
 Elementy podrzędne są wbudowane zadania parametry `ParameterGroup` elementu. Każdy parametr przyjmuje nazwę elementu, który definiuje ją. Poniższy kod definiuje parametr `Text`.  
  
```xml  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 Parametry może mieć co najmniej jeden z tych atrybutów:  
  
-   `Required` jest opcjonalny atrybut, który jest `false` domyślnie. Jeśli `true`, a następnie parametr jest wymagany i musi mieć określoną wartość przed wywołaniem zadania.  
  
-   `ParameterType` jest opcjonalny atrybut, który jest `System.String` domyślnie. Do dowolnego typu pełni kwalifikowana, co element lub wartość, który może zostać przekonwertowany do i z ciągu za pomocą System.Convert.ChangeType może zostać ustawiony. (Innymi słowy, dowolnego typu, które mogą zostać przekazane do i z zadanie zewnętrzne.)  
  
-   `Output` jest opcjonalny atrybut, który jest `false` domyślnie. Jeśli `true`, a następnie parametr musi mieć określoną wartość przed powrotem z metody Execute.  
  
 Na przykład  
  
```xml  
<ParameterGroup>  
    <Expression Required="true" />  
      <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  
  
 definiuje trzy następujące parametry:  
  
-   `Expression` jest wymaganego parametru wejściowego typu System.String.  
  
-   `Files` jest wymagany element parametru wejściowego listy.  
  
-   `Tally` jest parametrem wyjściowym typu System.Int32.  
  
 Jeśli `Code` element ma `Type` atrybutu `Fragment` lub `Method`, a następnie właściwości są tworzone automatycznie dla każdego parametru. W przeciwnym razie wartość właściwości musi być jawnie zadeklarowany w kodzie źródłowym zadań i musi dokładnie odpowiadać ich definicje parametru.  
  
## <a name="example"></a>Przykład  
 Następujące zadania wbudowanego zamienia każde wystąpienie tokenu w danym pliku z danej wartości.  
  
```xml  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">  
  
  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">  
    <ParameterGroup>  
      <Path ParameterType="System.String" Required="true" />  
      <Token ParameterType="System.String" Required="true" />  
      <Replacement ParameterType="System.String" Required="true" />  
    </ParameterGroup>  
    <Task>  
      <Code Type="Fragment" Language="cs"><![CDATA[  
string content = File.ReadAllText(Path);  
content = content.Replace(Token, Replacement);  
File.WriteAllText(Path, content);  
  
]]></Code>  
    </Task>  
  </UsingTask>  
  
  <Target Name='Demo' >  
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Przewodnik: Tworzenie zadania wbudowanego](../msbuild/walkthrough-creating-an-inline-task.md)
