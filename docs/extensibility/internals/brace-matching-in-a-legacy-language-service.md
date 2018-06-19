---
title: Parowanie nawiasów klamrowych w usłudze języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9df179d6f5b1bd6d7b9f2c827568b6954860b81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131966"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Parowanie nawiasów klamrowych w starsza wersja usługi języka
Dopasowywanie nawiasu klamrowego pomaga developer śledzić elementy języka, które muszą zostać wykonane ze sobą, takie jak nawiasy i nawiasy klamrowe. Gdy dewelopera wprowadza zamykający nawias klamrowy, zostanie wyróżniona nawiasem otwierającym.  
  
 Można dopasować do dwóch lub trzech elementów wspólnie występującą, nazywanych pary i triples. Triples to zestawy trzy elementy występujące wspólnie. Na przykład w języku C# `foreach` instrukcji formularzy triple: "`foreach()`","`{`", a "`}`". Wszystkie trzy elementy są wyróżnione po zamykającego nawiasu klamrowego.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej na temat nowych sposób implementowania parowanie nawiasów klamrowych, zobacz [wskazówki: wyświetlanie pasujących nawiasów klamrowych](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasa obsługuje pary i triples z <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> i <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metody.  
  
## <a name="implementation"></a>Implementacja  
 Usługa języka musi zidentyfikować wszystkich elementów pasujących w języku, a następnie zlokalizuj wszystkie pary dopasowania. Zazwyczaj jest to osiągane przez wdrożenie <xref:Microsoft.VisualStudio.Package.IScanner> wykrywanie dopasowane języka i następnie przy użyciu <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody, aby dopasować elementy.  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metoda wywołuje skanera tokenizacji wiersza i zwraca token bezpośrednio przed karetką. Skaner wskazuje znaleziono pary element języka, ustawiając wartość tokenu wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> na bieżący token. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodę, która z kolei wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metody z wartością Przyczyna analizy <xref:Microsoft.VisualStudio.Package.ParseReason> można znaleźć zgodnego elementu języka. W przypadku odnalezienia pasującego elementu języka są wyróżnione obu elementów.  
  
 Pełny opis sposobu wpisanie nawiasu klamrowego wyzwala wyróżnianie nawiasów klamrowych, zobacz sekcję "Przykład przeanalizować operacji" w temacie [analizatora usługi języka starszych i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Włączanie obsługi pasujących nawiasów klamrowych  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Atrybut można określać `MatchBraces`, `MatchBracesAtCaret`, i `ShowMatchingBrace` nazwanych parametrów, które Ustaw odpowiednie właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Można również ustawić właściwości preferencji języka przez użytkownika.  
  
|Wpis rejestru|Właściwość|Opis|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Umożliwia parowanie nawiasów klamrowych|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Umożliwia parowanie nawiasów klamrowych jako przenosi karetki.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Prezentuje pasującego nawiasu klamrowego.|  
  
## <a name="matching-conditional-statements"></a>Dopasowywanie warunkowe instrukcje  
 Warunkowe instrukcje może dopasować takich jak `if`, `else if`, i `else`, lub `#if`, `#elif`, `#else`, `#endif`, w taki sam sposób jak ogranicznik. Można podklasy <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy i podaj obejmuje metody, które można dodać tekstu oraz ograniczników do tablicy wewnętrznej pasujących elementów.  
  
## <a name="setting-the-trigger"></a>Ustawienie wyzwalacza  
 Poniższy przykład pokazuje, jak wykrywanie zgodne nawiasy, nawiasy klamrowe i nawiasy kwadratowe i ustawienie wyzwalacza dla niego skanera. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metoda <xref:Microsoft.VisualStudio.Package.Source> klasy wykrywa wyzwalacza i wywołuje analizatora składni można znaleźć zgodnego pary (zobacz sekcję "Wyszukiwanie Match" w tym temacie). W tym przykładzie jest tylko w celach ilustracyjnych. Przyjęto założenie, że skaner zawiera metodę `GetNextToken` identyfikuje i zwraca tokenów z wiersza tekstu.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private const string braces = "()[]{}";  
        private Lexer lex;  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar) && token.Length > 0)  
                {  
                    if (braces.IndexOf(firstChar) != -1)  
                    {  
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;  
                    }  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="matching-the-braces"></a>Dopasowywanie nawiasy klamrowe  
 Oto uproszczony przykład dopasowywania {} elementy języka, () i [] i dodawanie ich zakresy do <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu. Ta metoda nie jest zalecane podejście do analizowania kodu źródłowego; jest tylko w celach ilustracyjnych.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class Parser  
    {  
         private IList<TextSpan[]> m_braces;  
         public IList<TextSpan[]> Braces  
         {  
             get { return m_braces; }  
         }  
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             if IsMatch(braceSpan1, braceSpan2)  
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });  
         }  
  
         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             //definition for matching here  
          }  
    }  
  
    public class TestLanguageService : LanguageService  
    {  
         Parser parser = new Parser();  
         Source source = (Source) this.GetSource(req.FileName);  
  
         private AuthoringScope ParseSource(ParseRequest req)  
         {  
             if (req.Sink.BraceMatching)  
             {  
                 if (req.Reason==ParseReason.MatchBraces)  
                 {  
                     foreach (TextSpan[] brace in parser.Braces)  
                     {  
                         req.Sink.MatchPair(brace[0], brace[1], 1);  
                     }  
                 }  
             }  
             return new TestAuthoringScope();  
         }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)