---
title: Analizatora usługi starszej wersji języka i skanera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52fb199af53d0fbbf30c0ae0dc6a2ad7083e4971
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234650"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analizator i skaner starszej wersji usługi językowej
Analizator jest Puls usługi języka. Klasy języka zarządzane pakietu Framework (MPF) wymagają analizatora składni języka aby wybrać informacji na temat kodu będzie wyświetlany. Analizator oddziela tekst w tokenach leksykalne, a następnie identyfikuje tokeny te według typu i funkcjonalność.  
  
## <a name="discussion"></a>Omówienie  
 Oto metoda C#.  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 W tym przykładzie tokeny są słów i znaków interpunkcyjnych. Dostępne są następujące typy tokenów.  
  
|Nazwa tokenu|Typ tokenu|  
|----------------|----------------|  
|przestrzeń nazw, klasy, public void, int|Słowo kluczowe|  
|=|operator|  
|{ } ( ) ;|Ogranicznik|  
|MyNamespace, MyClass, MyFunction, arg1, var1|identyfikator|  
|MyNamespace|— przestrzeń nazw|  
|MyClass|class|  
|MyFunction|— metoda|  
|arg1|parametr|  
|var1|Zmienna lokalna|  
  
 Rola Analizator jest do identyfikowania tokenów. Niektóre tokenów może mieć więcej niż jednego typu. Po analizator zidentyfikował tokenów, usługa języka można użyć informacji w ramach zapewnienia przydatne funkcje, takie jak wyróżnianie składni, nawiasy dopasowania i operacje IntelliSense.  
  
## <a name="types-of-parsers"></a>Typy analizatory składni  
 Analizatora usługa języka nie jest taka sama jak analizator używany jako część kompilatora. Jednak tego rodzaju analizator powinna być używana zarówno skaner i analizatora składni, w taki sam sposób jak analizator kompilatora.  
  
-   Skaner służy do identyfikowania typy tokenów. Te informacje są używane dla wyróżnianie składni i szybko zidentyfikować typy tokenów, mogą one powodować inne operacje, na przykład parowanie nawiasów klamrowych. Ten skaner jest reprezentowana przez <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu.  
  
-   Analizator jest używany do opisu funkcje i zakres tokenów. Te informacje jest używany podczas operacji IntelliSense, aby zidentyfikować elementy języka, takie jak metod, zmiennych, parametry i deklaracje oraz zapewnienie list elementów członkowskich i podpisy metod na podstawie kontekstu. Ten parser jest również używana do lokalizowania pasującego elementu kierunki, takich jak nawiasy i nawiasy. Ten parser jest dostępny za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.  
  
 Jak zaimplementować skanera i analizatora usługi języka zależy od użytkownika. Dostępnych jest kilka zasobów opisują sposób działania analizatory składni i jak napisać własny analizator składni. Ponadto są dostępne kilka produktów bezpłatne i komercyjne ułatwiające tworzenie analizatora składni.  
  
### <a name="the-parsesource-parser"></a>Analizator ParseSource  
 W przeciwieństwie do analizatora, które jest używane jako część kompilatora (gdzie tokeny są konwertowane na niektórych formą kodu wykonywalnego) można wywołać analizatora usługi języka wiele różnych powodów i w wielu różnych kontekstach. Jak wdrożyć to rozwiązanie w <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy zależy od użytkownika. Należy pamiętać, że <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda może być wywoływana wątku w tle.  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktura zawiera odwołanie do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu. To <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nie można użyć obiektu w wątku w tle. W rzeczywistości wiele klas podstawowych MPF nie można używać w wątku w tle. Obejmują one <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> klasy i inną klasę, która bezpośrednio lub pośrednio komunikuje się z widoku.  
  
 Ten parser zwykle analizuje czasu pliku pierwszy całego źródła, jest ona wywoływana lub podczas analizy przyczyny wartość <xref:Microsoft.VisualStudio.Package.ParseReason> podano. Kolejne wywołania <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody obsługi niewielką częścią analizowanej kodu i mogą być wykonywane znacznie szybciej przy użyciu wyniki poprzedniej operacji pełnej analizy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metody komunikuje się wyniki analizy operacji za pośrednictwem <xref:Microsoft.VisualStudio.Package.AuthoringSink> i <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektów. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Obiekt jest używany do gromadzenia informacji dla analizy powód, na przykład informacje o obejmuje zgodnych nawiasów klamrowych lub podpisy metod, które mają listy parametrów. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Zawiera kolekcje deklaracje i podpisy metod, a także obsługę przejdź do zaawansowanych opcji Edytuj (**przejdź do definicji**, **przejdź do deklaracji**, **przejdź do Odwołanie**).  
  
