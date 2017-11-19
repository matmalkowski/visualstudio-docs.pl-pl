---
title: "T4 dotycząca Dyrektywa szablonu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: "10"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 9b48a6d079ebe43f3d1e3c97a9272e8ad05b6735
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="t4-template-directive"></a>Dyrektywa T4 dotycząca szablonu
A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonu tekstowego T4 zazwyczaj rozpoczyna się od `template` dyrektywy, który określa sposób przetwarzania szablonu. Powinna istnieć nie więcej niż jedna dyrektywa szablonu w szablonie tekstowym i wszystkich plikach, które on uwzględnia.  
  
 Ogólne omówienie pisania szablonów tekstowych, patrz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-template-directive"></a>Używanie dyrektywy Template  
  
```  
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 `template` Dyrektywy ma kilka atrybutów, które pozwalają określić różne aspekty transformacji. Wszystkie atrybuty są opcjonalne.  
  
## <a name="compileroptions-attribute"></a>Atrybut compilerOptions  
 Przykład:  
 `compilerOptions="optimize+"`  
  
 Prawidłowe wartości:  
 Wszystkie prawidłowe opcje kompilatora.  
  
 Ignorowane dla szablonów w czasie wykonywania (wstępnie przetworzonych).  
  
 Te opcje są stosowane, gdy szablon został przekonwertowany na [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)], a wynikowy kod ma być kompilowana.  
  
## <a name="culture-attribute"></a>Atrybut culture  
 Przykład:  
 `culture="de-CH"`  
  
 Prawidłowe wartości:  
 "", niezmienna kultura, co jest ustawieniem domyślnym.  
  
 Kultura jest wyrażona jako ciąg w postaci xx-XX. Na przykład en-US, ja-JP, de-CH, de-DE. Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.CultureInfo?displayProperty=fullName>.  
  
 Atrybut culture określa kulturę, jaka ma zostać użyta w przypadku konwersji bloku wyrażenia na tekst.  
  
## <a name="debug-attribute"></a>Atrybut debug  
 Przykład:  
 ```  
debug="true"  
```  
  
 Prawidłowe wartości:  
 `true, false`. Wartość domyślna to false.  
  
 Jeśli `debug` atrybutu `true`, plik pośredni kod będzie zawierał informacje, które umożliwiają debugera zidentyfikować dokładniej pozycji w szablonie, gdzie przerwania lub wyjątek wystąpił.  
  
 Podczas projektowania szablonów zostanie zapisany plik pośredni kodu do Twojej **% TEMP %** katalogu.  
  
 Aby uruchomić szablon czasu projektowania w debugerze, Zapisz szablon tekstu, a następnie otwórz menu skrótów szablonu tekstu w Eksploratorze rozwiązań i wybierz **debugowania szablon T4**.  
  
## <a name="hostspecific-attribute"></a>Atrybut hostspecific  
 Przykład:  
 ```  
hostspecific="true"  
```  
  
 Prawidłowe wartości:  
 `true, false, trueFromBase`. Wartość domyślna to false.  
  
 Jeśli ustawisz wartość tego atrybutu `true`, właściwość o nazwie `Host` jest dodawana do klasy generowane przez szablon tekstu. Właściwość jest odwołanie do hosta przez aparat przekształcania i jest zadeklarowany jako <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Jeśli został zdefiniowany niestandardowy host, można go rzutować na niestandardowy typ hosta.  
  
 Ponieważ typ tej właściwości zależy od typu hosta, jest to przydatne wyłącznie podczas pisania szablonu tekstu, który działa tylko z określonym hostem. Nie ma zastosowania do [czasu projektowania szablonów](../modeling/design-time-code-generation-by-using-t4-text-templates.md), ale nie [szablony środowiska wykonawczego](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Gdy `hostspecific` jest `true` i za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], można rzutować `this.Host` do IServiceProvider dostępu do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funkcji. Można również użyć `Host.ResolvePath(filename)` uzyskanie bezwzględną ścieżkę pliku w projekcie. Na przykład:  
  
```csharp  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#@ import namespace="System.IO" #>  
<# // Get the Visual Studio API as a service:  
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
<#  
 // Find a path within the current project:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
 Jeśli używasz `inherits` i `hostspecific` atrybuty ze sobą, określić hosta = "trueFromBase" w klasie pochodnej i hosta = "true" w klasie podstawowej. Dzięki temu można uniknąć podwójnego definicji `Host` właściwości w wygenerowanym kodzie.  
  
## <a name="language-attribute"></a>Atrybut language  
 Przykład:  
 `language="VB"`  
  
 Prawidłowe wartości:  
 `C#`(ustawienie domyślne)  
  
 `VB`  
  
 Atrybut language określa język ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]) do użycia na potrzeby kodu źródłowego w blokach instrukcji i wyrażenie. Pliku kodu pośredniego, z którego jest generowane wyjście, użyje tego języka. Język ten nie jest powiązany z językiem generowanym przez szablon, który może być dowolnym rodzajem tekstu.  
  
 Na przykład:  
  
```vb  
<#@ template language="VB" #>  
<#@ output extension=".txt" #>  
Squares of numbers:  
<#  
  Dim number As Integer  
  For number = 1 To 4  
#>  
  Square of <#= number #> is <#= number * number #>  
<#  
  Next number  
#>  
  
```  
  
## <a name="inherits-attribute"></a>Atrybut inherits  
 Można określić, aby kod szablonu dziedziczył z innej klasy, która również może być generowana z szablonu tekstu.  
  
### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Dziedziczenie w szablonie tekstowym czasu wykonywania (wstępnie przetworzonym)  
 Można użyć dziedziczenia między szablonami tekstowymi czasu wykonywania, aby utworzyć podstawowy szablon, który ma kilka wariantów pochodnych. Szablony czasu wykonywania to takie, które mają **narzędzie niestandardowe** ustawioną właściwość **texttemplatingfilepreprocessor —**. Szablon czasu wykonywania generuje kod, który można wywoływać w aplikacji, aby tworzyć tekst zdefiniowany w szablonie. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Jeśli nie określisz `inherits` atrybut, klasa podstawowa i Klasa pochodna zostaną wygenerowane na podstawie szablonu tekstu. Po określeniu `inherits` wygenerowaniu atrybutu klasy pochodnej. Klasa bazowa może być napisana odręcznie, ale musi mieć metody, które są używane w klasie pochodnej.  
  
 Zazwyczaj można określić inny wstępnie przetworzony szablon jako klasę podstawową. Szablon podstawowy dostarcza wspólne bloki tekstu, które mogą się przeplatać z tekstem z szablonów pochodnych. Można użyć klasy funkcji bloki `<#+ ... #>` do definiowania metod, które zawierają fragmentów tekstu. Na przykład można umieścić strukturę tekstu wyjściowego w szablonie podstawowym, zapewniającym wirtualne metody, które mogą zostać zastąpione w szablonach pochodnych:  
  
 Szablon tekstowy (wstępnie przetworzony) czasu wykonywania BaseTemplate.tt:  
 ```scr  
This is the common header.  
<#   
  SpecificFragment1();   
#>  
A common central text.  
<#   
  SpecificFragment2();   
#>  
This is the common footer.  
<#+   
  // Declare abstract methods  
  protected virtual void SpecificFragment1() { }  
  protected virtual void SpecificFragment2() { }  
#>  
  
```  
  
 Szablon tekstowy (wstępnie przetworzony) czasu wykonywania DerivedTemplate1.tt:  
 ```csharp  
<#@ template language="C#" inherits="BaseTemplate" #>  
<#   
  // Run the base template:  
  base.TransformText();  
#>  
<#+  
// Provide fragments specific to this derived template:  
protected override void SpecificFragment1()  
{  
#>  
   Fragment 1 for DerivedTemplate1  
<#+  
}  
protected override void SpecificFragment2()  
{  
#>  
   Fragment 2 for DerivedTemplate1  
<#+  
}  
#>  
  
```  
  
 Kod aplikacji do wywołania DerivedTemplate1:  
 ```csharp  
Console.WriteLine(new DerivedTemplate().TransformText());  
```  
  
 Dane wyjściowe:  
 ```  
This is the common header.  
   Fragment 1 for DerivedTemplate1  
A common central text.  
   Fragment 2 for DerivedTemplate1  
This is the common footer.  
```  
  
 Można utworzyć klasy podstawowe i pochodne w różnych projektach. Pamiętaj, aby dodać podstawowy projekt lub zestawu do odwołania do projektu pochodnych.  
  
 Można również użyć zwykłej klasy odręcznej jako klasy bazowej. Klasa podstawowa musi dostarczać metody stosowane w klasie pochodnej.  
  
> [!WARNING]
>  Jeśli używasz `inherits` i `hostspecific` atrybuty ze sobą, określ hostspecific = "trueFromBase" w klasie pochodnej i hosta = "true" w klasie podstawowej. Dzięki temu można uniknąć podwójnego definicji `Host` właściwości w wygenerowanym kodzie.  
  
### <a name="inheritance-in-a-design-time-text-template"></a>Dziedziczenie w szablonie tekstowym czasu projektowania  
 Szablon tekstu w czasie projektowania jest pliku, dla którego **narzędzie niestandardowe** ustawiono **texttemplatingfilegenerator —**. Szablon generuje plik wyjściowy kodu lub tekstu, który stanowi część sieci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby wygenerować plik wyjściowy, szablon najpierw jest tłumaczony na plik kodu programu pośredniego, którego zwykle nie widać. `inherits` Atrybut określa klasę podstawową dla tego kodu pośrednich.  
  
 Szablon tekstu w czasie projektowania, można określić dla klasy podstawowej, która jest pochodną <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Użyj `<#@assembly#>` dyrektywy do ładowania zestawu lub projekt, który zawiera klasę podstawową.  
  
 Aby uzyskać więcej informacji, zobacz ["Dziedziczenia w szablonów tekstowych" w blogu Nowak Gareth](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
## <a name="linepragmas-attribute"></a>Atrybut LinePragmas  
 Przykład:  
 `linePragmas="false"`  
  
 Prawidłowe wartości:  
 `true`(ustawienie domyślne)  
  
 `false`  
  
 Ustawienie tego atrybutu na false powoduje usunięcie znaczników, które identyfikują numery wierszy w wygenerowanym kodzie. Oznacza to, że kompilator będzie zgłaszał błędy, używając numerów wierszy wygenerowanego kodu. Daje to więcej opcji debugowania, ponieważ można wybrać debugowanie szablonu tekstu lub wygenerowanego kodu.  
  
 Ten atrybut może również pomóc, jeśli jest wyszukiwanie, że bezwzględnej nazwy plików w dyrektywach pragma powodują rozpraszać scaleń pod kontrolą kodu źródłowego.  
  
## <a name="visibility-attribute"></a>Atrybut Visibility  
 Przykład:  
 `visibility="internal"`  
  
 Prawidłowe wartości:  
 `public`(ustawienie domyślne)  
  
 `internal`  
  
 W szablonie tekstowym czasu wykonywania, ustawia atrybut widoczności wygenerowanej klasy. Domyślnie klasy jest częścią publiczny interfejs API w kodzie, ale przez ustawienie `visibility="internal"` można upewnić się, czy tylko kod może użyć klasy generowania tekstu.
