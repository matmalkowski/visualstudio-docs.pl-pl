---
title: "Ukończenie elementu członkowskiego w starsza wersja usługi języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e77511bdaaa96dc75f5be75c175b63fcd3cc3253
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="member-completion-in-a-legacy-language-service"></a>Element członkowski uzupełniania w starsza wersja usługi języka
IntelliSense zakończenia elementu członkowskiego jest etykietka narzędzia, która wyświetla listę możliwych elementów członkowskich z określonego zakresu, takich jak klasy, struktury, wyliczenia lub przestrzeni nazw. Na przykład w języku C#, jeśli użytkownik wpisze "to" następuje okres, listę wszystkich elementów członkowskich klasy lub struktury w bieżącym zakresie jest podana w listę, z którego użytkownik może wybrać.  
  
 Framework zarządzanego pakietu (MPF) zapewnia obsługę etykietka narzędzia i zarządzanie nimi na liście w etykietce narzędzia; wszystkie niezbędne jest współpracy z analizatora do dostarczania danych, który znajduje się na liście.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="how-it-works"></a>Jak to działa  
 Poniżej przedstawiono dwa sposoby, w których listy członków jest wyświetlany za pomocą klasy MPF:  
  
-   Pozycjonowanie karetkę na podstawie identyfikatora lub po znaku zakończenia elementu członkowskiego i wybierając **członków listy** z **IntelliSense** menu.  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner> Skaner wykrywa znak zakończenia elementu członkowskiego i ustawia token trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> dla tego znaku.  
  
 Znak zakończenia elementu członkowskiego oznacza element członkowski klasy, struktury lub wyliczenia do wykonania. Na przykład w języku C# lub Visual Basic znak zakończenia elementu członkowskiego jest `.`, a w języku C++ znak albo `.` lub `->`. Gdy znak wybierz element członkowski jest skanowany ustawionej wartości wyzwalacza.  
  
### <a name="the-intellisense-member-list-command"></a>Polecenie List Członkowskich IntelliSense  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Polecenie inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metoda <xref:Microsoft.VisualStudio.Package.Source> klasy i <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> z kolei wywołuje metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora składni metody przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Analizator Określa kontekst bieżącej pozycji, a także token w obszarze lub bezpośrednio przed bieżącym położeniu. Lista deklaracji w oparciu o ten token, jest widoczne. Na przykład w języku C#, jeśli położenie karetki na element członkowski klasy i wybierz **członków listy**, zostanie wyświetlona lista wszystkich elementów członkowskich klasy. Jeśli umieścisz karetkę po upływie znajdujący się zmienna obiektu powoduje wyświetlenie listy wszystkich elementów członkowskich klasy, które reprezentuje obiekt. Należy pamiętać, że jeśli karetka jest ustawiana w elemencie członkowskim, gdy jest wyświetlana lista elementów członkowskich, wybierając element członkowski z listy zastępuje element członkowski, który karetka znajduje się na jednym na liście.  
  
### <a name="the-token-trigger"></a>Token wyzwalacza  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wyzwalacza inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody na <xref:Microsoft.VisualStudio.Package.Source> klasy i <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metoda z kolei wywołuje analizator przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason> (Jeśli token wyzwalacza również uwzględniony <xref:Microsoft.VisualStudio.Package.TokenTriggers> flagę z powodu analizy jest <xref:Microsoft.VisualStudio.Package.ParseReason> które łączy wyboru elementu członkowskiego i wyróżnianie nawiasów klamrowych).  
  
 Analizator Określa kontekst bieżącej pozycji oraz co zostało wpisane przed zaznacz element członkowski. Z tej informacji analizator tworzy listę wszystkich elementów członkowskich w żądanym zakresie. Ta lista deklaracji są przechowywane w <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiekt, który jest zwracany z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Jeśli wszelkimi deklaracjami są zwracane, jest wyświetlana etykietka narzędzia elementu członkowskiego ukończenia. Etykietka narzędzia, która jest zarządzana przez wystąpienie <xref:Microsoft.VisualStudio.Package.CompletionSet> klasy.  
  
## <a name="enabling-support-for-member-completion"></a>Włączanie obsługi uzupełniania elementu członkowskiego  
 Musi mieć `CodeSense` wpis rejestru ustawioną wartość 1 do obsługi żadnej operacji IntelliSense. Ten wpis rejestru można ustawić za pomocą nazwany parametr przekazany do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybut użytkownika skojarzonego z pakietem języka. Klasy usługi języka odczytać wartości wpisu rejestru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.  
  
 Jeśli skaner zwraca token trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers>i z analizatora zwraca listę deklaracje, a następnie zostanie wyświetlona lista uzupełniania elementu członkowskiego.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Obsługa uzupełniania elementu członkowskiego w skanerze  
 Skaner musi być w stanie wykryć znak zakończenia elementu członkowskiego i ustawić wyzwalacz tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> podczas analizowania znaku.  
  
### <a name="example"></a>Przykład  
 Oto uproszczony przykład wykrywanie znak zakończenia elementu członkowskiego i ustala odpowiedni <xref:Microsoft.VisualStudio.Package.TokenTriggers> flagi. W tym przykładzie jest tylko w celach ilustracyjnych. Przyjęto założenie, że skaner zawiera metodę `GetNextToken` identyfikuje i zwraca tokenów z wiersza tekstu. Przykładowy kod ustawia wyzwalacza przy każdym stwierdzeniu rodzaj znaku.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>Obsługa uzupełniania elementu członkowskiego w analizatorze składni  
 Na zakończenie elementu członkowskiego <xref:Microsoft.VisualStudio.Package.Source> klasy wywołania <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metody. Lista musi implementować w klasie pochodzącej z <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Zobacz <xref:Microsoft.VisualStudio.Package.Declarations> klasy, aby uzyskać szczegółowe informacje o metodach musi implementować.  
  
 Analizator jest wywoływana z <xref:Microsoft.VisualStudio.Package.ParseReason> lub <xref:Microsoft.VisualStudio.Package.ParseReason> po wpisaniu znaku wybierz element członkowski. Lokalizacji określonej <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt jest bezpośrednio po znaku wybierz element członkowski. Analizator musi pobrać nazwy wszystkich elementów członkowskich, które mogą być wyświetlane na liście elementu członkowskiego, w tym punkcie określonego w kodzie źródłowym. Następnie analizator należy przeanalizować bieżący wiersz do określenia zakresu, które użytkownik chce skojarzone z znak wybierz element członkowski.  
  
 Ten zakres jest oparty na typie identyfikatora, przed zaznacz element członkowski. Na przykład w języku C#, otrzyma zmiennej członkowskiej `languageService` mający typ `LanguageService`, wpisz **languageService.** Tworzy listę wszystkich członków `LanguageService` klasy. Również w języku C# wpisując **to.** Tworzy listę wszystkich elementów członkowskich klasy w bieżącym zakresie.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wypełnienia <xref:Microsoft.VisualStudio.Package.Declarations> listy. Ten kod przyjęto założenie, że analizator konstruuje deklaracji i dodaje go do listy, wywołując `AddDeclaration` metoda `TestAuthoringScope` klasy.  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```