### <a name="the-iscanner-scanner"></a>Skaner IScanner  
 Skaner, który implementuje musi implementować też <xref:Microsoft.VisualStudio.Package.IScanner>. Jednakże ponieważ ten skaner działa na zasadzie wiersz po wierszu za pośrednictwem <xref:Microsoft.VisualStudio.Package.Colorizer> klasa, jest zazwyczaj łatwiejsze do wdrożenia. Na początku każdego wiersza daje MPF <xref:Microsoft.VisualStudio.Package.Colorizer> wartość do użycia jako zmiennej stanu, który jest przekazywany do skanera klasy. Na koniec każdego wiersza skanera zwraca zmiennej zaktualizowany stan. MPF buforuje tych informacji o stanie dla każdego wiersza, tak, aby uruchomić skanera analizowania z dowolnego wiersza bez konieczności uruchamiania na początku pliku źródłowego. Szybkie skanowanie pojedynczej linii umożliwia szybkie reagowanie użytkownika w edytorze.  
  
## <a name="parsing-for-matching-braces"></a>Analiza kodu dla pasujących nawiasów klamrowych  
 Ten przykład przedstawia przepływu sterowania do dopasowania zamykający nawias klamrowy, wpisanego przez użytkownika. W tym procesie skanera, który jest używany do kolorowania umożliwia również określić typ tokenu i określa, czy token może wyzwolić operacji nawiasu klamrowego dopasowania. Jeśli zostanie znaleziony wyzwalacza, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda jest wywoływana można odnaleźć pasującego nawiasu klamrowego. Na koniec dwa nawiasy klamrowe są wyróżnione.  
  
 Mimo że nawiasy klamrowe są używane w nazwach wyzwalaczy i analiza przyczyn, ten proces nie jest ograniczony do rzeczywistego nawiasów klamrowych. Pary znaków, określonym jako pary pasujących jest obsługiwana. Przykłady obejmują (a), \< i >, a [i].  
  
 Załóżmy, że usługa języka obsługuje pasujących nawiasów klamrowych.  
  
1.  Użytkownik wpisuje zamykający nawias klamrowy (}).  
  
2.  Nawias klamrowy zostanie wstawiony wskazywanej przez kursor w pliku źródłowym i kursor jest zaawansowane o jeden.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metoda <xref:Microsoft.VisualStudio.Package.Source> klasy jest wywoływana z typu zamykający nawias klamrowy.  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metoda <xref:Microsoft.VisualStudio.Package.Source> klasy, aby uzyskać token na pozycji tuż przed aktualną pozycją kursora. Token ten odnosi się do typu zamykający nawias klamrowy).  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metoda <xref:Microsoft.VisualStudio.Package.Colorizer> obiekt, aby uzyskać wszystkie tokeny w bieżącym wierszu.  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metoda <xref:Microsoft.VisualStudio.Package.IScanner> obiekt z tekstem bieżącego wiersza.  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Wielokrotnie wywołuje metodę <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metoda <xref:Microsoft.VisualStudio.Package.IScanner> obiektu na potrzeby zbierania wszystkich tokenów z bieżącego wiersza.  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Metoda wywołuje metodę prywatnych <xref:Microsoft.VisualStudio.Package.Source> klasy można uzyskać tokenu, który zawiera odpowiednią pozycję, a następnie przekazuje listy tokenów uzyskane z <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metody.  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metoda szuka flagą tokenu wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> w tokenie, która jest zwracana z <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metody; oznacza to, że token, który reprezentuje zamykający nawias klamrowy).  
  
6.  Jeśli wyzwalacz flagę <xref:Microsoft.VisualStudio.Package.TokenTriggers> zostanie znaleziony, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metoda <xref:Microsoft.VisualStudio.Package.Source> nosi nazwę klasy.  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> — Metoda rozpoczyna się operacja związana z wartością Przyczyna analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Ta operacja ostatecznie wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Jeśli przetwarzania asynchronicznego jest włączone, to wywołanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody występuje wątku w tle.  
  
8.  Po zakończeniu operacji analizy, program obsługi uzupełniania wewnętrzny (znanej także jako metoda wywołania zwrotnego) o nazwie `HandleMatchBracesResponse` jest wywoływana <xref:Microsoft.VisualStudio.Package.Source> klasy. To wywołanie automatycznie przez <xref:Microsoft.VisualStudio.Package.LanguageService> podstawowa klasa, nie przez analizatora.  
  
9. `HandleMatchBracesResponse` Metoda uzyskuje listę zakresów z <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiekt, który jest przechowywany w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu. (Zakres jest <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struktury, która określa zakres wierszy i znaków w pliku źródłowym.) Ta lista obejmuje zazwyczaj zawiera dwa zakresy, jeden dla otwarcia i zamknięcia nawiasów klamrowych.  
  
10. `HandleBracesResponse` Wywołania metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiekt, który jest przechowywany w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu. Ten rezultat podkreśla danego zakresów.  
  
11. Jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences> właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> jest włączona, `HandleBracesResponse` metoda uzyskuje tekst, który ujęty przez dopasowania zakresu i wyświetla 80 pierwszych znaków z tego zakresu na pasku stanu. To działa najlepiej, jeśli <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda zawiera element języka, dołączony pasującą parę. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> właściwości.  
  
12. Gotowe.  
  
