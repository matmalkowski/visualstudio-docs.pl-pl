---
title: "Generowanie testów jednostek dla kodu za pomocą IntelliTest | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 2015-10-05
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.UnitTest.CreateIntelliTest
ms.assetid: cd9ff940-e948-4d28-a72c-b291ef5c1e90
caps.latest.revision: "33"
ms.author: douge
manager: douge
ms.openlocfilehash: 533e1938e83a7d4dccc3be4d8847967ee7c91f6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Generowanie testów jednostek dla kodu za pomocą IntelliTest
IntelliTest Eksploruje kodu .NET do generowania danych testowych i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie, jest generowany wprowadzania testu który wykona tej instrukcji. Analizy przypadków jest wykonywane dla każdego gałąź warunkowa w kodzie. Na przykład `if` instrukcje, potwierdzeń i wszystkie operacje, które można zgłaszają wyjątki są analizowane. Analiza jest używany do generowania danych testowych dla sparametryzowanego testu jednostkowego dla każdej z metod tworzenia testów jednostkowych z pokryciem kodu wysoki.  
  
 Po uruchomieniu IntelliTest, można łatwo Zobacz które testy kończą się niepowodzeniem i Dodaj wszelkie niezbędne kod, aby je naprawić. Można wybrać, które wygenerowane testy do zapisania do projektu testowego, aby zapewnić mechanizm regresji. Jak zmienić swój kod, należy ponownie uruchomić IntelliTest, aby zachować synchronizację ze zmianami kodu wygenerowane testy.  

## <a name="availability-and-extensions"></a>Dostępność i rozszerzenia

**Utworzyć IntelliTest** i **Uruchom program IntelliTest** polecenia menu:

* Są dostępne w tylko Enterprise Edition dla programu Visual Studio 2015 i nowszym.

* Obsługuje tylko kodu C# przeznaczonego dla programu .NET Framework.

