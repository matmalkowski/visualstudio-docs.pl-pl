---
title: T4 Dyrektywa Include | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 4f46faae63d3fd60715ecd9aec804d03ef6dbc81
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="t4-include-directive"></a>Dyrektywa T4 Include
W szablonie tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mogą zawierać tekst z innego pliku przy użyciu `<#@include#>` dyrektywy. Możesz umieścić `include` dyrektywy w dowolnym miejscu szablonu tekstowego przed pierwszym bloku funkcji klasy `<#+ ... #>`. Pliki załączone może również zawierać `include` dyrektywy i innych dyrektyw. To pozwala na udostępnianie kodu szablonu i standardowych wzorców tekstu szablonu między szablonami.  
  
## <a name="using-include-directives"></a>Używanie dyrektyw Include  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
-   `filePath`może być ścieżką bezwzględną, lub względem bieżącego pliku szablonu.  
  
     Ponadto określonych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzeń można określić ich własnych katalogów do wyszukiwania plików dołączanych. Na przykład po zainstalowaniu wizualizacji i modelowania SDK (narzędzia DSL) następujący folder zostanie dodany do listy include: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
     Te dodatkowe foldery dołączania mogą zależeć od rozszerzenia dołączanego pliku. Na przykład narzędzia DSL zawierają folder jest dostępna wyłącznie dla w tym pliki mające rozszerzenie pliku`.tt`  
  
-   `filePath`może zawierać zmienne środowiskowe rozdzielany z "%". Na przykład:  
  
    ```  
    <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
    ```  
  
-   Nazwa pliku dołączanego musi użyć rozszerzenia `".tt"`.  
  
     Możesz chcieć użyć innego rozszerzenia, takiego jak `".t4"` dołączone pliki. Wynika to z faktu, po dodaniu `.tt` plik do projektu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie ustawia jego **narzędzie niestandardowe** właściwości `TextTemplatingFileGenerator`. Zwykle nie chcesz, żeby dołączone pliki były przekształcane indywidualnie.  
  
     Z drugiej strony należy pamiętać, że w niektórych przypadkach rozszerzenie pliku wpływa na to, w których dodatkowych folderach będą wyszukiwane dołączane pliki. Może to być ważne, gdy masz dołączony plik, który zawiera inne pliki.  
  
-   Dołączona zawartość jest przetwarzana prawie tak, jakby była częścią dołączającego szablonu tekstu. Jednak można dołączyć plik zawierający bloku funkcji klasy `<#+...#>` nawet wtedy, gdy `include` dyrektywy następuje zwykły tekst i bloki formantu standardowego.  
  
-   Użyj `once="true"` aby upewnić się, czy szablon znajduje się tylko raz, nawet wtedy, gdy jest wywoływana z więcej niż jeden plik include.  
  
     Umożliwia wykonanie tej funkcji ułatwiają tworzenie biblioteki wstawki T4 wielokrotnego użytku, obejmujących na zostanie nie martwiąc się, że niektóre fragment kodu ma już one dołączone.  Na przykład załóżmy, że biblioteka bardzo szczegółowych fragmentów, które zajmują się przetwarzania szablonu i C# generacji.  Z kolei są one używane przez niektóre narzędzia bardziej specyficzne dla zadania, takie jak generowanie wyjątków, które można następnie użyć z dowolnego szablonu bardziej specyficzne dla aplikacji. Jeśli narysujesz wykres zależności, zobaczysz, że niektóre wstawki kodu programu byłyby dołączone kilka razy. Ale `once` parametr zapobiega kolejnych dołączenia.  
  
 **MyTextTemplate.tt:**  
  
```  
<#@ output extension=".txt" #>  
Output message 1 (from top template).  
<#@ include file="TextFile1.t4"#>  
Output message 5 (from top template).  
<#  
   GenerateMessage(6); // defined in TextFile1.t4  
   AnotherGenerateMessage(7); // defined in TextFile2.t4  
#>  
  
```  
  
 **TextFile1.t4:**  
  
```  
   Output Message 2 (from included file).  
<#@include file="TextFile2.t4" #>  
   Output Message 4 (from included file).  
<#+ // Start of class feature control block.  
void GenerateMessage(int n)  
{  
#>  
   Output Message <#= n #> (from GenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **TextFile2.t4:**  
  
```  
        Output Message 3 (from included file 2).  
<#+ // Start of class feature control block.  
void AnotherGenerateMessage(int n)  
{  
#>  
       Output Message <#= n #> (from AnotherGenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **Powstałe w ten sposób wygenerowany plik, MyTextTemplate.txt:**  
  
```  
Output message 1 (from top template).  
   Output Message 2 (from included file).  
        Output Message 3 (from included file 2).  
  
   Output Message 4 (from included file).  
  
Output message 5 (from top template).  
   Output Message 6 (from GenerateMessage method).  
       Output Message 7 (from AnotherGenerateMessage method).  
  
```  
  
##  <a name="msbuild"></a>Za pomocą właściwości projektu MSBuild i Visual Studio  
 Mimo że można użyć makra programu Visual Studio podobnego do $(SolutionDir) w dyrektywy include, nie działają one w programie MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.  
  
 Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. W tym przykładzie definiuje właściwość o nazwie `myIncludeFolder`:  
  
```xml  
<!-- Define a project property, myIncludeFolder: -->  
<PropertyGroup>  
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myIncludeFolder">  
      <Value>$(myIncludeFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Teraz można używać właściwości projektu w szablonach tekstowych, które są prawidłowo przekształcane w Visual Studio i MSBuild:  
  
```  
<#@ include file="$(myIncludeFolder)\defs.tt" #>  
```