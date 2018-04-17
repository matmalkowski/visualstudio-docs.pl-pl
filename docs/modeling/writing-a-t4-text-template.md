---
title: Pisanie szablonu tekstowego T4 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 140e49af62b2ea1a9bb43b7cf3fb95ccc7b257e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="writing-a-t4-text-template"></a>Pisanie szablonu tekstowego T4
Szablon tekstu zawiera tekst, który zostanie z niego wygenerowany. Na przykład szablon, który tworzy stronę sieci web będzie zawierać "\<html >..." i wszystkich innych standardowych części strony HTML. Wstawione do szablonu są *kontrolować bloki*, które są fragmenty kodu programu. Bloki sterujące zawierają zmienne wartości i umożliwiają warunkowość oraz powtarzalność części tekstu.  
  
 Ta struktura ułatwia tworzenie szablonu, ponieważ można zacząć od prototypu wygenerowanego pliku, po czym stopniowo wstawiać bloki sterujące, które różnicują wynik.  
  
 Szablony tekstu składają się z następujących elementów:  
  
-   **Dyrektywy** — elementy, które kontrolują sposób przetwarzania szablonu.  
  
-   **Bloki** — zawartości, który jest kopiowany bezpośrednio do wyjścia.  
  
-   **Kontrolować bloki** -kod, która wstawia wartości zmiennej na tekst i kontroluje warunkowych lub powtórzony fragmenty tekstu programu.  
  
 Aby wypróbować przykłady w tym temacie, skopiuj je do pliku szablonu zgodnie z opisem w [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Po zakończeniu edycji pliku szablonu, zapisz go, a następnie sprawdź dane wyjściowe **.txt** pliku.  
  
## <a name="directives"></a>Dyrektyw  
 Dyrektywy szablonów tekstu przekazują do silnika tworzenia szablonów tekstu ogólne instrukcje o sposobach generowania kodu przekształcenia oraz pliku wyjściowego.  
  
 Na przykład następująca dyrektywa określa, że plik wyjściowy powinien mieć rozszerzenie .txt:  
  
```  
  
<#@ output extension=".txt" #>  
```  
  
 Aby uzyskać więcej informacji na temat dyrektywy zobacz [dyrektywy szablonu tekstowego T4](../modeling/t4-text-template-directives.md).  
  
## <a name="text-blocks"></a>Bloki tekstu  
 Blok tekstu wstawia tekst bezpośrednio do pliku wyjściowego. Nie istnieje żadne specjalne formatowanie bloków tekstu. Na przykład następujący szablon tekstu będzie generował plik tekstowy zawierający wyraz „Hello”:  
  
```  
<#@ output extension=".txt" #>  
Hello  
```  
  
## <a name="control-blocks"></a>Bloki sterujące  
 Bloki sterujące to sekcje kodu programu służące do przekształcania szablonów. Domyślnym językiem jest C#. Chcąc używać języka [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], można napisać następującą dyrektywę na początku pliku:  
  
```  
<#@ template language="VB" #>  
```  
  
 Język, w którym jest pisany kod źródłowy bloków sterujących, nie ma związku z językiem generowanego tekstu.  
  
### <a name="standard-control-blocks"></a>Standardowe bloki sterujące  
 Standardowy blok sterujący to sekcja kodu programu, która generuje część pliku wyjściowego.  
  
 W pliku szablonu można połączyć dowolną liczbę bloków tekstu i standardowych bloków sterujących . Nie można jednak umieścić jednego bloku sterującego w innym. Każdy blok sterujący jest ujęty w symbole `<# ... #>`.  
  
 Na przykład następujące bloki sterujący i tekstu spowodują, że plik wyjściowy będzie zawierał wiersz „0, 1, 2, 3, 4 Hello!”:  
  
```  
  
      <#  
    for(int i = 0; i < 4; i++)  
    {  
        Write(i + ", ");  
    }  
    Write("4");  
#> Hello!  
```  
  
 Zamiast używać jawnych instrukcji `Write()`, można przeplatać tekst i kod. Poniższy przykład wyświetla "tekst Hello"! cztery razy:  
  
```  
<#  
    for(int i = 0; i < 4; i++)  
    {  
#>  
Hello!  
<#  
    }   
#>  
```  
  
 Blok tekstu można wstawić w każdym miejscu kodu, gdzie jest dozwolona instrukcja `Write();`.  
  
> [!NOTE]
>  Po osadzeniu bloku tekstu w złożonej instrukcji, takie jak pętli lub warunkowy, należy zawsze używać nawiasów klamrowych {...} do bloku tekstu.  
  
### <a name="expression-control-blocks"></a>Bloki sterowania wyrażeniami  
 Blok sterowania wyrażeniem oblicza wartość wyrażenia i konwertuje ją na ciąg. Powstały ciąg jest wstawiany do pliku wyjściowego.  
  
 Bloki sterowania wyrażeniami są ujmowane w symbole `<#= ... #>`.  
  
 Na przykład następujący blok sterujący spowoduje, że plik wyjściowy będzie zawierał cyfrę „5”:  
  
```  
<#= 2 + 3 #>  
```  
  
 Zwracamy uwagę, że symbol otwierający ma trzy znaki „<#=”.  
  
 Wyrażenie może zawierać dowolną zmienną znajdującą się w jego zakresie. Na przykład ten blok spowoduje wyświetlanie wierszy z następującymi liczbami:  
  
```  
<#@ output extension=".txt" #>  
<#  
    for(int i = 0; i < 4; i++)  
    {  
#>  
This is hello number <#= i+1 #>: Hello!  
<#  
    }   
#>  
```  
  
### <a name="class-feature-control-blocks"></a>Bloki sterowania cechami klas  
 Blok sterowania cechami klasy definiuje właściwości, metody i wszelki inny kod, który nie powinien być objęty głównym przekształceniem. Bloki cech klas są często używane do funkcji pomocników.  Zwykle bloki funkcji klasy są umieszczane w osobnych plikach tak, aby można je [uwzględnione](#Include) przez więcej niż jeden szablon tekstu.  
  
 Bloki sterowania cechami klas są ujęte w symbole `<#+ ... #>`.  
  
 Na przykład następujący plik szablonu deklaruje i wykorzystuje metodę:  
  
```  
<#@ output extension=".txt" #>  
Squares:  
<#  
    for(int i = 0; i < 4; i++)  
    {  
#>  
    The square of <#= i #> is <#= Square(i+1) #>.  
<#  
    }   
#>  
That is the end of the list.  
<#+   // Start of class feature block  
private int Square(int i)  
{  
    return i*i;  
}  
#>  
```  
  
 Cechy klas muszą być umieszczone na końcu pliku, w którym są zapisywane. Można jednak dołączyć (`<#@include#>`) plik, który zawiera cechę klasy, nawet jeśli po dyrektywie `include` następują standardowe bloki i tekst.  
  
 Aby uzyskać więcej informacji na temat bloków sterowania, zobacz [bloki formantów szablonów tekstowych](../modeling/text-template-control-blocks.md).  
  
### <a name="class-feature-blocks-can-contain-text-blocks"></a>Bloki cech klas mogą zawierać bloki tekstu  
 Można napisać metodę, która generuje tekst. Na przykład:  
  
```  
List of Squares:  
<#  
   for(int i = 0; i < 4; i++)  
   {  WriteSquareLine(i); }  
#>  
End of list.  
<#+   // Class feature block  
private void WriteSquareLine(int i)  
{  
#>  
   The square of <#= i #> is <#= i*i #>.  
<#+     
}  
#>  
```  
  
 Szczególnie przydatne jest umieszczenie metody generującej tekst w oddzielnym pliku, który może być dołączony przez więcej niż jeden szablon.  
  
## <a name="using-external-definitions"></a>Używanie zewnętrznych definicji  
  
### <a name="assemblies"></a>Zestawy  
 Bloki kodu szablonu mogą wykorzystywać typy zdefiniowane w najczęściej używanych zestawach środowiska .NET, takich jak System.dll. Ponadto mogą się odwoływać do innych zestawów środowiska .NET oraz zestawów utworzonych przez użytkownika. Jako lokalizację zestawu można podać ścieżkę albo silną nazwę:  
  
```  
<#@ assembly name="System.Xml" #>  
```  
  
 W nazwach ścieżek należy używać ich bezwzględnych nazw lub standardowych nazw makr. Na przykład:  
  
```  
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>  
```  
  
 Dyrektywa zestawu nie przynosi efektów w [szablonu tekstowego wstępnie przetworzonych](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md).  
  
### <a name="namespaces"></a>Namespaces  
 Dyrektywa „import” działa tak samo jak klauzula `using` w języku C# lub klauzula `imports` w języku Visual Basic. Umożliwia odwoływanie się z kodu do typów bez podawania w pełni kwalifikowanej nazwy:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 Można użyć tylu dyrektyw `assembly` i `import`, ilu trzeba. Trzeba je umieścić przed blokami tekstu i sterującymi.  
  
 Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca importowania](../modeling/t4-import-directive.md).  
  
###  <a name="Include"></a> W tym kodu i tekstu  
 Dyrektywa `include` wstawia tekst z innego pliku szablonu. Na przykład poniższa dyrektywa spowoduje wstawienie zawartości pliku `test.txt`.  
  
 `<#@ include file="c:\test.txt" #>`  
  
 Dołączona zawartość jest przetwarzana prawie tak, jakby była częścią dołączającego szablonu tekstu. Można jednak dołączyć plik, który zawiera blok cech klasy `<#+...#>`, nawet jeśli po dyrektywie „include” następuje zwykły tekst i standardowe bloki sterujące.  
  
 Aby uzyskać więcej informacji, zobacz [obejmują dyrektywa T4 dotycząca](../modeling/t4-include-directive.md).  
  
### <a name="utility-methods"></a>Metody narzędziowe  
 Istnieją różne metody, np. `Write()`, które są zawsze dostępne w bloku sterującym. Są wśród nich m.in. metody do stosowania wcięć w danych wyjściowych oraz zgłaszania błędów.  
  
 Można także napisać własny zestaw metod narzędziowych.  
  
 Aby uzyskać więcej informacji, zobacz [metody narzędziowe szablonu tekstowego](../modeling/text-template-utility-methods.md).  
  
## <a name="transforming-data-and-models"></a>Przekształcanie danych i modeli  
 Najbardziej przydatnym zastosowaniem szablonu tekstu jest generowanie materiału na podstawie zawartości źródła takiego jak model, baza danych lub plik danych. Szablon wyodrębnia i reformatuje dane. Kolekcja szablonów może przekształcić takie źródło w wiele plików.  
  
 Istnieją różne techniki odczytywania pliku źródłowego.  
  
 **Odczytywanie pliku szablonu tekstowego**. Jest to najprostszy sposób wprowadzenia danych do szablonu:  
  
```  
<#@ import namespace="System.IO" #>  
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...  
```  
  
 **Ładowanie pliku jako model można nawigować**. Bardziej zaawansowaną metodą jest odczyt danych jako modelu, po którym może się poruszać kod źródłowy szablonu tekstu. Na przykład można wczytać plik XML i nawigować po nim przy użyciu wyrażeń XPath. Można także użyć [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765) utworzyć zestaw klas, z którymi mogą odczytywać dane XML.  
  
 **Przeprowadź edycję pliku modelu na diagramie lub formularza.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] udostępnia narzędzia, które można edytować modelu w postaci diagramu lub formularza systemu Windows. Ułatwia to przedyskutowanie modelu z użytkownikami wygenerowanej aplikacji. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] tworzy również zestaw silnie typizowanych klas, które odzwierciedlają strukturę modelu. Aby uzyskać więcej informacji, zobacz [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="relative-file-paths-in-design-time-templates"></a>Względne ścieżki plików w szablonach czasu projektowania  
 W [tekstu w czasie projektowania szablonu](../modeling/design-time-code-generation-by-using-t4-text-templates.md), jeśli chcesz odwołać plik w lokalizacji względnej wobec szablonu tekstowego, użyj `this.Host.ResolvePath()`. Ponadto w dyrektywie `hostspecific="true"` trzeba ustawić wartość `template`:  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of MyFile.txt is:  
<#= myFile #>  
  
```  
  
Można również wykorzystywać inne usługi udostępniane przez hosta. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do programu Visual Studio lub innych hostów z szablonu](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Szablony tekstu czasu projektowania uruchamiane w oddzielnej domenie aplikacji

 Należy zwrócić uwagę że [tekstu w czasie projektowania szablonu](../modeling/design-time-code-generation-by-using-t4-text-templates.md) jest uruchamiany w domenie aplikacji, która jest niezależna od aplikacji głównej. W większości przypadków nie ma to znaczenia, jednak w pewnych skomplikowanych przypadkach mogą wystąpić ograniczenia. Na przykład aby można było przekazać dane między szablonem a osobną usługą, usługa musi udostępniać interfejs API obsługujący serializację.  
  
 (Nie jest to istotne w [szablonu tekstowego środowiska wykonawczego](../modeling/run-time-text-generation-with-t4-text-templates.md), który zawiera kod, który ma być kompilowana wraz z resztą kodu.)  
  
## <a name="editing-templates"></a>Edytowanie szablonów  
 Z internetowej galerii menedżera rozszerzeń można pobrać wyspecjalizowane edytory szablonów tekstu. Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzenia**. Kliknij przycisk **galerii Online**, a następnie użyć narzędzia wyszukiwania.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Zadanie|Temat|  
|----------|-----------|  
|Pisanie szablonu.|[Zalecenia dotyczące pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md)|  
|Generowanie tekstu przy użyciu kodu programu.|[Struktura szablonu tekstowego](../modeling/writing-a-t4-text-template.md)|  
|Generowanie plików w rozwiązaniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Uruchom generowania tekstu poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|  
|Przekształć dane w postaci języka specyficznego dla domeny.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Zapis procesory dyrektywy do przekształcania źródeł danych.|[Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)|
