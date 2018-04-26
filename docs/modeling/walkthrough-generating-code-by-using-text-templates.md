---
title: 'Wskazówki: generowanie kodu przy użyciu szablonów tekstowych'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ad7f424f9c44623a2112680757598f8076358f36
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-generating-code-by-using-text-templates"></a>Wskazówki: generowanie kodu przy użyciu szablonów tekstowych
Generowanie kodu służy do tworzenia kodu program, który jest silnie typizowane i jeszcze można łatwo zmienić po zmianie modelu źródłowego. Natomiast to alternatywny technice zapisywania całkowicie ogólny program, który akceptuje w pliku konfiguracji, który jest bardziej elastyczna, ale wyniki w kodzie, który nie jest tak łatwe do odczytu i zmienić, ani nie ma takich dobrą wydajność. W tym przewodniku przedstawiono takich korzyści.

## <a name="typed-code-for-reading-xml"></a>Kod maszynowy odczytywania pliku XML
 Przestrzeń nazw zestawów System.Xml udostępnia zaawansowane narzędzia do ładowania dokumentu XML, a następnie przechodząc go za darmo w pamięci. Niestety wszystkie węzły mają ten sam typ, XmlNode. W związku z tym jest bardzo proste popełnione programowania, takich jak oczekiwano niewłaściwy typ węzła podrzędnego lub nieprawidłowe atrybuty.

 W tym projekcie przykładowy szablon odczytuje przykładowego pliku XML i generuje klasy, które odpowiadają każdego typu węzła. W kodzie odręcznego można użyć tych klas, można przejść do pliku XML. Można również uruchomić aplikację na inne pliki tego samego typu węzła. Celem przykładowy plik XML jest zapewnienie przykłady wszystkie typy węzłów, które mają aplikacji biznesowych w radzeniu sobie z.

> [!NOTE]
>  Aplikacja [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765), która jest dostarczana z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], można wygenerować klas jednoznacznie z plików XML. Jako przykład znajduje się szablon, pokazano poniżej.

 Oto przykładowy plik:

```
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

 W projekcie tworzy tego przewodnika, można napisać kod, takie jak wymienione poniżej i IntelliSense wyświetla monit o poprawne nazwy atrybutu i podrzędnych podczas pisania:

```
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

 Natomiast to kodem bez typu, który może zapisać bez szablonu:

```
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

 W wersji jednoznacznie zmiany do schematu XML spowoduje zmian dla klasy. Kompilator wyróżnione części kodu aplikacji, która musi zostać zmienione. W wersji bez typu, która używa ogólnego kod XML nie ma takiej obsługi.

 W tym projekcie jednego pliku szablonu służy do generowania klasy, które umożliwiają typizowaną wersję.

## <a name="setting-up-the-project"></a>Konfigurowanie projektu

### <a name="create-or-open-a-c-project"></a>Utwórz lub Otwórz projekt C#
 Ta technika może dotyczyć żadnego kodu projektu. W tym przewodniku zastosowano projektu C# i do celów testowych możemy korzystać z aplikacji konsoli.

##### <a name="to-create-the-project"></a>Aby utworzyć projekt

1.  Na **pliku** kliknij menu **nowy** , a następnie kliknij przycisk **projektu**.

2.  Kliknij przycisk **Visual C#** węzeł, a następnie w **szablony** okienku, kliknij przycisk **aplikacji konsoli.**

### <a name="add-a-prototype-xml-file-to-the-project"></a>Dodaj plik XML prototypu do projektu
 Celem tego pliku jest zapewnienie przykłady typów węzła XML, które chcesz mieć możliwość odczytu. Może to być plik, który będzie używany na potrzeby testowania aplikacji. Szablon utworzy klasę C# dla każdego typu węzła, w tym pliku.

 Ten plik powinien być częścią projektu, aby szablon może go odczytać, ale nie będzie go można wbudować do skompilowanej aplikacji.

##### <a name="to-add-an-xml-file"></a>Aby dodać plik XML

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj** , a następnie kliknij przycisk **nowy element**.

2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku XML** z **szablony** okienka.

3.  Dodaj zawartość próbki do pliku.

4.  W ramach tego przewodnika, nadaj nazwę plikowi `exampleXml.xml`. Ustaw zawartość pliku jako pliku XML w poprzedniej sekcji.

 .

### <a name="add-a-test-code-file"></a>Dodaj plik kodu testu
 Dodawanie pliku C# do projektu i zapisać w nim próbki kodu, który chcesz mieć możliwość zapisywania. Na przykład:

```
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

 Na tym etapie ten kod nie będzie można skompilować. Podczas pisania szablonu zostaną wygenerowane klasy, które zezwolenie na powiodło się.

 Bardziej szczegółowe badanie można sprawdzić dane wyjściowe tej funkcji testu w znanych zawartości przykładowy plik XML. Jednak w tym przewodniku będzie spełniony kiedy kompiluje metody testowej.

