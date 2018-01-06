---
title: "Obsługa wstawki kodu za pośrednictwem usługi języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6102a5bb6298cd6403285e3d36842424b0be3412
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Obsługa wstawki kodu za pośrednictwem usługi języka starsza wersja
Fragment kodu jest fragment kodu, który znajduje się w pliku źródłowym. Fragment kodu, sam jest oparte na języku XML szablonu z zestawu pól. Te pola są wyróżnione po fragment kodu zostanie wstawiony i może mieć różne wartości w zależności od kontekstu, w którym wstawieniu fragmentu. Natychmiast po wstawieniu fragmentu, usługa języka można sformatować fragment kodu.  
  
 Fragment kodu zostanie wstawiony w trybie edycji specjalny, który umożliwia pola fragment kodu, który ma zostać przesłane za pomocą klawisza TAB. Pola może obsługiwać menu rozwijanych IntelliSense stylu. Użytkownik zatwierdza fragment kodu do pliku źródłowego, wpisując ENTER lub klawisz ESC. Aby dowiedzieć się więcej o fragmentów, zobacz [wstawki kodu](../../ide/code-snippets.md).  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [wskazówki: implementacja wstawki kodu](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Obsługa Framework pakietu dla wstawki kodu zarządzanego  
 Struktura pakietu zarządzanych (MPF) obsługuje większość funkcji fragment, na podstawie odczytu szablon do wstawiania wstawki kodu i specjalną włączenie trybu edycji. Obsługa odbywa się za pośrednictwem <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy.  
  
 Gdy <xref:Microsoft.VisualStudio.Package.Source> tworzenia wystąpienia klasy <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> metody w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy jest wywoływana w celu uzyskania <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiektu (należy pamiętać, że podstawowym <xref:Microsoft.VisualStudio.Package.LanguageService> klasy zawsze zwraca nową <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiekt dla każdego <xref:Microsoft.VisualStudio.Package.Source> obiekt).  
  
 MPF nie obsługuje rozszerzania funkcji. Funkcja rozszerzenia jest nazwane funkcję, która jest osadzony w szablonie fragment i zwraca jedną lub więcej wartości do umieszczenia w polu. Wartości są zwracane przez język się za pośrednictwem usługi <xref:Microsoft.VisualStudio.Package.ExpansionFunction> obiektu. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Obiektu musi być implementowana przez usługę język do obsługi funkcji rozszerzenia.  
  
## <a name="providing-support-for-code-snippets"></a>Zapewnianie obsługi w przypadku wstawki kodu  
 Aby włączyć obsługę wstawki kodu, należy podać albo zainstalować fragmenty kodu i musisz podać środki do wstawienia tych fragmentów kodu użytkownika. Istnieją trzy kroki umożliwiające włączenie obsługi fragmentów kodu:  
  
1.  Instalowanie plików fragment kodu.  
  
2.  Włączanie wstawki kodu usługi języka.  
  
3.  Wywoływanie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiektu.  
  
### <a name="installing-the-snippet-files"></a>Instalowanie plików fragment kodu  
 Wszystkie fragmenty kodu języka są przechowywane jako szablon w plikach XML zwykle jeden fragment szablon dla każdego pliku. Aby uzyskać więcej informacji o schemat XML używane dla szablonów fragmentów kodu, zobacz [fragmenty kodu — odwołanie do schematu](../../ide/code-snippets-schema-reference.md). Każdy szablon fragment jest identyfikowany przy użyciu identyfikatora języka. Język ten identyfikator jest określona w rejestrze i są umieszczane w `Language` atrybutu \<kod > tag w szablonie.  
  
 Zazwyczaj są dwóch lokalizacjach, w którym są przechowywane pliki szablonów fragment: 1) Jeśli został zainstalowany język i 2) w folderze użytkownika. Lokalizacje te są dodawane do rejestru tak że Visual Studio **Menedżerze fragmentów kodu** można znaleźć fragmenty kodu. Folder użytkownika jest przechowywania wstawki utworzone przez użytkownika.  
  
 Układ typowy folder plików szablonów zainstalowanych fragment wygląda następująco: *[InstallRoot]*\\*[TestLanguage]*\Snippets\\*[LCID]*\Snippets.  
  
 *[InstallRoot]*  jest folder języka jest zainstalowany w.  
  
 *[TestLanguage]*  to nazwa języka jako nazwa folderu.  
  
 *[LCID]*  to identyfikator ustawień regionalnych. Jest to sposób zlokalizowane wersje programu fragmentów są przechowywane. Na przykład identyfikator ustawień regionalnych dla języka angielskiego jest 1033, więc *[LCID]* zastępuje 1033.  
  
 Należy podać jedną dodatkowego pliku i jest plikiem indeksu pliku, zwykle nazywane SnippetsIndex.xml lub ExpansionsIndex.xml (możesz użyć dowolnego prawidłowy pliku z rozszerzeniem .xml). Ten plik znajduje się zwykle w *[InstallRoot]*\\*[TestLanguage]* folderu i umożliwia określenie dokładnej lokalizacji folderu fragmentów, jak również identyfikator języka i identyfikator GUID języka Usługa, która używa fragmenty kodu. Dokładnej ścieżki pliku indeksu są umieszczane w rejestrze, zgodnie z opisem w dalszej części "Instalowanie wpisy rejestru". Oto przykład pliku SnippetsIndex.xml:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 \<Języka > tag Określa identyfikator języka ( `Lang` atrybut) i identyfikator GUID usługi języka.  
  
 W tym przykładzie przyjęto założenie, że zainstalowano usługi języka w folderze instalacji programu Visual Studio. Identyfikator LCID % zostanie zastąpiony identyfikator użytkownika bieżącego ustawienia regionalne. Wiele \<SnippetDir > tagi do dodania, po jednej dla każdego innego katalogu i ustawień regionalnych. Ponadto folder fragment może zawierać podfolderów, z których każdy jest określone w pliku indeksu o \<SnippetSubDir > tag, który jest osadzony w \<SnippetDir > tagu.  
  
 Użytkownicy mogą także tworzyć własne wstawki dla danego języka. Te są zwykle przechowywane w folderze ustawień użytkownika, na przykład *[TestDocs]*\Code wstawki\\*[TestLanguage]*\Test wstawki kodu, gdy *[TestDocs]* jest lokalizacja folderu Ustawienia użytkownika dla programu Visual Studio.  
  
 Następujące elementy podstawienia można umieścić w ścieżce przechowywane w \<DirPath > znacznika w pliku indeksu.  
  
