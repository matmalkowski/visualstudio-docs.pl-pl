---
title: Podgląd Pomocy firmy Microsoft zestawu SDK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ddc23ab56df017ef0a37c56cd5b0a81ee33a07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135424"
---
# <a name="microsoft-help-viewer-sdk"></a>Podgląd Pomocy firmy Microsoft SDK
Ten artykuł zawiera następujące zadania integratory Visual Studio Podgląd pomocy:  
  
-   Tworzenie tematu (Obsługa F1)  
  
-   Tworzenie pakietu znakowania zawartość podglądu pomocy  
  
-   Wdrażanie zestaw artykułów  
  
-   Dodawanie pomocy do Visual Studio shell (zintegrowany lub izolowany)  
  
-   Dodatkowe zasoby  
  
### <a name="creating-a-topic-f1-support"></a>Tworzenie tematu (Obsługa F1)  
Ta sekcja zawiera omówienie składników przedstawioną tematu, temacie wymagania, krótki opis jak utworzyć temat (w tym wymagania dotyczące obsługi F1), a na koniec tematu na jej wynik renderowany.  
  
**Omówienie podglądu tematu pomocy**  
  
Wywołanego tematu do renderowania podglądu pomocy pobiera znakowania elementy pakietu, które są skojarzone z tematu w czasie instalacji lub ostatniej aktualizacji, oraz temat XHTML i łączy dwa spowodować przedstawioną widok zawartości (znakowanie danych + dane tematu).  Pakiet znakowania zawiera logo, obsługę zachowania zawartości i tekst znakowania (prawa autorskie, itp.).  Aby uzyskać więcej informacji o znakowaniu elementy pakietu, zobacz "Tworzenie znakowanie pakietu" poniżej.  W przypadku, gdy nie ma żadnych oznaczonego pakietu związanych z tematem, podglądu pomocy będzie używać rezerwowej oznaczonego pakietu znajduje się w katalogu głównym aplikacji Podglądu pomocy (Branding_en US.mshc).  
  
**Wymagania tematu podglądu pomocy**  
  
Do renderowania poprawnie w Podglądzie pomocy, tematu nieprzetworzonej zawartości musi być podstawowy XHTML 1.1 W3C.  
  
Temat zwykle zawiera dwie sekcje:  
  
-   Metadane (zobacz zawartości odwołania metadanych): danych dotyczących tematu, na przykład unikatowy identyfikator tematu, wartość — słowo kluczowe, identyfikator spisu treści tematu nadrzędny identyfikator węzła itp.  
  
-   Zawartość treści: zgodne z podstawowych XHTML 1.1 W3C w tym obsługiwane zachowania zawartości (zwijanej obszaru, fragment kodu itp. Pełna lista jest przedstawiony poniżej).  
  
Pakiet programu Visual Studio znakowania obsługiwane kontrolki:  
  
-   Łącza  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Dziedziczony element członkowski  
  
-   LanguageSpecificText  
  
Obsługiwane ciągi języka (bez rozróżniania wielkości liter):  
  
-   JavaScript  
  
-   CSharp lub c#  
  
-   cplusplus lub visualc ++ lub c ++  
  
-   języka JScript  
  
-   VisualBasic lub vb  
  
-   f # lub języka fsharp lub fs  
  
-   inne - ciąg reprezentujący nazwę języka  
  
**Tworzenie tematu podglądu pomocy**  
  
Utwórz nowy dokument XHTML o nazwie ContosoTopic4.htm i zawierać znacznik tytułu (poniżej).  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
Następnie dodaj dane, aby zdefiniować sposób jak temat jest przedstawiane (self marki lub nie), aby odwołać się w tym temacie F1, w której istnieje w tym temacie w ramach spisu treści, a jego identyfikator (link z odwołaniem w innych tematach), itp.  Poniższa tabela "Zawartości metadanych" Aby uzyskać pełną listę obsługiwanych metadanych.  
  
-   W takim przypadku używamy własnej marki pakietu wariant oznaczonego pakietu Visual Studio podglądu pomocy.  
  
-   Dodaj F1 meta nazwę i wartość ("Microsoft.Help.F1" content = "ContosoTopic4") pasujących zostanie podana wartość F1 w zbiorze właściwości IDE.  (Zobacz sekcji pomocy F1, aby uzyskać więcej informacji.)   Jest to wartość, która jest dopasowywany do F1 wywoływać z w środowisku IDE, aby wyświetlić ten temat, po wybraniu F1 w IDE.  
  
-   Dodaj identyfikator tematu. Jest to ciąg, który jest używany przez inne tematy do odesłania do tego tematu.  Jest to identyfikator podglądu pomocy dla tego tematu.  
  
-   Spisu treści Dodaj węzła nadrzędnego w tym temacie, aby zdefiniować, gdy pojawi się ten węzeł spisu treści tematu.  
  
-   Spisu treści Dodaj kolejności węzła w tym temacie. Jeśli n liczbę węzłów podrzędnych węzła nadrzędnego, zdefiniuj kolejności węzłów podrzędnych lokalizacji w tym temacie. For example, w tym temacie jest numer 4 4 tematy podrzędne.)  
  
Przykład sekcji metadanych:  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
<meta name="SelfBranded" content="false" />     
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
**Treść tematu**  
  
Treść tematu (nie w tym nagłówku i stopce) będzie zawierać łączy strony, sekcję Uwaga zwijanej obszaru, fragment kodu i fragment tekstu określonego języka.  Zobacz sekcję znakowania informacji o tych obszarów przedstawioną tematu.  
  
1.  Dodaj znacznik tytułu tematu:  `<div class="title">Contoso Topic 4</div>`  
  
2.  Dodaj sekcję Uwaga: `<div class="alert"> add your table tag and text </div>`  
  
3.  Dodaj obszar zwijanej:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Dodaj fragment kodu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Dodaj kod języka określonego tekstu: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` należy pamiętać, że devLangnu = pozwala na wprowadzenie innych języków. Na przykład devLangnu = "Fortran" wyświetli Fortran podczas fragment kodu DisplayLanguage = Fortran  
  
6.  Dodawanie łączy strony: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Uwaga: w nieobsługiwanych nowe "język" (na przykład F #, Cobol, Fortran) kolorowania kodu we fragmencie kodu będzie w skali odcieni szarości.  
  
**Temat Podglądu pomocy przykład** kod ilustruje sposób definiowania metadanych, fragment kodu, obszar zwijanej i język określony tekst.  
  
```html
<?xml version="1.0" encoding="utf-8"?>  
<html>  
<head>  
<title>Contoso Topic 4</title>  
  
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />  
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />  
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />  
    <meta name="Language" content="en-us" />  
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />  
<meta name="Microsoft.Help.TocOrder" content="4" />   
<meta name="SelfBranded" content="false" />     
</head>  
  
<body>  
<div class="title">Contoso Topic 4</div>  
  
  <div id="header">  
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">  
        <tr id="headerTableRow2"><td align="left">  
            <span id="nsrTitle">Contoso Topic 1</span>  
          </td>  
<td align="right">  
</td></tr>  
<tr id="headerTableRow1"><td align="left">  
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>  
          </td></tr>  
      </table>  
</div>  
  
<h2>Table of Contents</h2>  
  
