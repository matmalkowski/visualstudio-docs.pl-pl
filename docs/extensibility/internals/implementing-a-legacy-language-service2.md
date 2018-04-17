---
title: Implementowanie klienta2 języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d54572bc3b105af01ed42b01a27f363da80d58de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-legacy-language-service"></a>Wdrażanie usługi języka starsza wersja
Do wdrożenia usługi języka przy użyciu zarządzanego pakietu framework (MPF), musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i implementować następujące metody abstrakcyjne i właściwości:  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> — Metoda  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> — Metoda  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> — Metoda  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Właściwości  
  
 Zobacz odpowiedniej sekcji poniżej szczegółowe informacje dotyczące implementacji tych metod i właściwości.  
  
 Do obsługi dodatkowych funkcji, usługa języka może mieć wyprowadzenia klasy z jednej z klas usługi języka MPF; na przykład do obsługi dodatkowych poleceń, musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy i Przesłoń kilka metod obsługi polecenia (zobacz <xref:Microsoft.VisualStudio.Package.ViewFilter> szczegółowe informacje). <xref:Microsoft.VisualStudio.Package.LanguageService> Klasa udostępnia wiele metod, które są wywoływane w celu utworzenia nowego wystąpienia różnych klas i zastąpić metodę tworzenia odpowiednich zapewnienie wystąpienia klasy. Na przykład, należy zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> metody w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy można zwrócić wystąpienia własny <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy. W sekcji "Tworzenie wystąpień klasy niestandardowej" Aby uzyskać więcej informacji.  
  
 Usługi języka może też podawać własną ikony, które są używane w wielu miejscach. Na przykład gdy jest wyświetlana lista uzupełniania IntelliSense, każdy element na liście mogą mieć ikony skojarzone z nią oznaczyć element jako metody, klasy, przestrzeń nazw, właściwości, lub niezależnie od jest niezbędne dla danego języka. Te ikony służą na wszystkich listach IntelliSense, **pasek nawigacyjny**, a następnie w **listy błędów** okna zadań. Zobacz poniższą sekcję "Obsługi Language obrazów", aby uzyskać szczegółowe informacje.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences — metoda  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Metoda zawsze zwraca to samo wystąpienie elementu <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Korzystając z podstawowym <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy, jeśli nie potrzebujesz wszelkie dodatkowe preferencje dotyczące usługi języka. Klasy usługi języka MPF założono obecności co najmniej podstawowy <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano Typowa implementacja <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metody. W tym przykładzie użyto podstawowym <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>GetScanner — metoda  
 Ta metoda zwraca wystąpienie klasy <xref:Microsoft.VisualStudio.Package.IScanner> obiekt, który implementuje analizator wiersza lub skanera służył tokeny i ich typów i wyzwalaczy. Skaner ten jest używany w <xref:Microsoft.VisualStudio.Package.Colorizer> klasy kolorowania, mimo że skanera można również uzyskania typy tokenów i wyzwalaczy jako prelude z operacją bardziej złożone analizy. Należy podać klasę implementującą <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu i zaimplementuj wszystkie metody w <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano Typowa implementacja <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody. `TestScanner` Klasa implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu (tego nie pokazano).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>ParseSource — metoda  
 Analizuje plik źródłowy, na podstawie różnych przyczyn. Ta metoda jest podana <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu, który opisuje, czego oczekuje się od określonej operacji analizy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda wywołuje bardziej złożonych parser, określająca funkcję tokena i zakres. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda jest używana w pomocy technicznej dla operacji IntelliSense, jak również dopasowanie nawiasu klamrowego. Nawet jeśli nie obsługuje takich operacji zaawansowane, możesz nadal musi zwracać prawidłowy <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu i czy wymaga utworzenia klasy, która implementuje <xref:Microsoft.VisualStudio.Package.AuthoringScope> interfejsu i wdrożenie wszystkie metody w tym interfejsie. Może zwracać wartości null z metody wszystkie, ale <xref:Microsoft.VisualStudio.Package.AuthoringScope> sam obiekt nie może być wartością null.  
  
