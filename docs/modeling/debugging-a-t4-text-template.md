---
title: Debugowanie szablonu tekstowego T4 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: da101fa60d897a56c42b52ebbb8e0cc21a6d7a9f
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="debugging-a-t4-text-template"></a>Debugowanie szablonu tekstowego T4
Można ustawić punktów przerwania w szablonach tekstowych. Debugowanie szablonu tekstowego czasu projektowania, Zapisz plik tekstowy szablonu, a następnie wybierz **debugowania szablon T4** menu skrótów w pliku w Eksploratorze rozwiązań. Debugowanie szablonu tekstowego środowiska wykonawczego, po prostu debugowania aplikacji, do którego on należy.  
  
 Debugowanie szablonu tekstowego, należy zrozumieć kroki procesu transformacji szablonu. Różnego rodzaju błędów, może wystąpić w każdym kroku. Dostępne są następujące kroki.  
  
|Krok|Szablon czasu projektowania: gdy zdarza się to|Szablon środowiska wykonawczego: gdy zdarza się to|  
|----------|--------------------------------------------|-----------------------------------------|  
|Kod jest generowany na podstawie szablonu tekstowego.<br /><br /> Błędy w dyrektywach lub niezgodne lub disordered `<#...#>` tagów.|Podczas zapisywania szablonu lub wywoływanie transformacji tekstu.|Podczas zapisywania szablonu lub wywoływanie transformacji tekstu.|  
|Kompilowania wygenerowanego kodu.<br /><br /> Błędy kompilacji w kodzie szablonu.|Bezpośrednio po poprzednim kroku.|Wraz z kodu aplikacji.|  
|Kod jest uruchamiany.<br /><br /> Błędy środowiska wykonawczego w kodzie szablonu.|Bezpośrednio po poprzednim kroku.|Gdy aplikacja jest uruchamiana i wywołuje kod szablonu.|  
  
 W większości przypadków numery wierszy w kodzie szablonu są podane w raporcie o błędzie. Gdy raport o błędach odwołuje się do tymczasowej nazwy pliku, zwykle przyczyną jest to niezgodne nawiasu w kodzie szablonu tekstowego.  
  
 Można ustawić punktów przerwania w szablonach tekstowych i debugowania w zwykły sposób.  
  
## <a name="common-errors-and-fixes"></a>Typowe błędy i poprawki  
 W poniższej tabeli wymieniono typowe błędy i ich poprawki.  
  
|Komunikat o błędzie|Opis|Rozwiązanie|  
|-------------------|-----------------|--------------|  
|Nie można załadować klasy podstawowej "{0}" z dziedziczy która klasa Transformation.|Występuje, gdy nie można znaleźć klasy podstawowej określonej w `inherits` parametru w dyrektywie szablonu. Komunikat zawiera numer wiersza w dyrektywie template.|Upewnij się, określonej klasy istnieje i że zestaw, który istnieje w został określony w dyrektywie zestawu.|  
|Nie można rozpoznać tekstu dyrektywy include dla file:{0}|Występuje, gdy nie można odnaleźć szablonu uwzględnione. Komunikat zawiera nazwę pliku dołączanego żądanej.|Pamiętaj, że ścieżka pliku jest względem oryginalnego szablonu ścieżki, lub że plik jest w lokalizacji, która jest zarejestrowana na hoście lub jest pełna ścieżka do pliku.|  
|Wygenerowano błędy podczas inicjowania obiektu transformacji. Transformacja nie zostanie uruchomiona.|Występuje, gdy "Initialize()" klasy przekształcania nie powiodło się lub zwróciła wartość false.|Kod w funkcji Initialize() pochodzi z klasy podstawowej przekształcania określonej w \<#@template#> dyrektywy oraz procesory dyrektywy. Błąd, który spowodował zainicjować się prawdopodobnie niepowodzeniem znajduje się na liście błędów. Sprawdź, dlaczego nie powiodło się. Zapoznanie się z rzeczywistego wygenerowany kod dla Initialize() zgodnie z instrukcjami opisanymi debugowania szablonu.|  
|Zestaw "{0}" dla procesora dyrektywy "{1}" nie uzyskał zestawu uprawnień FullTrust. Tylko zaufane zestawy mogą dostarczać procesory dyrektywy. Procesor dyrektywy nie zostanie załadowany.|Występuje, gdy system nie powoduje przyznania uprawnień FullTrust do zestawu zawierającego procesora dyrektywy. Komunikat zawiera nazwę zestawu i nazwa procesora dyrektywy.|Należy upewnić się, że tylko zaufane zestawy na komputerze lokalnym.|  
|Ścieżka "{0}" musi być lokalną na tym komputerze lub częścią zaufanej strefy.|Występuje, gdy dyrektywy lub dyrektywa zestawu odwołuje się do pliku, który jest nie na komputerze lokalnym lub w sieci zaufanej strefy.|Upewnij się że katalogu, w którym dyrektywy lub dyrektywy zestawu znajdują się w strefie zaufanych. Można dodać katalogu sieciowego do zaufanej strefy za pomocą programu Internet Explorer.|  
|Wiele błędów składni, takich jak "Nieprawidłowy token" catch"" lub "przestrzeni nazw nie może bezpośrednio zawierać elementów członkowskich"|Zbyt wiele nawiasów klamrowych zamknięcia w kodzie szablonu. Kompilator jest skomplikowana go z standardowe generowania kodu.|Sprawdź numer zamykające nawiasy i nawiasy wewnątrz ograniczników kodu.|  
|Pętle lub warunków nie kompilacji lub wykonania poprawnie. Na przykład: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Ten kod zawsze wyświetla wartość i. Tylko "Liczba to:" jest warunkowego.|W języku C# należy zawsze używać nawiasów klamrowych otaczającego bloki tekstu, które są osadzone w instrukcji sterowania.|Dodaj nawiasy klamrowe: `<#if (i>10) { #>    Number is: <#= i #><# } #>`.|  
|"Wyrażenie jest zbyt złożone" podczas przetwarzania szablonu czasu projektowania lub skompilowanie szablonu środowiska uruchomieniowego (wstępnie przetworzonych).<br /><br /> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]przestaje działać podczas próby sprawdź kod wygenerowany przez szablon środowiska wykonawczego.|Blok tekstu jest zbyt długa. T4 konwertuje tekst bloki wyrażenie łączenia ciągu z jednego ciągu literału dla każdego wiersza szablonu. Bloki bardzo długi tekst można overstep limity rozmiaru kompilatora.|Podzielić bloku długi tekst blok wyrażenia, takich jak:<br /><br /> `<#= "" #>`|  
  
