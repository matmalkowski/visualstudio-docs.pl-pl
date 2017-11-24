---
title: "Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
ms.assetid: 2774b83d-1adb-4c66-a607-746e019b80c0
caps.latest.revision: "38"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 97cf47eafc99abefeebce0f69ac2840617fb35e2
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2017
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4
Szablony tekstowe T4 czasu projektowania umożliwiają generowanie kodu i innych plików w sieci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Zazwyczaj pisania szablonów, aby różnią kodu, które generują one zgodnie z danymi z *modelu*. Model jest pliku lub bazy danych, który zawiera najważniejsze informacje na temat wymagań aplikacji.  
  
 Na przykład można mieć modelu, który definiuje przepływu pracy, jako tabelę lub diagram. Z modelu można wygenerować oprogramowania, która wykonuje przepływ pracy. Zmiany wymagań użytkowników, łatwiej omówiono w nim nowy przepływ pracy z użytkownikami. Trwa ponowne generowanie kodu z przepływu pracy jest bardziej niezawodna niż ręcznie zaktualizowanie kodu.  
  
> [!NOTE]
>  A *modelu* jest źródło danych, które opisano określonej proporcji aplikacji. Może to być wszystkie formularza, w dowolny plik lub bazy danych. Nie musi znajdować się w dowolnym danego formularza, takich jak modelu UML lub model języka specyficznego dla domeny. Typowy modele są w formie tabel lub plików XML.  
  
 Prawdopodobnie już znasz generowania kodu. Podczas definiowania zasobów w **.resx** plików w sieci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania, zestaw klasy i metody jest generowany automatycznie. Plik zasobów umożliwia znacznie łatwiejsze i bardziej niezawodny, aby edytować zasobów niż gdyby było edytować klasy i metody. Przy użyciu szablonów tekstowych może wygenerować kod w taki sam sposób jak ze źródła własnego projektu.  
  
 Szablon tekstu zawiera tekst, który chcesz wygenerować i kod program, który generuje zmiennej fragmenty tekstu. Kod programu i umożliwia Powtórz lub warunkowo pominięcie części wygenerowanego tekstu. Wygenerowanego tekstu może sam można kodu programu, która będzie częścią aplikacji.  
  
## <a name="creating-a-design-time-t4-text-template"></a>Tworzenie szablonu tekstowego T4 czasu projektowania  
  
#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>Aby utworzyć szablon T4 czasu projektowania w programie Visual Studio  
  
1.  Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu lub Otwórz istniejący.  
  
     Na przykład na **pliku** menu, wybierz **nowy**, **projektu**.  
  
2.  Dodawanie pliku szablonu tekstowego do projektu i nadaj mu nazwę, która ma rozszerzenie **.TT —**.  
  
     Aby to zrobić, w **Eksploratora rozwiązań**, w menu skrótów projektu, wybierz **Dodaj**, **nowy element**. W **Dodaj nowy element** wybierz okno dialogowe **szablonu tekstowego** w środkowym okienku.  
  
     Zwróć uwagę, że **narzędzie niestandardowe** właściwość pliku jest **texttemplatingfilegenerator —**.  
  