|Element|Opis|  
|-------------|-----------------|  
|IDENTYFIKATOR LCID %|Identyfikator ustawień regionalnych.|  
|% InstallRoot %|Główny folder instalacji programu Visual Studio, na przykład C:\Program Files\Microsoft Visual Studio 8.|  
|% ProjDir %|Folder zawierający bieżącego projektu.|  
|% ProjItem %|Folder zawierający element bieżącego projektu.|  
|% TestDocs %|Folderu w folderze ustawień użytkownika, na przykład C:\Documents and Settings\\*[username]*\My Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Włączanie usługi języka wstawki kodu  
 Wstawki kodu można włączyć usługi języka, dodając <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> atrybutu VSPackage (zobacz [zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md) szczegółowe informacje). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> i <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametry są opcjonalne, ale powinna zawierać `SearchPaths` nazwany parametr, aby poinformować **Menedżerze fragmentów kodu** lokalizacji z fragmentów.  
  
 Poniżej przedstawiono przykład sposobu użycia tego atrybutu:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>Wywoływania dostawcy rozszerzeń  
 Usługa języka steruje wstawiania żadnych fragment kodu, a także sposób, który jest wywoływany wstawiania.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Wywoływania dostawcy rozszerzeń dla wstawki kodu  
 Istnieją dwa sposoby do wywoływania dostawcy rozszerzeń: za pomocą polecenia menu lub przy użyciu skrótu z listy uzupełniania.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Wstawianie wstawek kodu za pomocą polecenia Menu  
 Polecenia menu do wyświetlenia w przeglądarce fragment, możesz dodać polecenie menu, a następnie wywołać <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfejsu w odpowiedzi na polecenie menu.  
  