### <a name="summary"></a>Podsumowanie  
 Zgodna operacja nawiasów klamrowych jest zazwyczaj ograniczone do prostych pary elementy języka. Bardziej złożonych elementów, takich jak dopasowania triples ("`if(...)`","`{`"i"`}`", lub "`else`","`{`"i"`}`"), można było wyróżnić w ramach operacji zakończenia programu word. Na przykład po zakończeniu "else" word, dopasowywania "`if`" może być wyróżniony instrukcji. Jeśli wystąpiły szereg `if` / `else if` instrukcje, na wszystkich z nich można wyróżnione przy użyciu ten sam mechanizm pasujących nawiasów klamrowych. <xref:Microsoft.VisualStudio.Package.Source> Klasy podstawowej już obsługuje tę funkcję, w następujący sposób: skaner musi zwracać wartość tokenu wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> połączeniu z wartością wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> dla tokenu, który jest wcześniejsza od bieżącej pozycji kursora.  
  
 Aby uzyskać więcej informacji, zobacz [dopasowywanie nawias klamrowy w starsza wersja usługi języka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Podczas analizowania kolorowania  
 Kolorowanie kod źródłowy jest proste, po prostu identyfikowania typ tokenu i zwracany koloru informacje o danym typie. <xref:Microsoft.VisualStudio.Package.Colorizer> Klasa działa jako pośrednik między edytorze i skanera zapewnienie kolor informacji o każdym tokenu. <xref:Microsoft.VisualStudio.Package.Colorizer> Klasy używa <xref:Microsoft.VisualStudio.Package.IScanner> obiektu pomoc w wierszu kolorowanie i zbierać informacje o stanie dla wszystkich wierszy w pliku źródłowym. W klasach usługi języka MPF <xref:Microsoft.VisualStudio.Package.Colorizer> klasa nie ma do zastąpienia, ponieważ komunikuje się ona z skanera tylko za pomocą <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu. Podaj obiekt, który implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu przez zastąpienie <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> Skanera znajduje się wiersz kodu źródłowego za pomocą <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metody. Wywołuje się <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metody są powtarzane uzyskanie następnego tokenu, w wierszu wyczerpania wiersza tokenów. Kolorowania MPF traktuje wszystkie kodu źródłowego za pomocą sekwencji wierszy. W związku z tym skaner musi być w stanie poradzić sobie ze źródłem przesyłanych go jako wiersze. Ponadto wiersza mogą być przekazywane do skanera w dowolnym momencie, a tylko gwarancji jest, że skaner otrzyma zmiennej stanu z wiersza przed wierszem o do skanowania.  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> Klasy również służy do identyfikowania wyzwalaczy tokenu. Te wyzwalacze Poinformuj MPF token określonego zainicjować bardziej złożonych operacji, takich jak word zakończenia lub pasujących nawiasów klamrowych. Ponieważ zidentyfikowanie tych wyzwalaczy musi być szybkie i musi występować w dowolnym miejscu, skaner jest najbardziej odpowiednie dla tego zadania.  
  
 Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starsza wersja usługi języka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Analiza kodu dla funkcji i zakres  
 Analiza kodu dla funkcji i zakres wymaga więcej niż tylko identyfikacji typów tokenów, które wystąpią. Analizator musi zidentyfikować nie tylko typ tokenu, ale także funkcje, dla której jest używany. Na przykład identyfikator jest po prostu nazwy, ale w określonym języku, identyfikator może być nazwa klasy, przestrzeń nazw, metody lub zmienną, w zależności od kontekstu. Ogólny typ tokenu może być identyfikatorem, ale identyfikator mogą także mieć inne znaczenie, w zależności od tego, co jest i w którym jest zdefiniowana. Ten identyfikator wymaga analizatora mają szerszej wiedzy na temat języka, które są analizowane. Jest to, gdy <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy jest dostarczany. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasy zbiera informacje o identyfikatory, metody pasującego kierunki (takie jak i nawiasów klamrowych) i triples języka (podobnie jak kierunki z tą różnicą, że istnieją trzy elementy, na przykład "`foreach()`" "`{`"i"`}`"). Ponadto można zastąpić <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy do obsługi identyfikacji kodu, który jest używany w weryfikacji wczesnych punktów przerwania, aby debuger musi być załadowany, oraz **automatycznych** debugowania okna, które zawiera lokalne Parametry i zmienne automatycznie po program jest debugowany i wymaga analizatora do identyfikowania odpowiednie zmiennych lokalnych i parametrów, które prezentuje debugera.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Obiekt jest przekazywany do analizatora jako część <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu, a nowy <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiekt jest utworzony zawsze nowy <xref:Microsoft.VisualStudio.Package.ParseRequest> tworzony jest obiekt. Ponadto <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda musi zwracać <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu, który jest używany do obsługi różnych operacji IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Obiekt przechowuje listę dla deklaracji i listy dla metod, albo którego zostanie wypełnione, w zależności od przyczyny analizy. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasy musi być implementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Omówienie usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-overview.md)   
 [Kolorowanie składni w starsza wersja usługi języka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)