---
title: "Dynamiczne wykonywania symboliczne | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Dynamic symbolic execution
ms.assetid: B938E2D2-7B7C-4D76-B26C-2616F5B4A9F5
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 89754f6b66de78b4ff3fb9c80cf9eb3dfab7cfac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="input-generatation-using-dynamic-symbolic-execution"></a>Dane wejściowe generatation przy użyciu dynamicznych symboliczne wykonywania

Dane wejściowe generuje IntelliTest [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) analizując warunków gałęzi w programie. Dane wejściowe testu są wybierane w zależności od tego, czy mogą wyzwalać nowe rozgałęziania zachowania programu. Analiza jest procesem przyrostowe. Udoskonalanie predykat **q: I -> {true, false}** za pośrednictwem formalnych test parametrów wejściowych **I**. **q** reprezentuje zestaw zachowań, które już obserwował IntelliTest. Początkowo **q: = false**, ponieważ nie ma jeszcze przestrzegane.

Kroki pętli są:

1. Określa dane wejściowe, IntelliTest **i** tak, aby **q (i) = false** przy użyciu [moduł rozwiązywania ograniczeń](#constraint-solver). 
   W konstrukcji, dane wejściowe **i** potrwa ścieżka wykonywania nie zauważony. Oznacza to, że początkowo **i** może być żadnych danych, ponieważ nie ma ścieżki wykonanie jeszcze nie stwierdzono.

1. IntelliTest wykonuje test z nim wejściowych **i**i monitoruje wykonywania testu i programu w ramach testu.

1. Podczas wykonywania program pobiera określonej ścieżki, która jest określana przez rozgałęzień warunkowych programu. Zestaw wszystkie warunki, które określają wykonywania jest nazywany *warunku ścieżki*, zapisany jako predykat **p: I -> {true, false}** za pośrednictwem formalnych parametrów wejściowych. IntelliTest oblicza reprezentacja tego predykatu.

1. Ustawia IntelliTest **q: = (q lub p)**. Innymi słowy, rejestruje fakt, że znalazła ścieżki reprezentowanej przez **p**.

1. Przejdź do kroku 1.

IntelliTest w [moduł rozwiązywania ograniczeń](#constraint-solver) może uwzględniać wartości wszystkich typów, które mogą zostać wyświetlone programy .NET:

* [Liczby całkowite](#integers-and-floats) i [przesunięty](#integers-and-floats)
* [Obiekty](#objects)
* [Struktury](#structs)
* [Tablice](#arrays-and-strings) i [ciągów](#arrays-and-strings)

IntelliTest odfiltrowuje dane wejściowe naruszających podane założeń.

Oprócz natychmiastowego danych wejściowych (argumenty [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)), test może wykonywać Rysowanie dodatkowe wartości wejściowych z [PexChoose](static-helper-classes.md#pexchoose) klasy statycznej. Opcje również określają zachowanie [sparametryzowana mocks](#parameterized-mocks).

<a name="constraint-solver"></a>
## <a name="constraint-solver"></a>Moduł rozwiązywania ograniczeń

IntelliTest używa solver ograniczenie, aby określić odpowiednie wartości wejściowe testu i programu w ramach testu.

Używa IntelliTest [Z3](https://github.com/Z3Prover/z3/wiki) moduł rozwiązywania ograniczeń.

<a name="dynamic-code-coverage"></a>
## <a name="dynamic-code-coverage"></a>Pokrycie kodu dynamiczne

Jako efekt uboczny monitorowania środowiska uruchomieniowego IntelliTest zbiera dane pokrycia kodu dynamicznych. Ta metoda jest wywoływana *dynamiczne* ponieważ IntelliTest tylko zna kod, który zostało wykonane, w związku z tym go nie zapewniają wartości bezwzględne pokrycia w taki sam sposób jak inne narzędzia pokrycia zwykle. 

Na przykład, gdy IntelliTest zgłasza dynamicznego pokrycia jako 5/10 podstawowych bloków, oznacza to, że pięć bloków z 10 były objęte, gdzie całkowita liczba bloków w wszystkie metody, które zostały osiągnięte w do tej pory przez analizy (w przeciwieństwie do wszystkich metod, które istnieją w ssembly w ramach testu) wynosi 10.
Nowsze do analizy, więcej metod dostępne są odnajdywane licznik (5 w tym eaxmple) i może zwiększyć denominator (10).

<a name="integers-and-floats"></a>
## <a name="integers-and-floats"></a>Liczby całkowite i elementów przestawnych

IntelliTest w [moduł rozwiązywania ograniczeń](#constraint-solver) określa wartości wejściowe testu typów podstawowych, takich jak **bajtów**, **int**, **float**, a inne w Aby wyzwolić wykonywanie różnych ścieżki testu i program w ramach testu.

<a name="objects"></a>
## <a name="objects"></a>Obiekty

IntelliTest można albo [tworzenia wystąpień istniejących klas .NET](#existing-classes), lub skorzystać z IntelliTest, aby automatycznie [Tworzenie obiektów zasymulować](#parameterized-mocks) wykonania określonego interfejsu i zachowywać się na różne sposoby w zależności od użycia.

<a name="existing-classes"></a>
## <a name="instantiating-existing-classes"></a>Tworzenie wystąpień istniejących klas

**Co to jest problem?**

IntelliTest monitoruje instrukcje wykonywane po uruchomieniu testu i programów w ramach testu. W szczególności monitoruje dostęp do pola. Następnie używa [moduł rozwiązywania ograniczeń](#constraint-solver) ustalenie nowe dane wejściowe testu, łącznie z obiektów i ich wartości pola tak, aby testu i programów w ramach testu będzie się odbywać na inne ciekawe sposoby.

Oznacza to, że program IntelliTest muszą do utworzenia obiektów niektórych typów i ustawienia ich wartości pól. Jeśli klasa jest [widoczne](#visibility) i ma [widoczne](#visibility) domyślnego konstruktora IntelliTest można utworzyć wystąpienia klasy.
Jeśli wszystkie pola klasy [widoczne](#visibility), IntelliTest można ustawić pola automatycznie.

Typ nie jest widoczny, czy pola nie są [widoczne](#visibility), IntelliTest musi pomocy do tworzenia obiektów i ich dostosowania do stanów interesujące aby osiągnąć pokrycie kodu maksymalna. IntelliTest można używać odbicia do tworzenia i inicjowania wystąpienia w dowolny sposób, ale nie jest to zazwyczaj  
pożądane, ponieważ może on Przenieś obiekt w stan, który nigdy nie może wystąpić podczas normalnego działania programu. Zamiast tego program IntelliTest zależy od wskazówek z użytkownika.

<a name="visibility"></a>
## <a name="visibility"></a>Widoczność

.NET Framework ma rozbudowane widoczność modelu: typy, metody, pól i inne elementy Członkowskie mogą być **prywatnej**, **publicznego**, **wewnętrzny**i inne.

IntelliTest, generując testy, spróbuje wykonać tylko te akcje (takie jak wywołania konstruktorów, metod i ustawiania pól), które są w odniesieniu do reguły widoczności .NET z w kontekście wygenerowane testy.

Dostępne są następujące reguły:

* **Widoczność wewnętrzne elementy członkowskie**
  * IntelliTest przyjęto założenie, że generowane testy będą mieli dostęp do wewnętrznych elementów członkowskich, które były widoczne dla otaczający [PexClass](attribute-glossary.md#pexclass).
  Ma .NET **InternalsVisibleToAttribute** rozszerzenie widoczność członków wewnętrznych do innych zestawów.<p />

* **Widoczność prywatnych i członków rodziny (chroniony w C#) [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest zawsze umieszcza wygenerowane testy bezpośrednio w [PexClass](attribute-glossary.md#pexclass) lub do podklasy. W związku z tym IntelliTest zakłada, że może go używać wszyscy członkowie rodziny widoczne (**chronione** w języku C#).
  * Jeśli wygenerowane testy są umieszczane bezpośrednio w [PexClass](attribute-glossary.md#pexclass) (zazwyczaj za pomocą klasy częściowe) IntelliTest zakłada, że może również używać wszyscy członkowie prywatnego [PexClass](attribute-glossary.md#pexclass).<p />

* **Widoczność publiczne elementy członkowskie**
  * IntelliTest przyjęto założenie, że może używać wyeksportowane wszystkie elementy członkowskie, które są widoczne w kontekście [PexClass](attribute-glossary.md#pexclass).

<a name="parameterized-mocks"></a>
## <a name="parameterized-mocks"></a>Mocks sparametryzowane

Jak przetestować metodę, która ma parametr typu interfejsu? Lub klasą niezapieczętowaną? IntelliTest nie może określić, które implementacje później będzie używane, jeśli ta metoda jest wywoływana. I prawdopodobnie nie ma jeszcze rzeczywistego wykonania dostępne w czasie testu.

Odpowiedź z konwencjonalnej jest użycie *mock obiektów* z jawnym zachowanie. 

Obiekt zasymulować implementuje interfejs (lub rozszerza klasę niezapieczętowaną). Reprezentuje rzeczywistą implementacji, ale tylko skrótu klawiaturowego, który zezwala na wykonywanie testów za pomocą zasymulować obiektu. Jego zachowanie jest definiowane ręcznie w ramach każdego przypadku testowego, w którym została użyta. Istnieją wielu narzędzi, które ułatwiają zdefiniuj zasymulować obiektów i ich zachowanie oczekiwane, ale nadal należy ręcznie zdefiniować to zachowanie.

Zamiast do zakodowanych wartości w obiektach zasymulować IntelliTest mogą generować wartości. Podobnie jak umożliwia [sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing), IntelliTest umożliwia również mMocks sparametryzowana.

Sparametryzowane mocks mają dwa tryby wykonywania różnych:

* **Wybieranie**: podczas eksplorowania kodu, sparametryzowane mocks są źródłem dane wejściowe testu dodatkowe i IntelliTest podejmie próbę wybierz interesujące wartości
* **powtarzania**: podczas wykonywania wcześniej wygenerowany test, mocks sparametryzowane przypominają klas zastępczych z zachowaniem (innymi słowy, wstępnie zdefiniowanych zachowanie).

Użyj [PexChoose](static-helper-classes.md#pexchoose) można uzyskać wartości sparametryzowane mocks.

<a name="structs"></a>
## <a name="structs"></a>Struktury

IntelliTest obiektu wnioskowania o **struktury** wartości jest podobny do sposobu zajmuje się [obiektów](#objects).

<a name="arrays-and-strings"></a>
## <a name="arrays-and-strings"></a>Tablice i ciągi

IntelliTest monitoruje instrukcje wykonywane podczas działania testu i programów w ramach testu. W szczególności przestrzega, gdy program jest zależny od długość ciągu lub tablicy (dolną i długości tablicy wielowymiarowej). Przestrzega również, jak program używa różnych elementów string lub array. Następnie używa [moduł rozwiązywania ograniczeń](#constraint-solver) do określenia, które długości i wartości elementu może spowodować testu i programów w ramach testu będzie działać w sposób.

IntelliTest próbuje zminimalizować rozmiar ciągi wymagany do wyzwolenia interesujące zachowania programu i tablic.

<a name="additional-inputs"></a>
## <a name="obtaining-additional-inputs"></a>Uzyskiwanie dodatkowych danych wejściowych

[PexChoose](static-helper-classes.md#pexchoose) klasy statycznej może zostać użyty do uzyskania dodatkowe dane wejściowe do testu i może służyć do zaimplementowania [sparametryzowana mocks](#parameterized-mocks).

<a name="further-reading"></a>
## <a name="further-reading"></a>Dalsze informacje

* [Jak to działa?](https://blogs.msdn.microsoft.com/visualstudioalm/2014/12/11/smart-unit-tests-a-mental-model/)

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
