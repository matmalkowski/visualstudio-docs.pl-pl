---
title: Informacje o parametrach w klienta2 języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6aaf8ba9be9e16eeb979b0d64d3e80e8d70b564f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informacje o parametrach w starsza wersja usługi języka
Informacje o parametrach funkcji IntelliSense jest znak (zazwyczaj nawias otwierający) na liście parametrów metody początkowy etykietka narzędzia wyświetlana podpis metody, gdy użytkownik wpisze listy parametrów. Każdy parametr jest wprowadzana i wpisano parametr separatora (zazwyczaj przecinkami), element tooltip jest aktualizowana w celu wyświetlenia następny parametr pogrubione.  
  
 Klasy framework (MPF) zarządzanego pakietu zapewniają obsługę zarządzania tooltip informacje o parametrach. Analizator musi wykryć parametru uruchamianie, parametr następnie i znaków zakończenia parametr, a podać listę sygnatury metody i związanych z nimi parametrów.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="implementation"></a>Implementacja  
 Analizator należy ustawić wartość wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> jest ustawiona, gdy znajdzie parametr znaku początek listy (często nawias otwierający). Powinny one ustawione <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wyzwalaj, gdy znajdzie parametr separatora (często przecinkami). Powoduje to, że informacje o parametrach etykietka narzędzia można zaktualizować i wyświetlić następny parametr pogrubione. Analizator należy ustawić wartość wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> podczas jeśli znajdzie znak końcowy listy parametrów (często nawiasu zamykającego).  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wartość wyzwalacza inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metodę, która z kolei wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora składni metody przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Jeżeli analizator Określa, że przed listy parametrów znak początkowy identyfikatora jest rozpoznawaną nazwą metody, zwraca listę zgodnych podpisy metod w <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu. Jeśli znaleziono wszystkie podpisy metod, informacje o parametrach zostanie wyświetlony pierwszy podpisu na liście. Ta tooltip jest następnie aktualizowany jako jeden podpis jest wpisany. Po wpisaniu znaku zakończenia listy parametrów tooltip informacje o parametrach jest usuwany z widoku.  
  
> [!NOTE]
>  Aby upewnić się, że informacje o parametrach tooltip jest poprawnie sformatowana, konieczne jest przesłonięcie właściwości na <xref:Microsoft.VisualStudio.Package.Methods> klasę, aby podać odpowiednie znaki. Podstawowym <xref:Microsoft.VisualStudio.Package.Methods> klasa działa według założenia C# — styl podpis metody. Zobacz <xref:Microsoft.VisualStudio.Package.Methods> klasy, aby uzyskać szczegółowe informacje, w jaki sposób można to zrobić.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Włączanie obsługi informacje o parametrach  
 Aby obsługiwać informacje o parametrach etykietki narzędzi, należy ustawić `ShowCompletion` o nazwie parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> do `true`. Usługa języka odczytuje wartość tego wpisu rejestru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwości.  
  
 Ponadto <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> musi mieć ustawioną właściwość `true` uzyskać informacje o parametrach etykietki narzędzia ma być wyświetlany.  
  
### <a name="example"></a>Przykład  
 Oto uproszczony przykład wykrywanie znaki listy parametrów i wyzwalaczy odpowiednie ustawienia. W tym przykładzie jest tylko w celach ilustracyjnych. Przyjęto założenie, że skaner zawiera metodę `GetNextToken` identyfikuje i zwraca tokenów z wiersza tekstu. Przykładowy kod ustawia wyzwalacze przy każdym stwierdzeniu rodzaj znaku.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Obsługa etykietki narzędzia informacji parametru w analizatorze składni  
 <xref:Microsoft.VisualStudio.Package.Source> Klasy sprawia, że niektóre założenia dotyczące zawartości <xref:Microsoft.VisualStudio.Package.AuthoringScope> i <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy podczas wyświetlania i zaktualizować informacje o parametrach etykietka narzędzia.  
  
-   Podano analizator <xref:Microsoft.VisualStudio.Package.ParseReason> po wpisaniu znaku początek listy parametrów.  
  
-   Lokalizacji określonej <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt jest natychmiast po liście parametrów znak początkowy. Analizator należy zebrać podpisy wszystkie dostępne w deklaracji metody, których położenie i przechowywać je na liście w używanej wersji programu <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu. Ta lista zawiera nazwę metody metody typu (lub typ zwracany) oraz listę możliwych parametrów. Ta lista jest później wyszukiwany podpis metody lub podpisy do wyświetlenia w etykietce narzędzia informacje o parametrach.  
  
 Analizator należy następnie analizować wiersza określonego przez parametr <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt do zbierania nazwę metody wprowadzane, a także jak daleko wzdłuż użytkownika znajduje się w wpisanie parametrów. Jest to osiągane przez przekazanie Nazwa metody do <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metody w <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu, a następnie wywołując <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> przeanalizować metody, gdy znak początkowy listy parametrów, wywołania <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> — metoda podczas listy parametrów Następny znak jest przeanalizowanej i koniec wywołania <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metodą podczas analizowania znaku zakończenia listy parametrów. Wyniki wywołania te metody są używane przez <xref:Microsoft.VisualStudio.Package.Source> klasy odpowiednio zaktualizować informacje o parametrach etykietka narzędzia.  
  
### <a name="example"></a>Przykład  
 Oto wiersza tekstu, który użytkownik może wprowadzić. Liczby poniżej wiersza wskazują, który krok jest pobierana przez analizatora składni na tej pozycji w wierszu (przy założeniu analizy Przenosi od lewej do prawej). Jest tu założenie, że wszystko przed wierszem ma już przeanalizować podpisów metody, w tym podpis metody "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Poniżej opisano kroki, które przyjmuje analizatora:  
  
1.  Wywołania analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> z tekstem "testfunc".  
  
2.  Wywołania analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Wywołania analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Wywołania analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.