### <a name="add-a-text-template-file"></a>Dodawanie pliku szablonu tekstowego
 Dodawanie pliku szablonu tekstowego, a następnie ustaw rozszerzenie wyjścia do "CS".

##### <a name="to-add-a-text-template-file-to-your-project"></a>Aby dodać do projektu pliku szablonu tekstowego

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**.

2.  W **Dodaj nowy element** wybierz okno dialogowe **szablonu tekstowego** z **szablony** okienka.

    > [!NOTE]
    >  Upewnij się, możesz dodać szablonu tekstowego, a nie wstępnie przetworzony szablonu tekstowego.

3.  W pliku w dyrektywie template zmienić `hostspecific` atrybutu `true`.

     Ta zmiana spowoduje włączenie kod szablonu w celu uzyskania dostępu do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usług.

4.  W dyrektywie danych wyjściowych należy zmienić atrybutu rozszerzenia na "CS", tak, aby szablon generuje plik C#. W projektach Visual Basic czy zmienić go do ".vb".

5.  Zapisz plik. Na tym etapie plik szablonu tekst powinien zawierać następujące wiersze:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

 .

 Należy zauważyć, że plik .cs jest widoczny w Eksploratorze rozwiązań zależny pliku szablonu. Można to sprawdzić, klikając [+] obok nazwy pliku szablonu. Ten plik został wygenerowany z pliku szablonu, Zapisz lub Przenieś fokus od pliku szablonu. Wygenerowany plik zostanie skompilowany w ramach projektu.

 Dla wygody, podczas opracowywania pliku szablonu, Rozmieść okna pliku szablonu i wygenerowanego pliku, tak aby były widoczne obok siebie. Dzięki temu można natychmiast zobaczyć dane wyjściowe szablonu. Można również zauważyć, że gdy szablon generuje nieprawidłowy kod C#, błędy zostaną wyświetlone w oknie komunikat błędu.

 Wszelkich zmian, które należy wykonać bezpośrednio w wygenerowanym pliku zostaną utracone, jeśli zapiszesz plik szablonu. Użytkownik powinien w związku z tym należy unikać edytowania wygenerowanego pliku albo go edytować tylko w przypadku krótkich eksperymentów. Czasami jest to przydatne, i spróbuj krótki fragment kodu w wygenerowanym pliku, w którym IntelliSense jest używany w operacji, skopiuj go do pliku szablonu.

## <a name="developing-the-text-template"></a>Tworzenie szablonu tekstowego
 Następujące najlepsze porady na elastyczne programowanie będzie opracowywania szablonu w krokach małych wyczyszczenie niektóre błędy na każdego kolejnego przyrostu wartości, dopóki kod testu kompiluje i działa poprawnie.

### <a name="prototype-the-code-to-be-generated"></a>Prototyp będzie generowany kod
 Kod testu wymaga klasy dla każdego węzła w pliku. W związku z tym niektóre błędy kompilacji zniknie Jeśli Dołącz te wiersze do szablonu, a następnie zapisz go:

```
class Catalog {}
class Artist {}
class Song {}
```

 Dzięki temu można zobaczyć, co jest wymagane, ale powinny być generowane deklaracje typów węzła w przykładowym pliku XML. Usuń te wiersze eksperymentalne z szablonu.

### <a name="generate-application-code-from-the-model-xml-file"></a>Generowanie kodu aplikacji z pliku XML modelu
 Do odczytania pliku XML i Generowanie deklaracji klasy, Zastąp zawartość następującym kodem szablonu szablonu:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

 Zastąp ścieżkę pliku poprawną ścieżkę projektu.

 Zwróć uwagę, ograniczniki blok kodu `<#...#>`. Te ograniczniki nawiasów fragment kodu program, który generuje tekst. Ograniczniki blok wyrażenia `<#=...#>` nawiasów wyrażenia, które może przyjąć na ciąg.

 Podczas pisania szablon, który generuje kod źródłowy aplikacji są zajmujących dwa teksty inny program. Program wewnątrz ograniczników blok kodu ma być uruchamiany zawsze możesz zapisać szablon lub przejść do innego okna. Tekst, który generuje i pojawi się poza ograniczniki, jest kopiowany do wygenerowanego pliku i staje się częścią kodu aplikacji.

 `<#@assembly#>` Dyrektywy zachowuje się jak odwołanie, udostępniając zestawu kod szablonu. Listę zestawów, które zostały odebrane przez szablon jest oddzielony od listy odwołań w projekcie aplikacji.

 `<#@import#>` Dyrektywy działa jak `using` instrukcji, co umożliwia używanie krótkiej nazwy klasy w importowanych przestrzeni nazw.

 Niestety, chociaż ten szablon generuje kod, generuje deklaracji klasy dla każdego węzła w przykładowy plik XML, dzięki czemu Jeśli istnieje kilka wystąpień `<song>` węzła, pojawi się kilka deklaracji utworu klasy.