<ul class="toc">  
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>  
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>  
</ul>  
  
<div class="topic">  
  
<div id="mainSection">  
<div id="mainBody">  
  
<a name="introduction"></a>  
<h2>1.0 Introduction</h2>  
<p>[This documentation is for sample purposes only.]</p>  
  
<p>Contoso Topic 1 contains examples of:  
<ul>  
<li>Collapsible Area</li>  
<li>Bookmark ("See also")</li>  
<li>Code Snippets from Branding Package</li>  
</ul>  
 </p>  
<div class="alert"><table><tr><th>  
<strong>Note </strong></th></tr>  
<tr><td>  
<p>This is an example of a <span class="label">Note </span>section.    
Call out important items for your reader in this <span class="label">Note </span>box.  
</p></td></tr>  
</table>  
</div>  
</div>  
  
<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">  
  
            <a id="sectionToggle0"><!----></a>  
  
<div>  
Example of Collapsible Area  
<br/>  
Lorem ipsum dolor sit amet...  
</div>  
</CollapsibleArea>  
  
<div id="snippetGroup" >  
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >  
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip  
Dim messageBoxVB as New System.Text.StringBuilder()  
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)  
    messageBoxVB.AppendLine()  
 ...  
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")  
End Sub  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >  
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)   
{   
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();  
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );  
messageBoxCS.AppendLine();  
...  
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );  
}  
</CodeSnippet>  
  
<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >  
some F# code  
</CodeSnippet>  
</div>  
  
<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />  
  
<a name="seealso"></a>  
<h1 class="heading">See Also</h1>  
  
    <div id="seeAlsoSection" class="section">   
    <div class="seeAlsoStyle">  
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>  
    </div>  
 </div>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Obsługa F1**  
  
