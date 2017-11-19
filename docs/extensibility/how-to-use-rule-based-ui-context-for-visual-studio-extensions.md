---
title: "Porady: Użyj kontekstu opartego na regułach interfejsu użytkownika dla rozszerzenia programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
ms.openlocfilehash: d1307f63464b0e652a97e9b06314b08112d8b097
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Porady: Użyj kontekstu opartego na regułach interfejsu użytkownika dla rozszerzenia programu Visual Studio
Program Visual Studio umożliwia ładowanie VSPackages podczas niektórych dobrze znanego <xref:Microsoft.VisualStudio.Shell.UIContext>s są uaktywnione. Jednak te konteksty interfejsu użytkownika nie są bardzo małe system, pozostawiając autorów rozszerzenia wybór nie, ale do pobrania dostępnych kontekstu interfejsu użytkownika, który uaktywnia przed punktem chcieli naprawdę pakiet VSPackage załadować. Aby uzyskać listę znanych kontekstów interfejsu użytkownika, zobacz <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Podczas ładowania pakietów może mieć negatywny wpływ na wydajność i ładowania je szybciej niż jest to konieczne nie jest najlepszym rozwiązaniem. Visual Studio 2015 wprowadzono koncepcję opartych na regułach kontekstów interfejsu użytkownika, mechanizm, który umożliwia autorom rozszerzenia zdefiniuj dokładne warunki kontekstu interfejsu użytkownika jest aktywny i załadować skojarzone VSPackages.  
  
## <a name="rule-based-ui-context"></a>Kontekst opartego na regułach interfejsu użytkownika  
 "Reguła" składa się z nowym kontekście interfejsu użytkownika (GUID) i wyrażenie logiczne, który odwołuje się do co najmniej jeden "warunki" połączonych z logicznych "i", "lub", "nie" operacji. "Warunki" są obliczane dynamicznie w czasie wykonywania, a wyrażenie jest ponownie oceniane zawsze, gdy jego zmiany warunków. Jeśli wyrażenie zwraca wartość true, jest aktywowana skojarzony kontekst interfejsu użytkownika. W przeciwnym razie kontekst interfejsu użytkownika jest wyłączony.  
  
 Na podstawie reguł kontekstu interfejsu użytkownika mogą być używane różne sposoby:  
  
1.  Określ ograniczenia widoczności poleceń i okien narzędzi. Polecenia/narzędzi systemu windows można ukryć, dopóki nie zostanie spełniony reguły kontekstu interfejsu użytkownika.  
  
2.  Jak automatycznie załadować ograniczenia: automatycznie obciążenia pakietów tylko wtedy, gdy reguły jest spełniony  
  
3.  Zadanie opóźnione: opóźnić ładowania dopiero po upływie określonego interwału i reguły nadal jest spełniony.  
  
 Mechanizm mogą być używane przez wszystkie rozszerzenia programu Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Tworzenie kontekstu opartego na regułach interfejsu użytkownika  
 Załóżmy, że rozszerzenie o nazwie TestPackage, który oferuje polecenia menu, które dotyczą tylko pliki z rozszerzeniem ".config". Przed VS2015, najlepszym rozwiązaniem było załadować TestPackage podczas <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> uaktywniono kontekstu interfejsu użytkownika. Nie jest to wydajne, ponieważ załadowane rozwiązanie nie może zawierać nawet pliku .config. Daj nam zobacz sposób opartych na regułach kontekstu interfejsu użytkownika można go użyć do aktywowania kontekst interfejsu użytkownika tylko wtedy, gdy plik z rozszerzeniem .config jest zaznaczone oraz załadować TestPackage po uaktywnieniu tego kontekstu interfejsu użytkownika.  
  