## <a name="warning-descriptions-and-fixes"></a>Ostrzeżenie opisy i poprawki  
 W poniższej tabeli wymieniono najczęściej ostrzeżenia wraz z poprawki, jeśli jest dostępna.  
  
|Komunikat ostrzegawczy|Opis|Rozwiązanie|  
|---------------------|-----------------|--------------|  
|Podczas ładowania pliku dołączanego "{0}" zwróciła wartość null lub pusty ciąg.|Występuje, gdy tekst dołączony plik szablonu jest pusty. Komunikat zawiera nazwę pliku dołączanego pliku.|Usuń dyrektywy include lub upewnij się, że plik ma zawartość.|  
|Kompilowanie transformacji:|Dołącza ten ciąg, aby wszystkie błędy lub ostrzeżenia, pochodzących z kompilatora podczas kompiluje transformacji. Ten ciąg oznacza, że kompilator zwrócił błąd lub ostrzeżenie.|Jeśli masz problem ze znalezieniem z biblioteką DLL może być konieczne Podaj pełną ścieżkę lub silnej nazwy FQDN, jeśli biblioteka znajduje się w pamięci GAC.|  
|Parametr "{0}" już istnieje w dyrektywie. Zduplikowany parametr zostanie zignorowany.|Występuje, gdy parametr jest określony więcej niż raz w dyrektywie. Komunikat zawiera nazwę parametru i numer wiersza dyrektywy.|Usuń specyfikację zduplikowany parametr.|  
|Wystąpił błąd podczas ładowania pliku dołączanego "{0}". Dyrektywa include zostaną zignorowane.|Występuje, gdy nie można odnaleźć pliku określonego w `include` dyrektywy. Komunikat zawiera nazwę pliku i numer wiersza dyrektywy.|Upewnij się, że istnieje dołączanego pliku, w tym samym katalogu co oryginalny plik szablonu tekstu lub w jednym z katalogów dołączania, które są zarejestrowane z hostem.|  
|Określono nieprawidłową klasę podstawową klasy transformacji. Klasa podstawowa musi pochodzić od element Microsoft.VisualStudio.TextTemplating.TextTransformation.|Występuje, gdy `inherits` parametru w dyrektywie szablonu określa klasę, która nie dziedziczy z `TextTransformation`. Komunikat zawiera numer wiersza w dyrektywie template.|Określ klasę pochodną `TextTransformation`.|  
|Określono nieprawidłową kulturę w dyrektywie "template". Kultura musi mieć format "xx-XX". Zostanie użyta Niezmienna kultura.|Występuje, gdy parametr kulturę w dyrektywie szablonu została określona nieprawidłowo. Komunikat zawiera numer wiersza w dyrektywie template.|Zmień parametr kultury prawidłową kulturą format "xx-XX".|  
|Nieprawidłową wartość debugowania "{0}" została określona w dyrektywie template. Wartość debugowania musi być "true" lub "false". Wartość domyślna "false" będą używane.|Występuje, gdy `debug` został niepoprawnie określony parametr w dyrektywie szablonu. Komunikat zawiera numer wiersza w dyrektywie template.|Ustaw parametr debugowania na "true" lub "false".|  
|Nieprawidłowa wartość HostSpecific "{0}" została określona w dyrektywie template. Wartość HostSpecific musi być "true" lub "false". Wartość domyślna "false" będą używane.|Występuje, gdy parametr specyficzne dla hosta w `template` dyrektywa została określona nieprawidłowo. Komunikat zawiera numer wiersza w dyrektywie template.|Ustaw dla parametru specyficzne dla hosta "prawda" lub "false".|  
|Nieprawidłowy język "{0}" została określona w dyrektywie "template". Język musi mieć wartość "C#" lub "VB". Zostanie użyta wartość domyślna "C#".|Występuje, gdy określono nieobsługiwany język w `template` dyrektywy. Tylko "C#" lub "VB" są dozwolone (bez uwzględniania wielkości liter). Komunikat zawiera numer wiersza w dyrektywie template.|Ustaw `language` parametru w dyrektywie template "C#" lub "VB".|  
|W szablonie znaleziono wiele dyrektyw danych wyjściowych. Wszystkie, oprócz pierwszej zostaną zignorowane.|Występuje, gdy wiele `output` dyrektywy zostały określone w pliku szablonu. Komunikat zawiera numer wiersza dyrektywy zduplikowany wyjściowy.|Usuń zduplikowane `output` dyrektywy.|  
|W szablonie znaleziono wiele dyrektyw szablonu. Wszystkie, oprócz pierwszej zostaną zignorowane. Wiele parametrów dyrektywy template należy określić w ramach jednej dyrektywy template.|Występuje w przypadku określenia wielu `template` dyrektywy w pliku szablonu tekstowego (w tym pliki dołączane). Komunikat zawiera numer wiersza dyrektywy duplikat szablonu.|Agreguj różnych `template` dyrektywy do jednego `template` dyrektywy.|  
|Nie określono procesora dla dyrektywy o nazwie "{0}". Dyrektywa zostanie zignorowana.|Występuje po określeniu `custom` dyrektywy, ale nie zapewniają `processor` atrybutu. Komunikat zawiera nazwę dyrektywy i numer wiersza.|Podaj `processor` atrybutu o nazwie `directive` procesora dla dyrektywy.|  
|Nie można odnaleźć procesora o nazwie "{0}" dla dyrektywy o nazwie "{1}". Dyrektywa zostanie zignorowana.|Występuje, gdy w systemie nie można odnaleźć `directive` procesora określona w `custom` dyrektywy. Komunikat zawiera nazwy dyrektywy, Nazwa procesora i numer wiersza dyrektywy.|Ustaw `processor` atrybutu w dyrektywie nazwę procesora dyrektywy.|  
|Nie znaleziono wymaganego parametru "{0}" dla dyrektywy "{1}". Dyrektywa zostanie zignorowana.|Występuje, gdy system nie ma wymaganego parametru dyrektywy. Komunikat zawiera nazwę brakującego parametru, dyrektywy nazwę i numer wiersza.|Podaj brakujący parametr.|  
|Procesor o nazwie "{0}" nie obsługuje dyrektywy o nazwie "{1}". Dyrektywa zostanie zignorowana.|Występuje, gdy procesor dyrektywy nie obsługuje dyrektywy. Komunikat zawiera nazwę i wiersz numer ataku dyrektywy wraz z nazwą procesora dyrektywy.|Popraw nazwę dyrektywy.|  
|Dyrektywa include dla pliku "{0}" powoduje nieskończoną pętlę.|Wyświetlane, gdy cykliczne zawiera dyrektywy, które są określone (na przykład pliku zawiera plik B, w tym pliku A).|Nie określaj cykliczne dyrektyw.|  
|Uruchamianie transformacji:|Dołącza ten ciąg, aby wszystkie błędy lub ostrzeżenia, które są generowane podczas wykonywania transformacji.|Nie dotyczy.|  
|Znaleziono nieoczekiwany tag początkowy lub końcowy w bloku. Upewnij się, że użytkownik został poprawnie wpisany tag początkowy lub końcowy i że nie masz żadnych zagnieżdżonych bloków w szablonie.|Wyświetlane, gdy użytkownik ma nieoczekiwany \<# lub #>. Oznacza to jeśli masz \<# po innym Otwórz tagu, który nie został zamknięty lub użytkownik ma #> gdy niezamknięty tag Otwórz przed nią nie istnieje. Komunikat zawiera numer wiersza niedopasowanych tagu.|Usuń niedopasowanych tag początkowy lub końcowy lub użyj znaku ucieczki.|  
|Dyrektywa został określona w niewłaściwym formacie. Dyrektywa zostanie zignorowana. Określ dyrektywę w formacie`<#@ name [parametername="parametervalue"]*  #>`|Wyświetlane przez parser, jeśli nie określono dyrektywę w poprawnym formacie. Komunikat zawiera dyrektywy niepoprawny numer wiersza.|Upewnij się, wszystkie dyrektywy są w formie `<#@ name [parametername="parametervalue"]*  #>`. Aby uzyskać więcej informacji, zobacz [dyrektywy szablonu tekstowego T4](../modeling/t4-text-template-directives.md).|  
|Nie można załadować zestawu "{0}" dla zarejestrowanego procesora dyrektywy "{1}"<br /><br /> {2}|Występuje, gdy nie można załadować procesora dyrektywy przez hosta. Komunikat identyfikuje zestawu udostępniane dla procesora dyrektywy i nazwę procesora dyrektywy.|Upewnij się procesora dyrektywy jest poprawnie zarejestrowana i czy zestaw istnieje.|  
|Nie można odnaleźć typu "{0}" w zestawie "{1}" dla zarejestrowanego procesora dyrektywy "{2}"<br /><br /> {3}|Występuje, gdy nie można załadować typu procesora dyrektywy z jej zestawu. Komunikat zawiera nazwę typu, zestawów i procesora dyrektywy.|Vshost umożliwia znalezienie informacji procesora dyrektywy (nazwa zestawu i typ) w rejestrze. Upewnij się, procesora dyrektywy jest poprawnie zarejestrowana i czy typ istnieje w zestawie.|  
|Wystąpił problem podczas ładowania zestawu "{0}"|Występuje, gdy występuje problem podczas ładowania zestawu. Komunikat zawiera nazwę zestawu.|Można określić zestawów, aby można było załadować \<@# assembly #> dyrektywy oraz procesory dyrektywy. Komunikat o błędzie, znajdujący się na ten ciąg powinien zawierać więcej danych na Dlaczego nie można załadować zestawu.|  
|Wystąpił problem podczas tworzenia i inicjowania procesora dla dyrektywy o nazwie "{1}". Typ procesora to {0}. Dyrektywa zostanie zignorowana.|Występuje, gdy system nie można utworzyć lub zainicjować procesora dyrektywy. Komunikat zawiera nazwę i wiersz numer dyrektywy i typ procesora.|Upewnij się, użycia procesora dyrektywy poprawne i że procesora dyrektywy ma publicznego konstruktora domyślnego. W przeciwnym razie użyj opcji debugowania, aby dowiedzieć się, dlaczego metodę Initialize() procesora dyrektywy kończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z szablonów tekstowych](../modeling/debugging-a-t4-text-template.md).|  
|Wystąpił wyjątek podczas przetwarzania dyrektywy o nazwie "{0}".|Występuje, gdy procesor dyrektywy zgłasza wyjątek podczas przetwarzania dyrektywy.|Pamiętaj, że parametry procesora dyrektywy są poprawne.|  
|Host zgłosił wyjątek podczas próby rozpoznania odwołania do zestawu "{0}".|Występuje, gdy host zgłasza wyjątek podczas próby rozpoznania odwołania do zestawu. Komunikat udostępnia zestaw odwołania ciągu.|Zestaw odwołania pochodzą z \<@# assembly #> dyrektywy i z procesory dyrektywy. Pamiętaj, że parametrowi 'name' podana w parametrze zestawu jest poprawna.|  
|Próba określenia wartości nieobsługiwanego {1} "{0}" dla dyrektywy {2}|Występuje za RequiresProvidesDirectiveProcessor, (wszystkie nasze wygenerowanego procesory dyrektywy pochodzić od niego), jeśli podasz nieobsługiwany wymaga lub zawiera argument.|Pamiętaj, że nazwy name = "wartość" par w wymaga i zawiera parametry są poprawne.|