* Są [extensible](#extend-framework)i obsługuje emisji testów w MSTest, MSTest V2, NUnit, xUnit format.
  
* Nie obsługują x64 konfiguracji.  
  
## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Zapoznaj się z: IntelliTest używany do eksplorowania kodu i generowania testów jednostkowych  
 Do generowania testów jednostkowych, Twoje typy muszą być publiczne. W przeciwnym razie [tworzenia testów jednostkowych](#NoRun) pierwszy przed wygenerowaniem je.  
  
1.  Otwórz rozwiązanie w programie Visual Studio. Następnie otwórz plik klasy, który ma metodę, którą chcesz przetestować.  
  
2.  Kliknij prawym przyciskiem myszy w metodzie w kodzie i wybierz polecenie **Uruchom program IntelliTest** do generowania testów jednostkowych dla kodu w metodę.  
  
     ![Prawo &#45; kliknij w metodę do generowania testów jednostkowych](../test/media/runpex.png "RunPEX")  
  
     IntelliTest uruchamia kod wiele razy z różnych danych wejściowych. Każdym uruchomieniu jest reprezentowana w Tabela zawierająca dane wejściowe testu i wynikowe dane wyjściowe lub wyjątku.  
  
     ![Za pomocą testów zostanie wyświetlone okno wyników eksploracji](../test/media/pexexplorationresults.png "PEXExplorationResults")  
  
     Do generowania testów jednostkowych dla wszystkich publicznych metod w klasie, po prostu kliknij prawym przyciskiem myszy w klasie, a nie w określonej metody. Następnie wybierz pozycję **Uruchom program IntelliTest**. W oknie wyników eksploracji można użyć listy rozwijanej, aby wyświetlić testy jednostkowe i dane wejściowe dla każdej metody w klasie.  
  
     ![Wybierz wyników testu do wyświetlenia na liście](../test/media/selectpextest.png "SelectPEXTest")  
  
     Dla testów, które są zaliczone, sprawdź, czy zgłoszony wyników w kolumnie wynik odpowiada oczekiwania dotyczące kodu. Dla testów, które się nie powieść Usuń kod zależnie od potrzeb. Następnie ponownie uruchom program IntelliTest można sprawdzić poprawności poprawki.  
  
## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Utrwalanie: Zapisz testów jednostkowych jako mechanizm regresji  
  
1.  Wybierz wiersze danych, które chcesz zapisać z sparametryzowanego testu jednostkowego do projektu testowego.  
  
     ![Wybierz testy; prawo &#45; kliknij przycisk i wybierz polecenie Zapisz](../test/media/savepextests.png "SavePEXTests")  
  
     Możesz wyświetlić projekt testowy i sparametryzowanego testu jednostkowego, który został utworzony — testy pojedynczą jednostkę, odpowiadającego poszczególnym wierszy, są zapisywane w. plik g.cs projektu testowego i sparametryzowanego testu jednostkowego jest zapisywany w pliku CS. Można uruchomić testów jednostkowych i wyświetlić wyniki z Eksploratora testów, tak jak w przypadku wszystkie testy jednostek, które zostały utworzone ręcznie.  
  
     ![Klasa Otwórz plik w metodzie testowej, aby wyświetlić testu jednostkowego](../test/media/testmethodpex.png "TestMethodPEX")  
  
     Wszystkie niezbędne odwołania są także dodawane do projektu testowego.  
  
     W przypadku zmiany kodu metody, należy ponownie uruchomić IntelliTest, aby zachować synchronizację ze zmianami testów jednostkowych.  
  
## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Pomoc: Użyj IntelliTest do fokus Eksploracja kodu  
  
1.  Jeśli masz bardziej złożonego kodu IntelliTest pomaga z skupienie eksploracji kodu. Na przykład jeśli użytkownik ma metodę, która ma interfejs jako parametr, a istnieje więcej niż jedną klasę, która implementuje ten interfejs, IntelliTest umożliwia odnalezienie tych klas i zgłosi ostrzeżenie.  
  
     Wyświetl ostrzeżenia decyzji o tym, co chcesz zrobić.  
  
     ![Wyświetl ostrzeżenia](../test/media/pexviewwarning.png "PEXViewWarning")  
  
2.  Po zbadać kod i zrozumieć, jakie mają zostać przetestowane, można naprawić ostrzeżenie, aby wybrać klasy przetestować interfejs.  
  
     ![Prawo &#45; kliknij ostrzeżenia i wybierz opcję Napraw](../test/media/pexfixwarning.png "PEXFixWarning")  
  
     Ten wybór jest dodawana do pliku PexAssemblyInfo.cs.  
  
     `[assembly: PexUseType(typeof(Camera))]`  
  
3.  Teraz możesz ponownie uruchomić program IntelliTest do generowania sparametryzowanego testu jednostkowego i przetestować danych tylko przy użyciu klasy, który został rozwiązany.  
  
     ![Ponownie uruchom program IntelliTest do generowania danych testowych](../test/media/pexwarningsfixed.png "PEXWarningsFixed")  
  
## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Określ: IntelliTest używany do sprawdzania poprawności właściwości określone w kodzie  

Określ ogólne relację między wejściach i wyjściach, które mają wygenerowane testy jednostkowe można sprawdzić poprawności. Określenie tej wartości są umieszczane w metodę, która wygląda jak metody testowej, ale jest powszechnie wyliczone. Jest to metoda test sparametryzowany jednostki i potwierdzeń, wszelkie wprowadzone muszą spełniać wszystkie możliwe wartości wejściowej, które mogą generować IntelliTest.  
  
##  <a name="QandALink"></a>FUNKCJA PYTANIA I ODPOWIEDZI  
  
### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Pytanie: czy można użyć IntelliTest dla niezarządzanego kodu?  

**Odpowiedź:** nie, IntelliTest działa tylko z kodu zarządzanego.  
  
### <a name="q-when-does-a-generated-test-pass-or-fail"></a>Pytanie: kiedy wygenerowany test zakończone powodzeniem lub niepowodzeniem?  

**Odpowiedź:** przekazaniem tak jak inne jednostki testu, jeśli wystąpią żadne wyjątki. Jej nie powiedzie się, czy wszystkie potwierdzenie nie powiedzie się, czy testowanego kodu zgłasza nieobsługiwany wyjątek.  
  
 Jeśli masz testu, jaki może upłynąć, jeśli pewne wyjątki są zgłaszane, możesz ustawić jedną z następujących atrybutów, w zależności od wymagań w metodzie testowej, klasy testowej lub zestawu poziomu:  
  
-   **PexAllowedExceptionAttribute**  
  
-   **PexAllowedExceptionFromTypeAttribute**  
  
-   **PexAllowedExceptionFromTypeUnderTestAttribute**  
  
-   **PexAllowedExceptionFromAssemblyAttribute**  
  
### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Pytanie: czy mogę dodać założenia do sparametryzowanego testu jednostkowego?  

**Odpowiedź:** tak, użyj założenia, aby określić, które dane testowe nie jest wymagana dla testu jednostkowego dla określonej metody. Użyj <xref:Microsoft.Pex.Framework.PexAssume> klasa do dodania założeń. Na przykład można dodać założenie, że zmiennej długości nie jest zerowa następująco.  
  
 `PexAssume.IsNotNull(lengths);`  
  
 Jeśli możesz dodać założenie i ponownie uruchom program IntelliTest danych testowych, który jest już nieaktualny zostaną usunięte.  
  
### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Pytanie: czy można dodać potwierdzenia do sparametryzowanego testu jednostkowego?  

**Odpowiedź:** tak, program IntelliTest zostanie Sprawdź, czy co użytkownik zostanie w instrukcji jest w rzeczywistości poprawne po uruchomieniu testów jednostkowych. Użyj <xref:Microsoft.Pex.Framework.PexAssert> klasy lub potwierdzenia interfejs API, który jest dostarczany z struktury testowej, można dodać potwierdzenia. Na przykład można dodać potwierdzenia, że dwie zmienne są takie same.  
  
 `PexAssert.AreEqual(a, b);`  
  
 Jeśli dodawanie potwierdzenie, a następnie ponownie uruchom program IntelliTest, sprawdza czy Twoje potwierdzenia jest prawidłowa i test zakończy się niepowodzeniem, jeśli nie jest.  
  
###  <a name="NoRun"></a>Pytanie: czy mogę wygenerować sparametryzowanych testów jednostkowych bez uruchamiania IntelliTest najpierw?  

**Odpowiedź:** tak, kliknij prawym przyciskiem myszy, klasa lub metoda, a następnie wybierz **utworzyć IntelliTest**.  
  
 ![Prawo &#45; kliknij przycisk Edytor, wybierz polecenie Utwórz IntelliTest](../test/media/pexcreateintellitest.png "PEXCreateIntelliTest")  
  
 Zaakceptuj domyślny format generowania testów, lub zmienić sposób nazywania projekt i testy. Można utworzyć nowy projekt testowy, lub zapisać testów do istniejącego projektu.  
  
 ![Utwórz program IntelliTest z domyślnymi MSTest](../test/media/pexcreateintellitestmstest.png "PEXCreateIntelliTestMSTest")  

<a name="extend-framework"></a>  
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Pytanie: czy można użyć innych platform testów jednostkowych z IntelliTest?  

**Odpowiedź:** tak, wykonaj następujące kroki, aby [znajdować i instalować innych platform,](../test/install-third-party-unit-test-frameworks.md).
Test framework rozszerzenia są także dostępne w programie Visual Studio Marketplace:

* [Rozszerzenie NUnit generatory testu](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Rozszerzenie xUnit.net generatory testu](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)


Po ponownym uruchomieniu programu Visual Studio i ponownie otwórz rozwiązanie, kliknij prawym przyciskiem myszy, klasa lub metoda, a następnie wybierz pozycję **utworzyć IntelliTest**. Wybierz framework zainstalowanych w tym miejscu:  
  
![Wybierz inne frameworka testów jednostkowych dla IntelliTest](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")  
  
Następnie uruchom program IntelliTest do generowania testów jednostkowych poszczególnych w odpowiednie. g.cs plików.  

  
### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Pytanie: czy można dowiedzieć się więcej na temat sposobu generowania testów?  

**Odpowiedź:** tak, aby uzyskać ogólne omówienie przeczytać ten tekst [wpis w blogu](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx).