1.  Dodaj polecenie i przycisk do pliku vsct. Można znaleźć instrukcje dotyczące wykonywania, dlatego w [Tworzenie rozszerzenia za pomocą polecenia Menu](../../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Klasa wyprowadzona z <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy i zastąpić <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> metodę, aby wskazać obsługę nowego polecenia menu. W tym przykładzie zawsze włączone polecenie menu.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  Zastąpienie <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> metody w <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy w celu uzyskania <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiekt i wywołanie <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metody dla tego obiektu.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     Następujące metody w <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy są wywoływane przez Visual Studio w podanej kolejności podczas wstawiania wstawki kodu:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Po <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> metoda jest wywoływana, wstawiono fragment kodu i <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiekt jest w trybie edycji specjalne używane do modyfikowania fragment kodu, który właśnie został wstawiony.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Wstawianie wstawek kodu za pomocą skrótu  
 Implementacja skrót z listy uzupełniania jest znacznie bardziej skomplikowane niż wykonania polecenia menu. Najpierw należy dodać fragment skróty do listy uzupełniania IntelliSense programu word. Następnie należy Wykryj, kiedy w wyniku zakończenia wstawiono fragment krótką nazwę. Na koniec należy uzyskać fragment tytuł i ścieżki przy użyciu nazwy skrótów i przekazać te informacje do <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider> metody.  
  
 Aby dodać fragment skróty do listy uzupełniania word, dodaj je do <xref:Microsoft.VisualStudio.Package.Declarations> obiektu w Twojej <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy. Należy się upewnić się, że można zidentyfikować skrótów jako nazwa fragment kodu. Na przykład zobacz [wskazówki: pobieranie listy z zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Wykrywa wstawiania skrótów fragmentu kodu w <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metody <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Ponieważ nazwy fragment został już wstawiony do pliku źródłowego, należy usunąć po wstawieniu rozszerzenia. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Metoda przyjmuje zakresu, który opisuje punkt wstawiania dla fragmentu; Jeśli zakres zawiera nazwę fragment całego pliku źródłowego, ta nazwa jest zamieniana fragment kodu.  
  
 W tym miejscu jest wersja <xref:Microsoft.VisualStudio.Package.Declarations> klasa, która obsługuje wstawiania wstawek podane krótką nazwę. Inne metody w <xref:Microsoft.VisualStudio.Package.Declarations> klasy zostały pominięte dla uzyskania przejrzystości. Należy pamiętać, że trwa konstruktorze tej klasy <xref:Microsoft.VisualStudio.Package.LanguageService> obiektu. To może zostać przekazane za z wersji systemu <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu (na przykład implementacji <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy może potrwać <xref:Microsoft.VisualStudio.Package.LanguageService> obiektu w swoich konstruktorach i przekazać do obiektu z `TestDeclarations` konstruktora klasy).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Gdy usługa języka pobiera nazwę skrótów, wywołuje <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> metodę, aby uzyskać tytuł wstawki nazwę pliku i kod. Usługa języka następnie wywołuje <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy, aby wstawić fragment kodu. Następujące metody są wywoływane przez program Visual Studio w podanej kolejności w <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy podczas wstawiania wstawki kodu:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Aby uzyskać więcej informacji na temat pobierania listy fragmentów kodu zainstalowane usługi języka, zobacz [wskazówki: pobieranie listy z zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implementująca klasa ExpansionFunction  
 Funkcja rozszerzenia jest nazwane funkcję, która jest osadzony w szablonie fragment i zwraca jedną lub więcej wartości do umieszczenia w polu. Aby zapewnić obsługę funkcji rozszerzenia w usłudze języka, musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.ExpansionFunction> klasy i wdrożenie <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> metody. Następnie należy zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> metody w <xref:Microsoft.VisualStudio.Package.LanguageService> służącą do zwracania nowego wystąpienia tej wersji systemu <xref:Microsoft.VisualStudio.Package.ExpansionFunction> klasy dla każdej funkcji rozszerzenia obsługiwanych. Jeśli obsługują listę możliwych wartości z funkcji rozszerzenia, należy również zmienić <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> metoda <xref:Microsoft.VisualStudio.Package.ExpansionFunction> klasę, aby zwrócić listę tych wartości.  
  
 Funkcja rozszerzenia, która przyjmuje argumenty lub musi mieć dostęp inne pola nie powinna być skojarzona z edycji pole jako dostawca rozszerzeń nie może być pełni zainicjowana w czasie, gdy zostanie wywołana funkcja rozszerzenia. W związku z tym funkcja rozszerzenia nie będzie mógł uzyskać wartości argumentów lub inne pole.  
  
### <a name="example"></a>Przykład  
 Oto jak wywołuje funkcję rozszerzeń prosty przykład `GetName` może być zaimplementowany. Ta funkcja rozszerzenia dołącza numer na nazwę klasy podstawowej zawsze funkcji rozszerzenia zostanie uruchomiony (które odpowiada zawsze fragmentu kodu skojarzony jest wstawiany).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Wstawki kodu](../../ide/code-snippets.md)   
 [Przewodnik: pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)