W programie Visual Studio wybierając F1 generuje wartości dostarczone z umieszczenia kursora w środowisku IDE i wypełnienie klasy "zbiór właściwości" z podanych wartości (oparte na lokalizacji kursora. Gdy kursor znajduje się nad funkcji x, funkcja x jest fokusu/aktywny i wypełnia zbioru właściwości z wartościami.  W przypadku wybrania F1 zbioru właściwości jest wypełniane i wygląda kodu programu Visual Studio F1, jeśli źródło pomocy domyślne klientów znajduje się w lokalnej lub w trybie online (online jest wartość domyślna), następnie tworzy odpowiedni ciąg na podstawie użytkowników ustawienie (online jest ustawieniem domyślnym) — wykonanie powłoki (patrz Pomoc podręczniku administratora dla pliku exe Parametry uruchamiania) wraz z parametrami Podgląd pomocy lokalnej + słowa kluczowe ze zbioru właściwości, jeśli lokalnej pomocy jest wartość domyślna lub adres URL MSDN ze słowem kluczowym na liście parametrów.  
  
Jeśli dla F1 zwracane są trzy ciągi, określone jako ciąg o wielu wartościach, przeprowadzanie pierwszy termin poszukać trafienia, i jeśli znaleziono, możemy są wykonywane; Jeśli nie, aby przejść do następnego ciągu.  Kolejność ma znaczenie. Przedstawienie słowa kluczowe wielowartościowych powinno być najdłuższy ciąg na ciąg najkrótszy.  Aby to sprawdzić, w przypadku wielu wartości słów kluczowych, obejrzyj online ciągu F1 adres URL, który będzie zawierać wybrany — słowo kluczowe.  
  
W programie Visual Studio 2012 celowo wprowadziliśmy silniejszych dzielenia między online i offline, sposób, że jeśli ustawienia użytkownika dla usługi Online, następnie możemy po prostu przekazywane żądania F1 bezpośrednio do naszej usługi online zapytania MSDN, zamiast routingu za pomocą Help Library Agent Aby było w Visual Studio 2010. Następnie możemy polegać na stan "dostawcy zawartość zainstalowaną = true" do ustalenia, czy zrobienia czegoś innego, w tym kontekście. Jeśli PRAWDA, możemy wykonywać tę logikę analizy i routingu w zależności od tego, co chcesz obsługę klientów. W przypadku wartości FAŁSZ następnie możemy po prostu przejdź do MSDN. W przypadku ustawienia użytkownika do lokalnej, następnie wszystkie wywołania po prostu przejdź do aparatu lokalnej pomocy.  
  
F1 Diagram przepływu:  
  
![Przepływ F1](../../extensibility/internals/media/f1flow.png "F1flow")  
  
Jeśli źródło zawartości pomocy domyślne podglądu pomocy jest równa online (uruchamianie w przeglądarce):  
  
-   Visual Studio partnera (VSP) funkcji emisji wartość do zbioru właściwości F1 (prefix.keyword zbioru właściwości i adres URL online dla prefiksu znaleziony w rejestrze): F1 wysyła adres URL pliku VSP + parametrów do przeglądarki.  
  
-   Funkcje programu Visual Studio (Edytor języków, elementy menu określonego programu Visual Studio, itp.): F1 wysyła Visual Studio adres URL do przeglądarki.  
  
Jeśli źródło zawartości pomocy domyślne podglądu pomocy jest równa lokalnej pomocy (Uruchom w Podglądzie pomocy):  
  
-   Funkcje VSP, gdzie — słowo kluczowe jednakowe zbioru właściwości F1 i pod indeksem magazynu lokalnego (to znaczy prefix.keyword zbioru właściwości = wartość znajdującą się w indeksie magazynu lokalnego): F1 renderuje tematu w Podglądzie pomocy.  
  
-   Funkcje programu Visual Studio (opcja VSP do przesłonięcia zbioru właściwości emitowanych przez funkcje programu Visual Studio): F1 renderuje tematu w Podglądzie Pomocy programu Visual Studio.  
  
Ustaw następujące wartości rejestru, aby włączyć powrotu F1 dla dostawcy zawartości pomocy. F1 powrotu oznacza, że podglądu pomocy ma wartość do wyszukania zawartości pomocy F1 online, a zawartość dostawca jest instalowany lokalnie na dysku twardym użytkowników. Podgląd pomocy powinna wyglądać w lokalnej pomocy dla zawartości, nawet jeśli jest ustawieniem domyślnym dla pomocy online.  
  
1.  Ustaw **VendorContent** w kluczu rejestru 2.3 pomocy:  
  
    -   Dla 32-bitowych systemach operacyjnych:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = dword: 00000001  
  
    -   Dla 64-bitowych systemach operacyjnych:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = dword: 00000001  
  
2.  Rejestracja przestrzeni nazw partnera w kluczu rejestru 2.3 pomocy:  
  
    -   Dla 32-bitowych systemach operacyjnych:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< przestrzeń nazw\>*  
  
         "Lokalizacja"="offline"  
  
    -   Dla 64-bitowych systemach operacyjnych:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< przestrzeń nazw\>*  
  
         "Lokalizacja"="offline"  
  
**Podstawowa analiza kodu natywnego Namespace**  
  
Aby włączyć funkcję analizy podstawowej natywnego przestrzeni nazw, w rejestrze Dodaj nową wartość typu DWORD o nazwie: BaseNativeNamespaces i ustaw dla niego wartość 1 (w kluczu katalogu, które chce obsługiwać).  Na przykład jeśli chcesz używać katalogu programu Visual Studio, można dodać klucza do ścieżki:  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
Gdy F1 — słowo kluczowe w formacie, który napotkano nagłówek/metody, znak '/' będzie analizowany, co powoduje Poniższa konstrukcja:  
  
-   Nagłówek: będzie przestrzeni nazw, który może służyć do rejestrowania w rejestrze  
  
-   Metoda: będzie — słowo kluczowe, które jest przekazywane za pośrednictwem.  
  
Na przykład, biorąc pod uwagę niestandardowa biblioteka o nazwie CustomLibrary i metody o nazwie MyTestMethod, gdy F1 żądanie pochodzi w niej będą formatowane jako `CustomLibrary/MyTestMethod`.  
  
Użytkownik może następnie zarejestrować CustomLibrary jako przestrzeń nazw w gałęzi partnerów i podaj niezależnie od lokalizacji klucz chcą i słowo kluczowe przekazany do zapytania będzie MyTestMethod.  
  
**Włącz Pomoc narzędzia w IDE debugowania**  
  
Dodaj następujący klucz rejestru i wartości:  
  
Klawisz Pomocy HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic: dane wyjściowe debugowania wyświetlaną w wartości handlowej: tak  
  
W środowisku IDE, w menu Pomoc wybierz "Debugowanie pomóc w kontekście"  
  
**Metadane zawartości**  
  
W poniższej tabeli dowolny ciąg wyświetlany w nawiasach kwadratowych jest symbol zastępczy, które muszą zostać zastąpione rozpoznawaną wartością. Na przykład w \<meta name="Microsoft.Help.Locale" zawartość = "[kod języka]" / >, "[kod języka]" musi zostać zastąpiona wartością takich jak "en-us".  
  
|Właściwość (reprezentacja HTML)|Opis|  
|--------------------------------------|-----------------|  
|\< meta name="Microsoft.Help.Locale" content = "[kod języka]" / >|Określa ustawienia regionalne dla tego tematu. Jeśli ten tag jest używany w temacie, musi być użyte tylko raz i muszą być wstawiane powyżej innych tagów Microsoft Help. Jeśli ten tag nie jest używany, treść tego tematu jest indeksowana przy użyciu wyrazów, które jest skojarzone z ustawieniami regionalnymi produktu, jeśli jest określona; w przeciwnym razie wartość en-us dzielenie wyrazów jest używany. Ten tag jest zgodna z ISOC RFC 4646. Aby upewnić się, że Microsoft Help działa prawidłowo, należy użyć tej właściwości zamiast ogólne atrybut Language.|  
|\< meta name="Microsoft.Help.TopicLocale" content = "[kod języka]" / >|Ustawia ustawień regionalnych dla tego tematu, gdy są używane również innych ustawień regionalnych. Jeśli ten tag jest używany w temacie, musi można użyć tylko raz. Za pomocą tego tagu katalogu z zawartością w więcej niż jednym języku. Wiele tematów w katalogu mogą mieć ten sam identyfikator, ale każda należy określić unikatowy TopicLocale. Temat, który określa TopicLocale, zgodnym z ustawieniami regionalnymi wykazu jest temat, który jest wyświetlany w spisie treści. Jednak wszystkich wersji językowych tematu są wyświetlane w wynikach wyszukiwania.|  
|\< tytuł > [nazwa] \< /title >|Określa tytuł w tym temacie. Ten tag jest wymagana i musi być używany tylko raz w temacie. Jeśli treść tego tematu nie zawiera tytuł \<div > sekcji, ten tytuł jest wyświetlany w temacie i w spisie treści.|  
|\< meta name = "Microsoft.Help.Keywords" content = "[aKeywordPhrase]" / >|Określa tekst łącza wyświetlany w okienku podglądu pomocy indeksu. Po kliknięciu łącza po wyświetleniu. Można określić wiele indeksu słów kluczowych dla tematu lub znacznik można pominąć, jeśli nie chcesz, aby łącza do tego tematu, aby występuje w indeksie. Słowa kluczowe "K" z wcześniejszych wersji Pomocy może zostać przekonwertowany do tej właściwości.|  
|\< meta name="Microsoft.Help.Id" content = "[TopicID]" / >|Ustawia identyfikator dla tego tematu. Ten tag jest wymagana i musi być używany tylko raz w temacie. Identyfikator musi być unikatowa wśród tematów w katalogu, które mają takie same ustawienia regionalne. W innym temacie możesz utworzyć łącza do tego tematu, za pomocą tego identyfikatora.|  
|\< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Słowo kluczowe F1 dla tego tematu. Można określić wiele kluczowych F1 dla tematu lub znacznik można pominąć, jeśli nie chcesz tego tematu, aby być wyświetlane, gdy użytkownik aplikacji naciśnie klawisz F1. Zazwyczaj dla tematu został określony tylko jeden słów kluczowych F1. Słowa kluczowe "F" z wcześniejszych wersji Pomocy może zostać przekonwertowany do tej właściwości.|  
|\< meta name = "Opis" content = "[opis tematu]" / >|Zawiera krótkie podsumowanie zawartości w tym temacie. Jeśli ten tag jest używany w temacie, musi można użyć tylko raz. Ta właściwość jest dostępny bezpośrednio przez bibliotekę zapytania; nie są przechowywane w pliku indeksu.|  
 meta name="Microsoft.Help.TocParent" content = "[parent_Id]" / >|Określa temat nadrzędny tego tematu w spisie treści. Ten tag jest wymagana i musi być używany tylko raz w temacie. Wartość jest Microsoft.Help.Id elementu nadrzędnego. Temat może mieć tylko jedną lokalizację w tabeli treści. -"1" jest traktowany jako identyfikator tematu dla elementu głównego spisu treści. W [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], że strona jest stroną główną podglądu pomocy. Jest to z tego samego powodu się, że niektóre tematy, aby upewnić się, że ich wyświetlana u góry poziomu specjalnie wdrażaniu TocParent =-1. Strona główna podglądu pomocy jest strona systemu i dlatego niewymienne. Jeśli VSP próbuje dodać stronę o identyfikatorze -1, może zostaną dodane do zestawu zawartości, ale podglądu pomocy będzie zawsze używać stronie systemu — strona główna podglądu pomocy|  
|\< meta name="Microsoft.Help.TocOrder" content = "[dodatnią liczbą całkowitą]" / >|Określa, gdzie w spisie treści ten temat znajduje się względem jego elementów równorzędnych tematów. Ten tag jest wymagana i musi być używany tylko raz w temacie. Wartość jest liczbą całkowitą. Temat, który określa całkowitą wartość dolna pojawia się powyżej temat, który określa całkowitą wyższa wartość.|  
|\< meta name="Microsoft.Help.Product" content = "[kod produktu]" / >|Określa, w tym temacie opisano produktu. Jeśli ten tag jest używany w temacie, musi można użyć tylko raz. Te informacje mogą być także podane jako parametr przekazywany do indeksatora pomocy.|  
|\< meta name="Microsoft.Help.ProductVersion" content = "[numer wersji]" / >|Określa wersję produktu, który opisano w tym temacie. Jeśli ten tag jest używany w temacie, musi można użyć tylko raz. Te informacje mogą być także podane jako parametr przekazywany do indeksatora pomocy.|  
|\< meta name="Microsoft.Help.Category" content = "[parametry]" / >|Używany przez produktów do identyfikowania podpunkty zawartości. Można określić wiele podpunkty dla tematu lub znacznik można pominąć, jeśli nie chcesz, aby łącza, aby zidentyfikować wszelkie podsekcje. Ten tag jest używany do przechowywania atrybutów TargetOS i TargetFrameworkMoniker po przekonwertowaniu tematu z wcześniejszej wersji Pomocy. Format zawartości jest AttributeName:AttributeValue.|  
|\< zawartość name="Microsoft.Help.TopicVersion meta ="[temat numer wersji]"/ >|Określa tą wersją tego tematu, gdy istnieje wiele wersji w katalogu. Ponieważ Microsoft.Help.Id nie musi być unikatowa, ten tag jest wymagany w przypadku więcej niż jedną wersję tematu istnieje w katalogu, na przykład, gdy katalog zawiera temat dla programu .NET Framework 3.5 i temat dla programu .NET Framework 4 i mają tego samego Micro elastyczne. Help.Id.|  
|\< meta name = "SelfBranded" content = "[wartość PRAWDA lub FAŁSZ]" / >|Określa, czy w tym temacie używa pakietu znakowania uruchamiania Pomoc Menedżera biblioteki lub znakowania pakietu, który jest przeznaczony dla tematu. Ten tag musi mieć wartość PRAWDA lub FAŁSZ. Jeśli wartość TRUE, a następnie znakowania pakiet dla skojarzonego tematu zastępuje znakowania pakiet, który jest ustawiona, gdy Pomoc Menedżera biblioteki, uruchamia tematu jest renderowany zgodnie z założeniami, nawet jeśli różni się od renderowania zawartości innego. Jeśli ma ona wartość FALSE, bieżący temat jest renderowany zgodnie z znakowania pakiet, który jest ustawiona, gdy rozpoczyna się Pomoc Menedżera biblioteki. Domyślnie zakłada własnym znakowania, aby mieć wartość false, chyba że zmiennej SelfBranded jest zadeklarowany jako TRUE; Help Library Manager w związku z tym nie trzeba zadeklarować \<meta name = "SelfBranded" content = "FALSE" / >.|  
  
### <a name="creating-a-branding-package"></a>Tworzenie pakietu znakowania  
Wersję programu Visual Studio obejmuje szereg różnych produktów Visual Studio, w tym izolowany i zintegrowane powłok dla partnerów usługi Visual Studio.  Każdy z tych produktów wymaga pewnym stopniu oparte na temat zawartości pomocy znakowania pomocy technicznej, unikatowe dla produktu.  Na przykład tematów Visual Studio musi być prezentację spójne marki SQL Studio, który opakowuje powłoki ISO, wymaga własny unikatowy pomocy zawartości znakowanie dla każdego tematu.  Zintegrowane partnera powłoki może być ich tematy pomocy, aby być nadrzędnym zawartości pomocy produktu Visual Studio przy zachowaniu ich własnych znakowania tematu.  
  
Znakowania pakietów zainstalowanych w ramach produktu zawierający podglądu pomocy.  Dla produktów programu Visual Studio:  
  
-   Rezerwowy oznaczonego pakietu (Branding_\<ustawień regionalnych > .mshc) jest instalowany w katalogu głównym aplikacji 2.3 podglądu pomocy (przykład: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) przez pakiet językowy podglądu pomocy.  Służy on do przypadków, w których nie zainstalowano produktu znakowanie pakietu (został zainstalowany bez zawartości) lub gdy zainstalowanego pakietu znakowania jest uszkodzony.  Należy pamiętać, że elementów programu Visual Studio (logo i opinie) są ignorowane, podczas powrotu katalogu głównego aplikacji znakowanie pakietu jest używany.  
  
-   Po zainstalowaniu programu Visual Studio zawartości z pakietu zawartości usługi oznaczonego pakietu jest również instalowany (dla pierwszego scenariusza instalacji zawartości czasu).  W przypadku aktualizacji pakietu znakowania, aktualizacja jest zainstalowana w następnej aktualizacji zawartości lub akcji instalacji pakietu dodatkowe sytuacji.  
  
Podgląd Pomocy firmy Microsoft obsługuje znakowania tematy na podstawie metadanych tematu.  
  
-   Gdzie metadanych tematu definiuje self marki = true, renderowania tematu jest, nic nie rób (jak znakowanie).  
  
-   Gdzie metadanych tematu definiuje self marki = false, za pomocą znakowania pakietu skojarzone z wartością metadanych TopicVendor.  
  
-   Gdzie metadanych tematu definiuje name="Microsoft.Help.TopicVendor" zawartość =\< znakowania nazwy pakietu w dostawcy MSHA >, za pomocą znakowania pakietu zdefiniowane w wartość zawartości.  
  
-   Należy pamiętać, że w ramach katalogu programu Visual Studio priorytetu stosowania znakowania pakietów.  Stosowany jest pierwszy znakowania domyślnej programu Visual Studio, a następnie zdefiniowane w metadanych tematu i obsługiwane przez skojarzony znakowanie pakietu (zgodnie z definicją w msha instalacji), zdefiniowane przez dostawcę znakowania jest stosowany jako przesłonięcie.  
  
Elementy znakowania zazwyczaj dzielą się na trzy główne kategorie:  
  
-   Elementy nagłówka (przykłady link opinii, tekst warunkowego zastrzeżenie, logo)  
  
-   Zawartość zachowania (przykłady obejmują elementy tekstu formantu Rozwiń/Zwiń i elementy fragment kodu)  
  
-   Elementy stopki (przykład praw autorskich)  
  
Elementy uznawany za elementy marką obejmują (szczegóły dostępne w tej specyfikacji):  
  
-   Logo katalogu produktu (na przykład Visual Studio)  
  
-   Elementy link i wiadomości e-mail opinii  
  
-   Tekst klauzuli wyłączenia odpowiedzialności  
  
-   Tekst praw autorskich  
  
Pliki obsługi w pakiecie znakowania programu Visual Studio podglądu pomocy obejmują:  
  
-   Grafika (logo, ikony itp.)  
  
-   Branding.js - skryptu pliki pomocnicze zachowania zawartości  
  
-   Branding.XML - ciągów, które są zawsze używane w zawartości katalogu.  Uwaga: elementy tekstu lokalizacji programu Visual Studio w branding.xml, to _locID = "\<unikatową wartość >"  
  
-   Branding.css - definicji stylów spójności prezentacji  
  
-   Printing.css - definicji stylów dla spójne drukowania prezentacji  
  
Jak wspomniano powyżej, znakowanie pakiety są skojarzone z tematu:  
  
-   Gdy SelfBranded = false jest zdefiniowany w metadanych, temat dziedziczy katalogu znakowanie pakietu  
  
-   Lub jeśli SelfBranded = false i jest unikatowy pakiet znakowania zdefiniowany w MSHA i jest dostępny, gdy zawartość jest zainstalowany  
  
Dla VSPs Implementowanie niestandardowych pakietów znakowania (VSP zawartości, SelfBranded = True), jest jednym ze sposobów kontynuować do uruchamiania z pakietem znakowania rezerwowy (zainstalowaną z podglądu pomocy) i Zmień nazwę pliku, zależnie od potrzeb.  Branding_\<ustawień regionalnych > plik .mshc jest plik zip z rozszerzeniem pliku zmieniony na .mshc, więc po prostu Zmień rozszerzenie z .mshc na zip i Wyodrębnij zawartość.  Poniżej zamieszczono znakowanie elementów pakietu i zmodyfikuj odpowiednio (na przykład zmienić logo VSP logo i odwołanie do logo w pliku Branding.xml, zaktualizuj Branding.xml na charakterystykę VSP itp.).  
  
Gdy wszystkie modyfikacje są gotowe, Utwórz plik zip zawierający żądaną znakowania elementów i zmień rozszerzenie dyskretnej.  
  
Aby skojarzyć niestandardowe oznaczonego pakietu, należy utworzyć MSHA, który zawiera odwołanie do znakowania plików mshc wraz z mshc zawartości (tematy zawierające).  Wymienione poniżej "MSHA" sposób tworzenia podstawowych MSHA.  
  
Plik Branding.xml zawiera elementy listy, używany do renderowania elementów określonych w temacie spójnie, gdy zawiera temat \<meta name="Microsoft.Help.SelfBranded" content = "false" / >.  Poniżej przedstawiono listę elementów w pliku Branding.xml programu Visual Studio.  Należy pamiętać, że ta lista jest przeznaczona do użycia jako szablon dla entuzjastów powłoki ISO, gdzie modyfikują tych elementów (na przykład logo, opinie i prawach autorskich) na ich własnych produktu znakowania musi spełniać.  
  
Uwaga: zmienne zauważyć przez "{n}" ma zależności w kodzie — usuwanie lub zmiana tych wartości spowoduje, że błędów i awarii aplikacji. Identyfikatory lokalizacji (przykład _locID="codesnippet.n") są uwzględniane w pakiet programu Visual Studio znakowania.  
  
**Branding.XML**  
  
|||  
|-|-|  
|Funkcja:|**CollapsibleArea**|  
|Za pomocą:|Rozwiń węzeł Zwija tekst formantu zawartości|  
|**Element**|**Wartość**|  
|ExpandText|Rozwiń węzeł|  
|CollapseText|Zwiń|  
|Funkcja:|**CodeSnippet**|  
|Za pomocą:|Tekst formantu fragment kodu.  Uwaga: Zawartość fragment kodu z miejsca "Non-podziału" zostanie zmieniony na miejsce.|  
|**Element**|**Wartość**|  
|CopyToClipboard|Kopiuj do schowka|  
|ViewColorizedText|Pokolorowane widoku|  
|CombinedVBTabDisplayLanguage|Visual Basic (przykład)|  
|VBDeclaration|Deklaracja|  
|VBUsage|Użycie|  
|Funkcja:|**Opinie, stopka i Logo**|  
|Za pomocą:|Podaj formantu opinii dla klienta przekazać opinię na temat bieżącego za pośrednictwem poczty e-mail.  Tekst praw autorskich dla zawartości.  Definicja logo.|  
|**Element**|**Wartość (te ciągi można zmodyfikować, aby sprostać wymaganiom adopter zawartości.)**|  
|Prawa autorskie|© 2013 Microsoft Corporation. Wszelkie prawa zastrzeżone.|  
|SendFeedback|\<href = "{0}" {1} > Prześlij opinię\</a > na ten temat do firmy Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.GIF|  
|LogoFileNameHC|vs_logo_wh.GIF|  
|Funkcja:|**Zrzeczenie odpowiedzialności**|  
|Za pomocą:|Zestaw przypadków zastrzeżenia określonej dla maszyny translacji zawartości.|  
|**Element**|**Wartość**|  
|MT_Editable|Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie internetowe, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem oryginalnej zawartości w języku angielskim jednocześnie.|  
|MT_NonEditable|Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie internetowe, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem oryginalnej zawartości w języku angielskim jednocześnie.|  
|MT_QualityEditable|Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie internetowe, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem oryginalnej zawartości w języku angielskim jednocześnie.|  
|MT_QualityNonEditable|Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie internetowe, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem oryginalnej zawartości w języku angielskim jednocześnie.|  
|MT_BetaContents|Ten artykuł został przetłumaczony maszynowo dla wydania wstępnego. Jeśli masz połączenie internetowe, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem oryginalnej zawartości w języku angielskim jednocześnie.|  
|MT_BetaRecycledContents|Ten artykuł został przetłumaczony ręcznie dla wydania wstępnego. Jeśli masz połączenie internetowe, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem oryginalnej zawartości w języku angielskim jednocześnie.|  
|Funkcja:|**Połączonej**|  
|Za pomocą:|Obsługa łącza w temacie online|  
|**Element**|**Wartość**|  
|LinkTableTitle|Łącze tabeli|  
|TopicEnuLinkText|Pokaż angielską wersję\</a > w tym temacie, który jest dostępny na tym komputerze.|  
|TopicOnlineLinkText|Wyświetl ten temat \<href = "{0}" {1} > online\</a >|  
|OnlineText|online|  
|Funkcja:|**Formant Audio wideo**|  
|Za pomocą:|Wyświetlanie elementów i tekst dla zawartości wideo|  
|**Element**|**Wartość**|  
|MultiMediaNotSupported|Do obsługi zawartości {0} musi być zainstalowany program Internet Explorer 9 lub nowsza.|  
|VideoText|Wyświetlanie wideo|  
|Audiotekst|przesyłanie strumieniowe audio|  
|OnlineVideoLinkText|\<p > Aby wyświetlić wideo, związane z tym tematem, kliknij {0}\<href = "\ {1\}" > {2}here\</a >.\< /p >|  
|OnlineAudioLinkText|\<p > Aby wysłuchać nagrań audio, związanych z tym tematem, kliknij {0}\<href = "\ {1\}" > {2}here\</a >.\< /p >|  
|Funkcja:|**Formant zawartości nie jest zainstalowany**|  
|Za pomocą:|Tekst elementów (ciągi) używany do renderowania contentnotinstalled.htm|  
|**Element**|**Wartość**|  
|ContentNotInstalledTitle|Nie znaleziono zawartości na komputerze.|  
|ContentNotInstalledDownloadContentText|\<p > Aby pobrać zawartość do komputera, \<href = "{0}" {1} > klikając kartę Zarządzaj\</a >.\< /p >|  
|ContentNotInstalledText|\<p > Brak zainstalowanej zawartości na komputerze. Zobacz instalacji lokalnej zawartości Pomocy można uzyskać od administratora. \</p >|  
|Funkcja:|**Formant nie znaleziono tematu**|  
|Za pomocą:|Tekst elementów (ciągi) używany do renderowania topicnotfound.htm|  
|**Element**|**Wartość**|  
|TopicNotFoundTitle|Nie można odnaleźć żądanego tematu na komputerze.|  
|TopicNotFoundViewOnlineText|\<p > nie można odnaleźć żądanego tematu na komputerze, ale można \<href = "{0}" {1} > przeglądać temat online\</a >.\< /p >|  
|TopicNotFoundDownloadContentText|\<p > można znaleźć w okienku nawigacji odnośniki do podobnych tematów lub \<href = "{0}" {1} > klikając kartę Zarządzaj\</a > Aby pobrać zawartość do komputera.\< /p >|  
|TopicNotFoundText|\<p > nie można odnaleźć żądanego tematu na komputerze. \</p >|  
|Funkcja:|**Temat uszkodzony formantu**|  
|Za pomocą:|Tekst elementów (ciągi) używany do renderowania topiccorrupted.htm|  
|**Element**|**Wartość**|  
|TopicCorruptedTitle|Nie można wyświetlić żądanego tematu.|  
|TopicCorruptedViewOnlineText|\<p > Podgląd pomocy nie może wyświetlić żądanego tematu. Może to być błąd w zawartości tematu lub podstawowej zależności systemu. \</p >|  
|Funkcja:|**Formant strony głównej**|  
|Za pomocą:|Tekst obsługi wyświetlanie zawartości węzeł najwyższego poziomu podglądu pomocy.|  
|**Element**|**Wartość**|  
|HomePageTitle|Strona główna podglądu pomocy|  
|HomePageIntroduction|\<p > Witamy podglądu pomocy firmy Microsoft, zasadniczym źródłem informacji dla każdego użytkownika, który korzysta z narzędzi, produktów, technologii i usług firmy Microsoft. Podgląd Pomocy umożliwia dostęp do instrukcje i dokumentację, przykładowego kodu, artykułów technicznych i. Aby znaleźć zawartość potrzebujesz, przejrzyj spis treści, użyj wyszukiwania pełnotekstowego lub poruszanie się po zawartości przy użyciu indeksu słów kluczowych. \</p >|  
|HomePageContentInstallText|\<p >\<br / > Użyj \<href = "{0}" {1} > Zarządzaj zawartością\</a > kartę, aby wykonać następujące czynności:\<ul >\<li > dodać zawartość do komputera.\< /li >\<li > sprawdzić aktualizacje zawartości w sieci lokalnej.\< /li >\<li > usunąć zawartość z komputera.\< /li >\</ul >\</p >|  
|HomePageInstalledBooks|Zainstalowanych książek|  
|HomePageNoBooksInstalled|Nie znaleziono zawartości na komputerze.|  
|HomePageHelpSettings|Ustawienia zawartości pomocy|  
|HomePageHelpSettingsText|\<p > bieżące ustawienia jest lokalnej pomocy. Podgląd Pomocy wyświetla zawartość zainstalowaną na tym komputerze. \<br / > Aby zmienić źródło zawartości pomocy na pasku menu programu Visual Studio wybierz \<span style = "{0}" > Pomoc, ustaw preferencje pomocy\</span >.\< br / >\</p >|  
|Megabajtów|MB|  
  
**Branding.js**  
  
Plik branding.js zawiera JavaScript używane przez elementy znakowania programu Visual Studio podglądu pomocy.  Poniżej znajduje się lista elementów znakowania i obsługi funkcji JavaScript.  Wszystkie parametry do lokalizacji dla tego pliku są zdefiniowane w sekcji "Lokalizowalny ciągi" u góry tego pliku.  Należy pamiętać, że utworzono plik ICL loc ciągów w pliku branding.js.  
  
||||  
|-|-|-|  
|**Funkcja znakowania**|**Funkcja JavaScript**|**Opis**|  
|Var...||Zdefiniuj zmienne|  
|Pobierz język kodu użytkownika|setUserPreferenceLang|mapuje indeksu # na język kodu|  
|Ustawianie i pobieranie wartości plików cookie|getCookie, setCookie||  
|Dziedziczony element członkowski|changeMembersLabel|Rozwijanie/zwijanie dziedziczonego elementu członkowskiego|  
|Gdy SelfBranded = False|onLoad|Ciąg zapytania, aby sprawdzić, czy żądania wydruku jest do odczytu.  Ustaw wszystkie codesnippets aby skoncentrować się na karcie preferowanych użytkownika.  Jeśli jest drukowania żądania isPrinterFriendly następnie ustaw wartość true. Sprawdź, czy trybie dużego kontrastu.|  
|Fragment kodu|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|Zapisz wszystkie obiekt formantu zwijany do listy.|  
||CA_Click|na podstawie stanu zwijanej obszaru, definiuje, które obraz i tekst do prezentowania|  
|Obsługa kontrastu Logo|isBlackBackground()|Wywołuje się, by określić, czy tło jest czarny.  Tylko dokładne podczas w trybie dużego kontrastu.|  
||isHighContrast()|Użyj kolorowe zakres, aby wykryć trybie dużego kontrastu|  
||onHighContrast(black)|Wywołuje się po wykryciu duży kontrast|  
|Funkcje LST|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|Funkcje multimedialne|podpis (koniec tekstu, styl rozpoczęcia)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||styleRectify (styleName, styleValue)||  
||showCC(id)||  
||subtitle(ID)||  
  
**PLIKI HTML**  
  
Pakiet znakowania zawiera zestaw plików HTM, które obsługują scenariusze do przekazywania informacji klucza użytkowników zawartości pomocy, na przykład stronę główną, zawierający sekcji opisujące, który określa zawartości są zainstalowane i stron informujący użytkownika, gdy tematy nie można znaleźć w lokalnym zestaw tematów. Należy pamiętać, że te pliki HTM można modyfikować dla każdego produktu.  Dostawców ISO powłoki są może potrwać do domyślnego pakietu znakowania i zmianę zachowania i zawartości tych stron do zestawu ich potrzeb.  Te pliki odwoływać się do ich odpowiednich znakowania pakietów w kolejności znakowania tagów uzyskać odpowiednią zawartość z pliku branding.xml.  
  
||||  
|-|-|-|  
|**Plik**|**Użyj**|**Wyświetlane źródła zawartości**|  
|Strona_główna.htm|Jest to strona, wyświetlająca zawartość aktualnie zainstalowany i inne wiadomości należy użytkownikowi o ich zawartości.  Ten plik zawiera dodatkową zawartość "Microsoft.Help.Id" atrybutu meta danych =-"1", który umieszcza to zawartości w górnej części lokalnej zawartości spisu treści.||  
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.XML, tag \<HomePageTitle >|  
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.XML, tag \<HomePageIntroduction >|  
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.XML, tag \<HomePageContentInstallText >|  
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Nagłówek sekcji Branding.xml tag\<HomePageInstalledBooks >, danych wygenerowanych z aplikacji, \<HomePageNoBooksInstalled > Jeśli książek nie są zainstalowane.|  
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Nagłówek sekcji Branding.xml tag \<HomePageHelpSettings >, sekcja tekst \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Temat istnieje w zestawie lokalnym, ale dla jakiegoś powodu nie można wyświetlić (uszkodzony zawartości).||  
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, tag \<TopicCorruptedTitle >|  
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.XML, tag \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Jeśli temat nie został znaleziony w zawartości lokalnej ustawione ani dostępna online||  
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.XML, tag \<TopicNotFoundTitle >|  
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.XML, tag \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, tag \<TopicNotFoundText >|  
|contentnotinstalled.htm|Gdy brak zawartości lokalnej zainstalowany dla produktu.||  
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.XML, tag \<ContentNotInstalledTitle >|  
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.XML, tag \<ContentNotInstalledDownloadContentText >|  
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.XML, tag \<ContentNotInstalledText >|  
  
**Pliki CSS**  
  
Pakiet programu Visual Studio pomocy podglądu znakowania zawiera dwa pliki css do obsługi spójne prezentacji zawartości Pomocy programu Visual Studio:  
  
-   Branding.css — zawiera elementy css do renderowania where SelfBranded = false  
  
-   Printer.css — zawiera elementy css do renderowania where SelfBranded = false  
  
Pliki Branding.css zawiera definicje dla programu Visual Studio tematu prezentacji (zastrzeżenie: jest to, że branding.css zawartych w Branding_\<ustawień regionalnych > .mshc z usługi pakietu może zmienić).  
  
**Pliki graficzne**  
  
Visual Studio zawartości Wyświetla logo programu Visual Studio, a także inne grafiki.  Poniżej przedstawiono pełną listę plików graficznych w pakiecie znakowania programu Visual Studio podglądu pomocy.  
  
||||  
|-|-|-|  
|**Plik**|**Użyj**|**Przykłady**|  
|Clear.GIF|Używany do renderowania obszaru zwijanej||  
|footer_slice.GIF|Stopka prezentacji||  
|info_icon.GIF|Używany podczas wyświetlania informacji|Zrzeczenie odpowiedzialności|  
|online_icon.GIF|Ta ikona jest skojarzona z łącza online||  
|tabLeftBD.gif|Używany do renderowania kontenera wstawek kodu||  
|tabRightBD.gif|Używany do renderowania kontenera wstawek kodu||  
|vs_logo_bk.GIF|Używany do normalnej kontrastu logo odwołań, zgodnie z definicją w tagu Branding.xml \<LogoFileName >.  Dla produktów programu Visual Studio Nazwa logo jest vs_logo_bk.gif.||  
|vs_logo_wh.GIF|Używany do normalnej logo wysokiej odwołania zgodnie z definicją w tagu Branding.xml \<LogoFileNameHC >.  Dla produktów programu Visual Studio Nazwa logo jest vs_logo_wh.gif.||  
|ccOff.png|Podpisy grafiki||  
|ccOn.png|Podpisy grafiki||  
|ImageSprite.png|Używany do renderowania obszaru zwijanej|rozwinięte lub zwinąć grafiki|  
  
### <a name="deploying-a-set-of-topics"></a>Wdrażanie zestaw tematów  
Jest to bardzo proste i szybkie samouczek tworzenia rozmieszczania zawartości podglądu pomocy, ustaw comprised pliku MSHA i zestaw plików cab lub MSHC zawierającego tematów. MSHA jest plik XML, który opisuje zestaw plików cab lub MSHC plików. Podgląd pomocy może odczytywać MSHA, aby uzyskać listę zawartości (. Plik CAB lub. Pliki MSHC) dostępny do instalacji lokalnej.  
  
Jest to tylko Elementarz opisujące bardzo podstawowe schematu XML dla MSHA podglądu pomocy.  Należy pamiętać, że jest przykładem implementacji poniżej tego krótkie omówienie i przykładowe HelpContentSetup.msha.  
  
Nazwa MSHA, na potrzeby tego Elementarz jest HelpContentSetup.msha (nazwa pliku może być dowolna, o rozszerzeniu. MSHA). HelpContentSetup.msha (przykładu) powinien zawierać listę plików cab lub MSHCs dostępne.  Należy pamiętać, że typ pliku musi być zgodne w obrębie MSHA (nie obsługuje kombinację typów plików MSHA i CAB). Dla każdego pliku CAB lub MSHC powinien istnieć \<klasy div = "pakietu" >...  \< /div > (zobacz poniższy przykład).  
  
Uwaga: w poniższym przykładzie implementacji Przedstawiliśmy oznaczonego pakietu. Jest to szczególnie ważne, aby uwzględnić Aby uzyskać wymagane elementy renderowania zawartości programu Visual Studio i zachowania zawartości.  
  
Przykładowy plik HelpContentSetup.msha: (Zastąp "zawartości Ustaw nazwę 1" i "zawartości, nazwa zestawu 2" itp. z nazwy pliku.)  
  
```html
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>.  
  
```  
  
1.  Utwórz folder lokalny coś, takie jak "C:\SampleContent"  
  
2.  W tym przykładzie używamy MSHC pliki zawierają tematy.  MSHC jest zip z rozszerzeniem pliku zmieniła się z rozszerzeniem .zip do. MSHC.  
  
3.  Utwórz poniżej HelpContentSetup.msha jako plik tekstowy (Notatnik został użyty do utworzenia pliku) i zapisz go w folderze dostrzeżone powyżej (zobacz krok 1).  
  
Należy pamiętać, że klasa "Branding" istnieje i jest unikatowa. Branding mshc znajduje się w tym Elementarz tak, aby zainstalowaną zawartość będzie miał znakowania i zachowania zawartości, które są zawarte w MSHCs będzie mieć odpowiednią obsługę zawartym w pakiecie znakowania. W przeciwnym razie błędy spowoduje, że gdy system wyszukuje elementy pomocy technicznej, które nie są częścią zgranych (zainstalować) zawartości.  
  
Uzyskanie programu Visual Studio znakowanie pakietu, należy skopiować Branding_en US.mshc pliku w lokalizacji C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ do folderu roboczego.  
  
```html  
<html>  
<head />  
<body class="vendor-book">  
<div class="details">  
<span class="vendor">Your Company</span>  
<span class="locale">en-us</span>  
<span class="product">Your Company Help Content</span>  
<span class="name">Your Company Help Content</span>  
</div>  
<div class="package-list">  
<div class="package">  
<span class="name">Your_Company _Content_Set_1</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>  
</div>  
<div class="package">  
<span class="name">Your_Company _Content_Set_2</span>  
<span class="deployed">True</span>  
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>  
</div>  
<div class="package">  
<span class="packageType">branding</span>  
<span class="name">Branding_en-US</span>  
<span class="deployed">True</span>  
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>  
</div>  
</div>  
</body>  
</html>  
  
```  
  
**Podsumowanie**  
  
Przy użyciu i rozszerzanie powyższych kroków spowoduje włączenie VSPs wdrażania ich zawartości zestawy dla Visual Studio podglądu pomocy.  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Dodawanie pomocy do programu Visual Studio Shell (zintegrowany i izolowany)  
**Wprowadzenie**  
  
W tym przewodniku pokazano, jak dołączyć zawartości pomocy do aplikacji Visual Studio Shell, a następnie wdrożyć go.  
  
**Wymagania**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 izolowane powłoki Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**Omówienie**  
  
[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Powłoki to wersja [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE, na którym można oprzeć aplikacji. Takie aplikacje zawierają Isolated Shell wraz z rozszerzeń, które można utworzyć. Za pomocą szablonów projektu Isolated Shell, które są zawarte w [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] zestawu SDK do tworzenia rozszerzeń.  
  
Podstawowe kroki tworzenia aplikacji opartych na Isolated Shell i jego pomocy:  
  
1.  Uzyskaj [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO powłoki pakietu redystrybucyjnego (pobierania firmy Microsoft).  
  
2.  W programie Visual Studio Utwórz rozszerzenia pomocy, na podstawie Isolated Shell, na przykład, rozszerzenie pomocy firmy Contoso, które jest opisane w dalszej części tego przewodnika.  
  
3.  Zawijaj rozszerzenia i powłoki ISO pakietu redystrybucyjnego do wdrożenia MSI (Instalator aplikacji). Ten przewodnik nie obejmuje kroku konfiguracji.  
  
Tworzenie magazynu zawartości programu Visual Studio. W scenariuszu powłoka w trybie zintegrowanym zmienić Visual Studio12 nazwę katalogu produktu w następujący sposób:  
  
-   Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.  
  
-   Utwórz plik o nazwie CatalogType.xml i dodaj go do folderu. Plik powinien zawierać następujące wiersze kodu:  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
Zdefiniuj magazynu zawartości w rejestrze. Powłoka w trybie zintegrowanym zmienić VisualStudio15 produktu nazwa katalogu:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     Klucz: Wartość ciągu LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     Klucz: Wartość ciągu CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] dokumentacji  
  
**Tworzenie projektu**  
  
Aby utworzyć rozszerzenie Isolated Shell:  
  
1.  W programie Visual Studio w obszarze **pliku**, wybierz **nowy projekt**w obszarze **inne typy projektów** wybierz **rozszerzalności**, a następnie wybierz pozycję  **Visual Studio Shell izolowany**. Nazwij projekt `ContosoHelpShell`) do utworzenia rozszerzalność projektu na podstawie szablonu Visual Studio Isolated Shell.  
  
2.  W Eksploratorze rozwiązań Otwórz ApplicationCommands.vsct w projekcie ContosoHelpShellUI w folderze plików zasobów. Upewnij się, że ten wiersz jest oznaczone jako komentarz (Wyszukaj "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  Wybierz klawisz F5, aby skompilować i uruchomić **debugowania**. Eksperymentalne wystąpienie programu IDE izolowane powłoki, wybierz **pomocy** menu. Upewnij się, że **Wyświetl Pomoc**, **Dodawanie i usuwanie zawartości Pomocy**, i **Ustaw preferencje pomocy** polecenia są wyświetlane.  
  
4.  W Eksploratorze rozwiązań Otwórz ContosoHelpShell.pkgdef w projekcie ContosHelpShell w folderze dostosowywania powłoki. Aby zdefiniować katalogu Contoso pomocy, Dodaj następujące wiersze:  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  W Eksploratorze rozwiązań Otwórz ContosoHelpShell.Application.pkgdef w projekcie ContosHelpShell w folderze dostosowywania powłoki. Aby włączyć pomocy F1, Dodaj następujące wiersze:  
  
    ```  
    // F1 Help Provider  
  
    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="13407"  
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"  
    @="Help3 Provider"  
    [$RootKey$\HelpProviders]  
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"  
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]  
    "Name"="Help3 Provider"  
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  W Eksploratorze rozwiązań, w menu kontekstowym rozwiązania ContosoHelpShell wybierz **właściwości** elementu menu. W obszarze **właściwości konfiguracji**, wybierz pozycję **programu Configuration Manager**. W **konfiguracji** kolumny, zmień wartość każdego "Debug" na "Wersja".  
  
7.  Skompiluj rozwiązanie. Spowoduje to utworzenie zestawu plików w folderze wersji, która będzie używana w następnej sekcji.  
  
Aby przetestować, tak jakby wdrożone:  
  
1.  Na tym komputerze jest wdrażany firmy Contoso, aby zainstalować pobrany ISO powłoki (powyższego).  
  
2.  Utwórz folder w \\\Program Files (x86)\\i nadaj mu nazwę `Contoso`.  
  
3.  Skopiuj zawartość z folderu wersji ContosoHelpShell \\\Program plików (x86) \Contoso\ folderu.  
  
4.  Uruchom Edytor rejestru, wybierając **Uruchom** w **Start** menu i wprowadzając `Regedit`. W Edytorze rejestru, wybierz **pliku**, a następnie **importu**. Przejdź do folderu projektu ContosoHelpShell. W folderze podrzędne ContosoHelpShell wybierz ContosoHelpShell.reg.  
  
5.  Utwórz magazyn zawartości:  
  
     Dla powłoki ISO - Utwórz magazyn zawartości Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12  
  
     Aby uzyskać [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] powłoka w trybie zintegrowanym, Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  Utwórz CatalogType.xml i Dodaj do zawierający magazynu zawartości (w poprzednim kroku):  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Dodaj następujące klucze rejestru:  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Wartość ciągu LocationPath:  
  
     Dla obrazu ISO powłoki:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Powłoka w trybie zintegrowanym:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en — stany USA  
  
     Klucz: Wartość ciągu CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] dokumentacji. Dla powłoki ISO jest to nazwa katalogu.  
  
8.  Skopiuj zawartość (pliki cab lub MSHC i MSHA) do folderu lokalnego.  
  
9. Przykład powłoka w trybie zintegrowanym wiersza polecenia do testowania magazynu zawartości. Dla powłoki ISO Zmień wartości katalogu i launchingApp odpowiednio do dopasowania produktu.  
  
     Metoda /helpQuery/catalogname VisualStudio15 "C:\Program plików (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" = "& Identyfikator strony = ContosoTopic0" /launchingApp Microsoft Visual Studio, 12.0  
  
10. Uruchamianie aplikacji Contoso (z katalogu głównego aplikacji Contoso). W powłoce ISO, wybierz **pomocy** element menu, a następnie zmień **Ustaw preferencje pomocy** do **korzystanie z lokalnej pomocy**.  
  
11. W powłoce, wybierz **pomocy** element menu, następnie **Wyświetl Pomoc**. Podgląd pomocy lokalnej należy uruchomić. Wybierz **zarządzania zawartością** kartę. W obszarze **źródła instalacji**, wybierz **dysku** przycisk opcji. Wybierz **...**  przycisk, a następnie przejdź do folderu lokalnego zawartością Contoso (skopiowane do folderu lokalnego w kroku powyżej). Wybierz HelpContentSetup.msha. Contoso powinien teraz wyświetlane jako książkę w opcje książki. Wybierz **Dodaj**, a następnie wybierz pozycję **aktualizacji** przycisk (prawym dolnym rogu).  
  
12. W środowisku IDE firmy Contoso wybierz klawisz F1, aby przetestować funkcje F1.  
  
### <a name="additional-resources"></a>Dodatkowe zasoby  
Środowisko uruchomieniowe interfejsu API, zobacz [interfejsu API systemu Windows Help](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
Aby uzyskać dodatkowe informacje na temat korzystania z interfejsu API pomocy, zobacz [przykłady kodu dla podglądu pomocy](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
Aby wyrazić opinię na temat tych składników, należy użyć [Microsoft Connect](http://connect.microsoft.com/).  
  
Prześlij sugestii funkcji [głos użytkownika firmy Microsoft](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
Aby uzyskać dodatkową pomoc, spróbuj [fora systemu pomocy i dokumentacja dla deweloperów MSDN](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
Aktualizacje krytyczne problem, można znaleźć pod adresem [Readme podglądu pomocy](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
Aby się bezpośrednio z zespołem PM podglądu pomocy, Wyślij wiadomość e-mail na adres hlpfdbk@microsoft.com