### <a name="read-the-model-file-then-generate-the-code"></a>Odczytanie pliku modelu, a następnie generowania kodu
 Wiele szablonów tekstowych wykonaj wzorzec, w którym pierwsza część szablonu odczytuje plik źródłowy, a druga część generuje szablon. Należy odczytać wszystkich przykładowy plik Podsumowując typy węzłów, które zawiera, a następnie wygeneruj deklaracji klasy. Inny `<#@import#>` jest potrzebna, dzięki czemu możemy użyć `Dictionary<>:`

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>Dodaj metodę pomocniczą
 Formant bloku funkcji klasy jest blok można zdefiniować metody pomocnicze. Blok jest rozdzielone `<#+...#>` i musi ona występować jako ostatniego bloku w pliku.

 Jeśli wolisz nazw klas do zaczynać się wielką literę, można zastąpić ostatniej części szablonu następujący kod szablonu:

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

 Na tym etapie .cs wygenerowanego pliku zawiera następujące deklaracje:

```
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

 Więcej informacji, takich jak właściwości węzły podrzędne, atrybuty i tekst wewnętrzny można dodać przy użyciu tej samej metody.

### <a name="accessing-the-visual-studio-api"></a>Uzyskiwanie dostępu do interfejsu API programu Visual Studio
 Ustawienie `hostspecific` atrybutu `<#@template#>` dyrektywy umożliwia szablonu w celu uzyskania dostępu do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu API. Szablon można umożliwia to uzyskanie lokalizacji plików projektu, aby uniknąć używania bezwzględną ścieżkę do pliku w kodzie szablonu.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="completing-the-text-template"></a>Korzystanie z szablonu tekstowego
 Następująca zawartość szablonu generuje kod, który umożliwia kod testu skompilować i uruchomić.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="running-the-test-program"></a>Uruchomienie programu testu
 W oknie głównym aplikacji konsoli następujące wiersze wykona metody testowej. Naciśnij klawisz F5, aby uruchomić program w trybie debugowania:

```
using System;
namespace MyProject
{ class Program
  { static void Main(string[] args)
    { new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
} } }
```

### <a name="writing-and-updating-the-application"></a>Zapisywanie i aktualizowanie aplikacji
 Teraz można pisać aplikacji w stylu jednoznacznie przy użyciu wygenerowane klasy zamiast ogólnego kod XML.

 Po zmianie schematu XML, łatwo można wygenerować nowe klasy. Kompilator poinformuje dewelopera, gdy musi zostać zaktualizowany kod aplikacji.

 Aby ponownie wygenerować klas, gdy przykładowy plik XML zostanie zmieniony, kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.

## <a name="conclusion"></a>Wniosek
 W tym przewodniku przedstawiono kilka technik i zalet generowania kodu:

-   *Generowanie kodu* utworzenie części kodu źródłowego aplikacji z *modelu*. Model zawiera informacje w formularzu nadaje się do domeny aplikacji i może ulec zmianie w okresie istnienia aplikacji.

-   Silne wpisywanie jest jedną z korzyści płynących generowania kodu. Gdy model reprezentuje informacje w postaci bardziej odpowiednie dla użytkownika, wygenerowany kod umożliwia inne części aplikacji biznesowych w radzeniu sobie z informacjami o przy użyciu zestawu typów.

-   Funkcja IntelliSense i kompilator ułatwiają tworzenie kodu, który jest zgodna ze schematem modelu zarówno podczas pisanie nowego kodu i podczas schemat jest aktualizowany.

-   Dodanie jednego prostotę pliku szablonu do projektu zapewniają następujące korzyści.

-   Szablonu tekstowego można opracowany i przetestowany szybko i przyrostowo.

 W tym przewodniku z wystąpienia modelu reprezentatywny przykład plików XML, których aplikacja będzie przetwarzać faktycznie zostaje wygenerowany kod programu. W bardziej formalnych podejście schemat XML będzie danych wejściowych w szablonie w postaci pliku XSD lub definicji języka specyficznego dla domeny. Takie podejście może ułatwić szablonu, aby określić właściwości, takie jak liczebność relacji.

## <a name="troubleshooting-the-text-template"></a>Rozwiązywanie problemów z szablonu tekstowego
 Jeśli błędy kompilacji lub przekształcania szablonu w już wspomniano **listy błędów**, lub jeśli plik wyjściowy nie został poprawnie wygenerowany, można rozwiązywać problemy szablonu tekstowego z metod opisanych w [Generowanie Pliki za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)