1.  Zdefiniuj nowy identyfikator GUID UIContext i Dodaj do klasy pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Na przykład, załóżmy, że nowe UIContext "UIContextGuid" ma zostać dodany. Utworzony identyfikator GUID (identyfikator GUID można tworzyć przez kliknięcie menu Narzędzia -> utworzyć identyfikatora guid) jest "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Następnie dodaj następujący kod w klasie pakietu:  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Dla atrybutów, Dodaj następujący kod: (szczegóły tych atrybutów opisano później)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Te metadane Zdefiniuj nowy identyfikator GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) i wyrażeń odwołujących się do pojedynczego termin "DotConfig". Termin "DotConfig" zwraca wartość true, gdy bieżące zaznaczenie w aktywnej hierarchii ma nazwę, która jest zgodna ze wzorcem wyrażenia regularnego "\\.config$" (kończy się wyrazem ".config"). Wartość (ustawienie domyślne) Określa opcjonalną nazwę reguły, które są przydatne w przypadku debugowania.  
  
     Wartości atrybutu są dodawane do pkgdef generowane w czasie kompilacji później.  
  
2.  W pliku VSCT TestPackage poleceń Dodaj flagę "DynamicVisibility" do odpowiednich poleceń:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  W sekcji widoczności VSCT powiązanie odpowiednie polecenia, aby UIContext nowy identyfikator GUID zdefiniowane w #1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  W sekcji symbole Dodaj definicję UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Teraz poleceń menu kontekstowego plików *.config będą widoczne tylko wtedy, gdy wybrany element w Eksploratorze rozwiązań jest plikiem ".config" i pakiet nie zostanie załadowany do momentu wybrania jednej z tych poleceń.  
  
 Następnie Użyjmy debugera, aby upewnić się, że pakiet ładuje, tylko gdy Oczekujemy na. Aby debugować TestPackage:  
  
1.  Ustaw punkt przerwania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
2.  Tworzenie TestPackage i Rozpocznij debugowanie.  
  
3.  Tworzenie projektu lub otwórz je.  
  
4.  Wybierz dowolne pliki z rozszerzeniem innym niż config. Punkt przerwania nie powinny być trafiony.  
  
5.  Wybierz plik App.Config.  
  
 TestPackage ładuje i zatrzymuje się na punkt przerwania.  
  
## <a name="adding-more-rules-for-ui-context"></a>Dodawanie więcej reguł dla kontekstu interfejsu użytkownika  
 Ponieważ reguły kontekstowe interfejsu użytkownika są wyrażeń logicznych, można dodawać reguły bardziej ograniczony w kontekście interfejsu użytkownika. Na przykład w kontekście interfejsu użytkownika powyżej, to określić, że reguła jest stosowana tylko po załadowaniu rozwiązania z projektem. W ten sposób polecenia nie będą wyświetlane jeśli otwarcia pliku ".config" jako autonomiczny plik, a nie jako część projektu.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Teraz wyrażenie odwołuje się do trzech warunków. Pierwsze dwa warunki "SingleProject" i "MultipleProjects" odwołuje się do innych dobrze znanych kontekstów interfejsu użytkownika (według ich identyfikatorów GUID). Trzeci termin "DotConfig" jest zdefiniowanego wcześniej kontekst interfejsu użytkownika opartego na regułach.  
  
## <a name="delayed-activation"></a>Opóźnionej aktywacji  
 Zasady mogą mieć opcjonalne "opóźnienie". Opóźnienie jest wyrażona w milisekundach. Jeśli nie istnieje opóźnienie powoduje, że aktywacji lub dezaktywacji kontekstu interfejsu użytkownika reguła opóźnionych w tym przedziale czasu. Jeśli zasada zmian z powrotem przed interwał opóźnienia, następnie nic się nie dzieje. Mechanizm ten może służyć do kroków inicjowania — szczególnie jednorazowe inicjowanie bez zależne czasomierzy lub rejestrowanie na potrzeby powiadomień bezczynności "różnicowanie".  
  
 Na przykład można określić reguły testu obciążenia do ma opóźnienie w milisekundach 100:  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Typy  
 Poniżej przedstawiono różne typy termin, które są obsługiwane:  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identyfikator GUID odwołuje się do kontekstu interfejsu użytkownika. Termin będzie mieć wartość true, zawsze, gdy kontekst interfejsu użytkownika jest aktywna i wartość false w przeciwnym razie wartość.|  
