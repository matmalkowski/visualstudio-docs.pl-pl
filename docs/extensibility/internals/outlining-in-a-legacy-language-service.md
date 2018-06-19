---
title: Konspekt w starsza wersja usługi języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b899f53ba6b2a0b58997cc51a83a0d9ca8480e63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135655"
---
# <a name="outlining-in-a-legacy-language-service"></a>Konspekt w starsza wersja usługi języka
Tworzenie konspektu umożliwia zwijane złożony program Przegląd lub konspektu. Na przykład w języku C# wszystkie metody może zostać zwinięty do jednej linii, pokazujący tylko sygnatura metody. Ponadto aby wyświetlić tylko nazwy struktur i klas może zostać zwinięty struktury i klasy. Wewnątrz jednej metody może zostać zwinięty złożonej logiki, aby pokazać ogólny przepływ poprzez wyświetlenie tylko pierwszego wiersza instrukcji takich jak `foreach`, `if`, i `while`.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [wskazówki: Tworzenie konspektu](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="enabling-support-for-outlining"></a>Włączanie obsługi Tworzenie konspektu  
 `AutoOutlining` Wpis rejestru jest ustawiona na 1, aby włączyć automatyczne zwijanie. Automatyczne zwijanie konfiguruje analizy całego źródła podczas ładowania pliku lub zmienione w celu identyfikowania regionów ukryte i nie wyświetlaj zwijania symboli. Tworzenie konspektu można również sterować ręcznie przez użytkownika.  
  
 Wartość `AutoOutlining` wpis rejestru można uzyskać za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. `AutoOutlining` Wpis rejestru mogą być inicjowane z nazwanym parametrem <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu (patrz [zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md) szczegółowe informacje).  
  
## <a name="the-hidden-region"></a>Ukryte regionu  
 Aby zapewnić zwijania, usługi języka musi obsługiwać ukryte obszary. Są to obejmuje tekst, który może zostać rozwinięte lub zwinięte. Ukryte obszary mogą być rozdzielane przy symbole standard języka, takich jak nawiasy klamrowe, za pomocą niestandardowych symboli. Na przykład C# ma `#region` / `#endregion` pary ograniczającego ukryte regionu.  
  
 Ukryte obszary są zarządzane przez Menedżera ukryte regionu, która jest ujawniona jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfejsu.  
  
 Tworzenie konspektu używa ukryte obszary <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interfejsu i zawierać zakres ukryte regionu, bieżący stan widoczne i transparent ma być wyświetlany, gdy zakres jest zwinięty.  
  
 Używa analizatora usługi języka <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodę, aby dodać nowy region ukrytych z domyślnym zachowaniem ukryte obszary podczas <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metody umożliwia dostosowanie wyglądu i zachowania konturu. Po ukryte obszary podano do sesji ukryte region [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zarządza ukryte obszary usługi języka.  
  
 Należy określić podczas sesji ukryte regionu zostanie zniszczony, ukryte regionu zostanie zmieniona, czy należy upewnić się, że określonym regionie ukryte jest widoczny; musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.Source> klasy i zastąpić odpowiedniej metody, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, i <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>odpowiednio.  
  
### <a name="example"></a>Przykład  
 Oto uproszczony przykład tworzenia ukryte obszary dla wszystkich par nawiasów klamrowych. Zakłada się, że język zapewnia parowanie nawiasów klamrowych, i nawiasy klamrowe mają być dopasowywane zawiera co najmniej nawiasy klamrowe ({i}). Ta metoda jest tylko w celach ilustracyjnych. Pełnej implementacji byłyby pełną obsługę przypadków w <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. W tym przykładzie przedstawiono również sposób ustawiania <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferencję `true` tymczasowo. Alternatywą jest określenie `AutoOutlining` nazwany parametr w `ProvideLanguageServiceAttribute` atrybut do pakietu języka.  
  
 W tym przykładzie przyjęto założenie, C# zasady komentarze, ciągi i literały.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)