### <a name="example"></a>Przykład  
 Ten przykład przedstawia minimalny implementacja <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> — metoda i <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy wystarczające, aby umożliwić usłudze języka skompilować i działać bez faktycznie obsługi bardziej zaawansowanych funkcji.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Właściwość Name  
 Ta właściwość zwraca nazwę usługi języka. Musi to być tej samej nazwie przy usługi języka został zarejestrowany. Ta nazwa jest używana w wielu miejscach, jest najbardziej widocznym którego <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy, której nazwa jest używana do dostępu do rejestru. Nie jest lokalizowany nazwa zwracane przez tę właściwość, ponieważ jest używany w rejestrze dla nazwy klucza i wpis rejestru.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono jeden możliwości stosowania <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> właściwości. Należy pamiętać, że nazwa tutaj ustalony: rzeczywista nazwa mają być uzyskiwane z pliku zasobów dzięki mogą być używane w rejestracji usługi języka (zobacz [zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>Tworzenie wystąpień klas niestandardowych  
 Zapewnienie wystąpień własne wersje każdej klasy można zastąpić poniższych metod w określonej klasy.  
  
### <a name="in-the-languageservice-class"></a>W klasie LanguageService  
  
|Metoda|Zwrócony — klasa|Opis|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Aby obsługiwać niestandardowe dodatki do widoku tekstu.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Aby obsługiwać niestandardowe właściwości dokumentu.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Do obsługi **pasek nawigacyjny**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Do obsługi funkcji w szablonów fragmentów kodu.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Do obsługi fragmentów kodu (tej metody zwykle nie jest zastępowany).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Do obsługi dostosowywania <xref:Microsoft.VisualStudio.Package.ParseRequest> struktury (tej metody zwykle nie jest zastępowany).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Do obsługi formatowania kodu źródłowego, określenie znaki komentarza i dostosowywanie podpisy metod.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Do obsługi dodatkowych poleceń.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Do obsługi wyróżnianie składni (tej metody zwykle nie jest zastępowany).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Do obsługi dostępu do Preferencje językowe. Ta metoda musi zostać wdrożone, ale może zwrócić wystąpienia klasy podstawowej.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Aby zapewnić analizatorem umożliwia identyfikowanie typy tokenów w wierszu. Ta metoda musi zostać wdrożona i <xref:Microsoft.VisualStudio.Package.IScanner> musi być pochodną.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Aby zapewnić analizatorem umożliwia identyfikowanie funkcjonalność i zakres w całym całego pliku źródłowego. Ta metoda musi zostać wdrożona i musi zwrócić wystąpienie swoją wersję <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy. Jeśli wszystkie mają być obsługiwane jest wyróżnianie składni (co wymaga <xref:Microsoft.VisualStudio.Package.IScanner> analizator składni zwrócił z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> — metoda), możesz zrobić nic w ramach tej metody inne niż powrotu wersję <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy, w której wszystkie metody zwrócić wartości null.|  
  
### <a name="in-the-source-class"></a>W klasie źródła  
  
|Metoda|Zwrócony — klasa|Opis|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Dostosowywania wyświetlania listy uzupełniania IntelliSense (tej metody zwykle nie jest zastępowany).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Do obsługi znaczników na liście zadań na liście błędów; w szczególności obsługę funkcji poza otwierania pliku i przejście do wiersza, który spowodował błąd.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Dostosowywania wyświetlania IntelliSense parametru podpowiedź.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Do obsługi komentarzy kodu.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Do zbierania informacji podczas operacji analizy.|  
  
### <a name="in-the-authoringscope-class"></a>W klasie AuthoringScope  
  
|Metoda|Zwrócony — klasa|Opis|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Lista deklaracji, takich jak elementy Członkowskie lub typów. Ta metoda musi zostać wdrożone, ale może zwrócić wartość null. Jeśli ta metoda zwróci prawidłowego obiektu, obiekt musi być wystąpieniem tej wersji systemu <xref:Microsoft.VisualStudio.Package.Declarations> klasy.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Zawiera listę podpisy metod dla danego kontekstu. Ta metoda musi zostać wdrożone, ale może zwrócić wartość null. Jeśli ta metoda zwróci prawidłowego obiektu, obiekt musi być wystąpieniem tej wersji systemu <xref:Microsoft.VisualStudio.Package.Methods> klasy.|  
  
## <a name="language-service-images"></a>Język obsługi obrazów  
 Aby udostępnić listę ikon do użycia w całym usługi języka, Przesłoń <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metody w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i zwracać <xref:System.Windows.Forms.ImageList> zawierający ikony. Podstawowym <xref:Microsoft.VisualStudio.Package.LanguageService> klasy ładuje domyślny zestaw ikon. Ponieważ Określ indeks obrazu dokładnie w tych miejscach, które wymagają ikony, jak Rozmieść listy obrazów jest całkowicie zależy.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Obrazy używane w liście uzupełniania IntelliSense  
 Na liście uzupełniania IntelliSense, indeks obrazu jest określony dla każdego elementu w <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metody <xref:Microsoft.VisualStudio.Package.Declarations> klasy, który należy zastąpić, jeśli chcesz udostępnić indeks obrazu. Wartość zwracana z <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metody jest indeksem listy obrazów do <xref:Microsoft.VisualStudio.Package.CompletionSet> zwracane z konstruktora klasy i który jest tej samej listy obrazów <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metody w <xref:Microsoft.VisualStudio.Package.LanguageService> (można zmienić listy obrazów, które do klasy na użytek <xref:Microsoft.VisualStudio.Package.CompletionSet> razie przesłonięcia <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> metoda <xref:Microsoft.VisualStudio.Package.Source> klasę, aby podać listę inny obraz).  
  
### <a name="images-used-in-the-navigation-bar"></a>Obrazy używane na pasku nawigacyjnym  
 **Pasek nawigacyjny** Wyświetla listę typów i członków i jest używany do szybkiego nawigacji można wyświetlić ikon. Te ikony są uzyskiwane z <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metody w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i nie można zastąpić specjalnie z myślą o **pasek nawigacyjny**. Indeksy używane dla każdego elementu w polu kombi są określane podczas list reprezentujących pola kombi są wypełniane <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody w <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy (zobacz [obsługę paska nawigacyjnego w starsza wersja usługi języka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Te wskaźniki obrazu są uzyskiwane w jakiś sposób z analizatora, zwykle za pomocą swojej wersji programu <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Jak indeksy są uzyskiwane jest całkowicie zależy.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Obrazy używane w oknie zadania listy błędów  
 Zawsze, gdy <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizator — metoda (zobacz [analizatora usługi języka starszych i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) napotka błąd i przekazuje tego błędu, aby <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metody w <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy, zgłaszany jest błąd w  **Lista błędów** okna zadań. Ikona mogą być skojarzone z każdym elementem, który jest wyświetlany w oknie zadania oraz tę ikonę pochodzą z tej samej listy obrazów zwrócony z <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Domyślne zachowanie klasy MPF nie będzie wyświetlany obraz z komunikatem o błędzie. Może jednak zmienić to zachowanie przez wyprowadzanie klasy z <xref:Microsoft.VisualStudio.Package.Source> klasy i zastępowanie <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metody. W tej metody, utworzysz nową <xref:Microsoft.VisualStudio.Package.DocumentTask> obiektu. Przed powrotem tego obiektu, można użyć <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> właściwość <xref:Microsoft.VisualStudio.Package.DocumentTask> obiektu w celu ustawienia indeks obrazu. To może wyglądać następująco. Należy pamiętać, że `TestIconImageIndex` jest wyliczeniem, który zawiera listę wszystkich ikon i jest specyficzna dla tego przykładu. Może mieć inny sposób identyfikowania ikony w usłudze języka.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TastPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>Lista obrazów domyślny dla usługi języka  
 Listy obrazów domyślne, dostarczone z klasami podstawowymi usługi języka MPF zawiera szereg ikony skojarzone z częściej elementy języka. Zbiorcze ikony ułożone w zestawach sześciu różnych wersji odpowiadającej pojęć dotyczących dostępu publiczne, wewnętrzne, friend, chronionych, prywatnego i skrótów. Na przykład może mieć inne ikony dla metody w zależności od tego, czy jest publicznych, chronionych lub prywatnych.  
  
 Wyliczenie następujące określa typowe nazwy dla każdego zestawu ikonę i określa skojarzonego indeksu. Na przykład oparte na wyliczeniu, można określić indeks obrazu dla Metoda chroniona jako `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Można zmienić nazwy tego wyliczenia zgodnie z potrzebami.  
  
```csharp  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Omówienie usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-overview.md)   
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)