3.  Otwórz plik. Będzie już zawierać następujące dyrektywy:  
  
    ```  
    <#@ template hostspecific="false" language="C#" #>  
    <#@ output extension=".txt" #>  
    ```  
  
     Jeśli został dodany szablon [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektu, będzie atrybut language "`VB`".  
  
4.  Dodaj tekst na końcu pliku. Na przykład:  
  
    ```  
    Hello, world!  
    ```  
  
5.  Zapisz plik.  
  
     Można napotkać **ostrzeżenie o zabezpieczeniach** komunikat, który prośba o potwierdzenie, że chcesz uruchomić szablon. Kliknij przycisk **OK**.  
  
6.  W **Eksploratora rozwiązań**rozwiń węzeł pliku szablonu, a plik, który ma rozszerzenie **.txt**. Plik zawiera wygenerowane z szablonu.  
  
    > [!NOTE]
    >  Jeśli Twój projekt jest projektem Visual Basic, należy kliknąć opcję **Pokaż wszystkie pliki** Aby wyświetlić plik wyjściowy.  
  
### <a name="regenerating-the-code"></a>Trwa ponowne generowanie kodu  
 Szablon zostanie wykonana, generowanie plików pomocniczych, w żadnym z następujących przypadków:  
  
-   Edytowanie szablonu, a następnie zmień fokus na inny [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna.  
  
-   Zapisz szablon.  
  
-   Kliknij przycisk **Przekształć wszystkie szablony** w **kompilacji** menu. To spowoduje przekształcenie wszystkie szablony w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania.  
  
-   W **Eksploratora rozwiązań**, w menu skrótów dowolnego pliku, wybierz polecenie **Uruchom narzędzie niestandardowe**. Użyj tej metody do przekształcania podzbiór wybrane szablony.  
  
 Można także skonfigurować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu, aby szablony są wykonywane, gdy zostały zmienione pliki danych, które są do odczytu. Aby uzyskać więcej informacji, zobacz [automatycznie ponownie wygenerować kod](#Regenerating).  
  
## <a name="generating-variable-text"></a>Generowanie tekstu zmiennej  
 Szablony tekstowe umożliwiają używanie kodu programu do zmiany zawartości wygenerowanego pliku.  
  
#### <a name="to-generate-text-by-using-program-code"></a>Do generowania tekstu przy użyciu kodu programu  
  
1.  Zmień zawartość `.tt` pliku:  
  
    ```csharp  
    <#@ template hostspecific="false" language="C#" #>  
    <#@ output extension=".txt" #>  
    <#int top = 10;  
  
    for (int i = 0; i<=top; i++)   
    { #>  
       The square of <#= i #> is <#= i*i #>  
    <# } #>  
    ```  
  
    ```vb  
    <#@ template hostspecific="false" language="VB" #>  
    <#@ output extension=".txt" #>  
    <#Dim top As Integer = 10  
  
    For i As Integer = 0 To top  
    #>  
        The square of <#= i #> is <#= i*i #>  
    <#  
    Next  
    #>  
  
    ```  
  
2.  Zapisz plik .TT — i sprawdź plik txt wygenerowane ponownie. Wyświetla listę kwadratów liczb z zakresu od 0 do 10.  
  
 Należy zauważyć, że instrukcje są ujęte w `<#...#>`i jednego wyrażenia w `<#=...#>`. Aby uzyskać więcej informacji, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
 Jeśli piszesz generowania kodu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], `template` dyrektywa musi zawierać `language="VB"`. `"C#"`jest ustawieniem domyślnym.  
  
## <a name="debugging-a-design-time-t4-text-template"></a>Debugowanie szablonu tekstowego T4 czasu projektowania  
 Debugowanie szablonu tekstowego:  
  
-   Wstaw `debug="true"` do `template` dyrektywy. Na przykład:  
  
     `<#@ template debug="true" hostspecific="false" language="C#" #>`  
  
-   Ustaw punkty przerwania w szablonie w taki sam sposób jak zwykłe kodu.  
  
-   Wybierz **debugowania szablon T4** z menu skrótów w pliku szablonu tekstowego w Eksploratorze rozwiązań.  
  
 Szablon zostaną uruchomione i zatrzymane o punktów przerwania. Możesz sprawdzić zmienne i wykonywać krokowo kodu w zwykły sposób.  
  
> [!TIP]
>  `debug="true"`sprawia, że wygenerowany kod mapowania dokładniej szablonu tekstowego, wstawiając numerowanie dyrektywy w wygenerowanym kodzie więcej wierszy. Pozostawienie go punktów przerwania może spowodować zatrzymanie uruchomienia w nieodpowiednim stanie.  
>   
>  Ale nawet wtedy, gdy nie debugowania, można pozostawić klauzuli w dyrektywie template. Powoduje to niewielkie spadek wydajności.  
  
## <a name="generating-code-or-resources-for-your-solution"></a>Generowanie kodu lub zasobów dla rozwiązania  
 Możesz wygenerować pliki programów, które różnią się w zależności od modelu. Model jest wartością wejściową, takie jak bazy danych, pliku konfiguracji, modelu UML, modelu DSL lub innego źródła. Kilka zwykle Generowanie plików programu pochodzą z tego samego modelu. Można to osiągnąć, Utwórz plik szablonu dla każdego pliku wygenerowanego programu, a wszystkie szablony przeczytaniu tego samego modelu.  
  
#### <a name="to-generate-program-code-or-resources"></a>Do generowania kodu programu lub zasobów  
  
1.  Zmień dyrektywy danych wyjściowych, aby wygenerować plik odpowiedniego typu, takich jak .cs, .vb, .resx lub XML.  
  
2.  Wstaw kod, który zostanie wygenerowany kod rozwiązania, która jest wymagana. Na przykład, jeśli chcesz wygenerować trzy deklaracje pól całkowitą w klasie:  
  
    ```csharp  
  
              <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    <# var properties = new string [] {"P1", "P2", "P3"}; #>  
    // This is generated code:  
    class MyGeneratedClass {  
    <# // This code runs in the text template:  
      foreach (string propertyName in properties)  { #>  
      // Generated code:  
      private int <#= propertyName #> = 0;  
    <# } #>  
    }  
    ```  
  
    ```vb  
    <#@ template debug="false" hostspecific="false" language="VB" #>  
    <#@ output extension=".cs" #>  
    <# Dim properties = {"P1", "P2", "P3"} #>  
    class MyGeneratedClass {  
    <#   
       For Each propertyName As String In properties  
    #>  
      private int <#= propertyName #> = 0;  
    <#  
       Next  
    #>  
    }  
  
    ```  
  
3.  Zapisz plik i sprawdź wygenerowanego pliku, który zawiera teraz następujący kod:  
  
    ```  
    class MyGeneratedClass {  
      private int P1 = 0;   
      private int P2 = 0;  
      private int P3 = 0;  
    }  
    ```  
  
### <a name="generating-code-and-generated-text"></a>Generowanie kodu i wygenerowanego tekstu  
 Podczas generowania kodu programu jest najważniejsza, aby uniknąć skomplikowana generowania kodu, która wykonuje w szablonie, a wynikowy wygenerowany kod, który staje się częścią rozwiązania. Nie masz dwóch języków być takie same.  
  
 Poprzedni przykład ma dwie wersje. W jednej wersji generowania kodu jest w języku C#. W bieżącej wersji generowania kodu jest Visual Basic. Ale wygenerowany przez oba tekst jest taki sam, a jest klasa C#.  
  
 W ten sam sposób, można użyć [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu, aby wygenerować kod w dowolnym języku. Wygenerowany tekst musi być w dowolnym języku określonym i nie musi być kod programu.  
  
### <a name="structuring-text-templates"></a>Struktury szablony tekstowe  
 Jako dobrym rozwiązaniem możemy często podzielić kod szablonu na dwie części:  
  
-   Konfiguracja lub części zbieranie danych, która ustawia wartości w zmiennych, ale nie zawiera bloki tekstu. W poprzednim przykładzie, ta część jest inicjowanie `properties`.  
  
     Jest to czasem nazywane sekcji "model", ponieważ tworzy model w magazynie i zwykle odczytuje plik modelu.  
  
-   Część generowania tekstu (`foreach(...){...}` w przykładzie), który używa wartości zmiennych.  
  
 To nie jest konieczne separacji, ale jest stylu, co ułatwia odczytać szablonu zmniejsza się złożoność części, która zawiera tekst.  
  
## <a name="reading-files-or-other-sources"></a>Odczytywanie plików lub innych źródeł  
 Dostęp do pliku modelu lub bazy danych, kod szablonu może użyć zestawy, takie jak System.XML. Aby uzyskać dostęp do tych zestawów, należy wstawić dyrektywy, takich jak te:  
  
```  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.IO" #>  
```  
  
 `assembly` Dyrektywy udostępnia określonego zestawu w kodzie szablonu w taki sam sposób jak sekcji odwołań [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Nie trzeba przeprowadzać zawiera odwołanie do System.dll, do którego odwołuje się automatycznie. `import` Dyrektywy umożliwia korzystanie z typów bez użycia ich w pełni kwalifikowane nazwy w taki sam sposób jak `using` dyrektywy w pliku zwykłego programu.  
  
 Na przykład po zaimportowaniu **System.IO**, można zapisać:  
  
```csharp  
  
      <# var properties = File.ReadLines("C:\\propertyList.txt");#>  
...  
<# foreach (string propertyName in properties) { #>  
...  
```  
  
```vb  
<# For Each propertyName As String In   
             File.ReadLines("C:\\propertyList.txt")  
#>  
  
```  
  
### <a name="opening-a-file-with-a-relative-pathname"></a>Otwarcie pliku względną nazwę ścieżki  
 Aby załadować pliku z lokalizacji względnej wobec szablonu tekstowego, można użyć `this.Host.ResolvePath()`. Aby użyć tej funkcji. Hosta, należy ustawić `hostspecific="true"` w `template`:  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
  
```  
  
 Następnie można napisać, na przykład:  
  
```csharp  
<# string fileName = this.Host.ResolvePath("filename.txt");  
  string [] properties = File.ReadLines(filename);  
#>  
...  
<#  foreach (string propertyName in properties { #>  
...  
  
```  
  
```vb  
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")  
   Dim properties = File.ReadLines(filename)  
#>  
...  
<#   For Each propertyName As String In properties  
...  
#>  
  
```  
  
 Można również użyć `this.Host.TemplateFile`, który wskazuje nazwę bieżącego pliku szablonu.  
  
 Typ `this.Host` (w języku VB, `Me.Host`) jest `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.  
  
### <a name="getting-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Pobieranie danych z[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Aby korzystać z usług w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ustaw `hostSpecific` atrybutu i obciążenia `EnvDTE` zestawu. Można następnie użyć IServiceProvider.GetCOMService() dostęp do innych usług i DTE. Na przykład:  
  
```scr  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
> [!TIP]
>  Szablonu tekstowego działa w domenie aplikacji i usług są używane przez przekazywanie. W takim przypadku GetCOMService() jest bardziej niezawodna niż GetService().  
  
##  <a name="Regenerating"></a>Automatyczne ponowne generowanie kodu  
 Zazwyczaj kilka plików w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania są generowane z jednego modelu wejściowego. Każdy plik jest generowany na podstawie własnych szablonu, ale szablonów, które wszystkie odnoszą się do tego samego modelu.  
  
 W przypadku zmiany modelu źródłowego, należy ponownie uruchom wszystkie szablony w rozwiązaniu. W tym celu należy ręcznie wybrać **Przekształć wszystkie szablony** na **kompilacji** menu.  
  
 Jeśli zainstalowano [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania SDK może mieć wszystkie szablony przekształcone automatycznie przy każdym wykonaniu kompilacji. Aby to zrobić, Edytuj plik projektu (pliku .csproj lub .vbproj) w edytorze tekstów i dodaj następujące wiersze zbliża się koniec pliku, po innych `<import>` instrukcji:  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
```  
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />  
<PropertyGroup>  
   <TransformOnBuild>true</TransformOnBuild>  
   <!-- Other properties can be inserted here -->  
</PropertyGroup>  
```  
  
 Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="error-reporting"></a>Raportowanie błędów  
 Można umieścić o błędach i komunikaty ostrzegawcze w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] błędów w oknie, można użyć następujących metod:  
  
```  
Error("An error message");  
Warning("A warning message");  
```  
  
##  <a name="Converting"></a>Konwertowanie istniejącego pliku do szablonu  
 Przydatna funkcja szablonów jest, że wyglądają bardzo podobnie pliki, które generują one wraz z kodu wstawionego program. Sugeruje to przydatne metody tworzenia szablonu. Najpierw utwórz zwykły plik jako prototyp, takich jak [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plików i stopniowego wprowadzenia generowania kodu, który różni się plik wynikowy.  
  
#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Aby przekonwertować istniejącego pliku szablonu czasu projektowania  
  
1.  Do Twojej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt, Dodaj plik typu, który chcesz wygenerować, takich jak `.cs`, `.vb`, lub `.resx` pliku.  
  
2.  Przetestuj nowy plik, aby upewnić się, że działa.  
  
3.  W Eksploratorze rozwiązań, zmień rozszerzenie nazwy pliku na **.TT —**.  
  
4.  Sprawdź następujące właściwości **.TT —** pliku:  
  
    |||  
    |-|-|  
    |**Niestandardowe narzędzie =**|**Texttemplatingfilegenerator —**|  
    |**Akcja kompilacji =**|**Brak**|  
  
5.  Wstaw następujące wiersze na początku pliku:  
  
    ```  
    <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    ```  
  
     Jeśli chcesz zapisać generowania kodu szablonu w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]ustaw `language` atrybutu `"VB"` zamiast `"C#"`.  
  
     Ustaw `extension` atrybutu rozszerzenie nazwy pliku dla typu pliku, który chcesz wygenerować, na przykład `.cs`, `.resx`, lub `.xml`.  
  
6.  Zapisz plik.  
  
     Pomocniczy plik utworzono z określonym rozszerzeniem. Jego właściwości są prawidłowe dla typu pliku. Na przykład **Akcja kompilacji** byłoby właściwości pliku CS **skompilować**.  
  
     Sprawdź, czy wygenerowany plik zawiera tę samą zawartość oryginalnego pliku.  
  
7.  Określ część pliku, które różnią się. Na przykład części, która jest wyświetlana tylko w niektórych warunkach, lub część jest ponownie, lub gdy różnią się określone wartości. Wstaw generowania kodu. Zapisz plik i Sprawdź poprawnie wygenerowania plików pomocniczych. Powtórz ten krok.  
  
## <a name="guidelines-for-code-generation"></a>Wskazówki dotyczące generowania kodu  
 Zobacz [wytyczne dotyczące szablonów tekstowych T4 zapisu](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
## <a name="next-steps"></a>Następne kroki  
  
|Następny krok|Temat|  
|---------------|-----------|  
|Zapisz i debugowanie szablonu tekstowego bardziej zaawansowanych, z kodem, który używa funkcji pomocniczych, dołączonych plików i danych zewnętrznych.|[Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)|  
|Generowanie dokumentów na podstawie szablonów w czasie wykonywania.|[Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|  
|Uruchom generowania tekstu poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|  
|Przekształć dane w postaci języka specyficznego dla domeny.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Zapis procesory dyrektywy do przekształcania źródeł danych.|[Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md)