|HierSingleSelectionName:\<wzorzec >|Termin będzie mieć wartość true, zaznaczenie w aktywnej hierarchii jest jeden element, a nazwa wybranego elementu odpowiada wyrażeniu regularnemu .net przez "wzorzec".|  
|UserSettingsStoreQuery:\<zapytania >|"zapytania" reprezentuje pełną ścieżkę do magazynu ustawień użytkownika, który musi mieć wartość inną niż zero. Zapytanie jest podzielony na "kolekcji" i "propertyName" w ostatnim ukośnika.|  
|ConfigSettingsStoreQuery:\<zapytania >|"zapytania" reprezentuje pełną ścieżkę do magazynu ustawienia konfiguracji, który musi mieć wartość inną niż zero. Zapytanie jest podzielony na "kolekcji" i "propertyName" w ostatnim ukośnika.|  
|ActiveProjectFlavor:\<projectTypeGuid >|Termin będzie mieć wartość true, przy każdym języka jest aktualnie wybrany projekt (łącznie) i ma podtyp odpowiadał typowi danego projektu identyfikatora GUID.|  
|ActiveEditorContentType:\<contentType >|Termin jest wartość true, jeśli wybrany dokument to edytor tekstów, z danym typem zawartości.|  
|ActiveProjectCapability:\<wyrażenia >|Termin ma wartość true, gdy możliwości aktywnego projektu jest zgodna z podanego wyrażenia. Wyrażenie może to wyglądać jak VB &#124; CSharp|  
|SolutionHasProjectCapability:\<wyrażenia >|Podobny do powyżej, ale termin ma wartość true, gdy rozwiązanie ma załadowanego projektu, który pasuje do wyrażenia.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|Termin będzie mieć wartość true, zawsze, gdy rozwiązanie zawiera projekt, który jest języka (łącznie) oraz jej podtyp odpowiadał typowi projektu dany identyfikator GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Zgodność z rozszerzeniem między wersjami  
 Reguły na podstawie konteksty interfejsu użytkownika jest nową funkcją w programie Visual Studio 2015 i nie może być przenoszone do wcześniejszych wersji. Spowoduje to utworzenie problem z rozszerzeń/pakietów przeznaczonych dla wielu wersji programu Visual Studio, który musi być ładowane automatycznie w programie Visual Studio 2013 lub starszym, ale można korzystać z kontekstami interfejsu użytkownika na podstawie reguł zapobiegające auto ładowany w programie Visual Studio 2015.  
  
 Aby zapewnić obsługę tych pakietów, AutoLoadPackages wpisy w rejestrze umożliwiają teraz flagę w polu wartość wskazująca, że wpis ma być pomijana w programie Visual Studio 2015 lub nowszym. Można to zrobić, dodając flagi opcję <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Teraz można dodać VSPackages **SkipWhenUIContextRulesActive** opcji w celu ich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atrybutu, aby wskazać, należy ją ignorować wpis w programie Visual Studio 2015 i nowszych.  
  
## <a name="extensible-ui-context-rules"></a>Reguły kontekstowe rozszerzonego interfejsu użytkownika  
 Czasami pakietów nie można użyć statycznej reguły kontekstowe interfejsu użytkownika. Na przykład załóżmy, że masz pakiet obsługi rozszerzalności w taki sposób, że stan polecenia jest oparty na Edytor typów, które są obsługiwane przez dostawców MEF zaimportowane. Polecenie jest włączone, jeśli rozszerzenie obsługi bieżącego typu edycji. W takich przypadkach samego pakietu nie można użyć statyczne reguły kontekstu interfejsu użytkownika, ponieważ warunki zmieniłby się w zależności od tego, które MEF rozszerzenia są dostępne.  
  
 Aby zapewnić obsługę tych pakietów, kontekstów interfejsu użytkownika na podstawie reguł obsługuje wyrażenie stałe zapisany "*" oznacza wszystkie poniższe warunki zostaną być połączony z lub. Umożliwia głównym pakietu do definiowania kontekstu interfejsu użytkownika na podstawie znanych reguł i powiązanie stanu polecenia dla tego kontekstu. Następnie wszystkie rozszerzenia MEF docelowe głównej pakietu dodać terminów dla edytory obsługiwanych bez wpływania na inne postanowienia lub wzorca wyrażenia.  
  
 Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> dokumentacji przedstawiono składnię rozszerzalnych zasad kontekstu interfejsu użytkownika.