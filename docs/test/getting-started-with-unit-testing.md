---
title: "Wprowadzenie do przeprowadzania testów jednostkowych — Tworzenie planów testów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit test plans
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e6789c3a8ddb9b0aa317df0d2362d39946069cbd
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="get-started-with-unit-testing"></a>Wprowadzenie do przeprowadzania testów jednostkowych

Definiowanie i Uruchamianie testów jednostek do obsługi kondycji kodu, upewnij się, pokrycie kodu, a także znalezienia błędów i błędy, zanim klienci za pomocą programu Visual Studio.

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>Tworzenie testów jednostkowych

Utwórz testy jednostkowe i uruchom je często, aby upewnić się, że kod działa prawidłowo.

1. Tworzenie projektu testu jednostki.
        
   ![Dodaj jednostkowy projekt testowy do rozwiązania](media/createunittest1.png)
    
1. Nazwa projektu.
        
   ![Szablon projektu testu jednostki](media/createunittest2.png)
  
   Projekt zostanie dodany do rozwiązania.
    
   ![Jednostkowy projekt testowy w Eksploratorze rozwiązań](media/createunittest5.png)
    
1. W jednostkowy projekt testowy Dodaj odwołanie do projektu, który ma zostać przetestowana.
        
   ![Dodaj odwołanie do projektu testu jednostki](media/createunittest6.png)
    
1. Wybierz projekt, który zawiera kod, który będzie testu.
        
   ![Wybierz odwołanie do dodania](media/createunittest7.png)
    
1. Kod testu jednostki.

   ![Dodaj kod, aby z testu jednostkowego](media/createunittest8.png) 

Można również utworzyć testu jednostkowego klas zastępczych metody z [ **tworzenia testów jednostkowych** polecenia](create-unit-tests-menu.md).
Lub użyć [frameworka testów jednostkowych różnych](#frameworks) do utworzenia testów dla kodu różnych języków.

![Za pomocą polecenia Create testy jednostkowe](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Uruchom testy jednostkowe

1. Otwórz Eksploratora testów.
        
   ![W menu Test Otwórz Eksplorator testów](media/rununittest1.png) 

1. Uruchom testy jednostkowe.
        
   ![Uruchom testy jednostkowe w narzędzia Eksplorator testów](media/rununittest2.png) 

   Można zauważyć, że jednostka testów, które przekazany lub Niepowodzenie w Eksploratorze testów.
      
   ![Przejrzyj wyniki testów jednostkowych w Eksploratorze testów](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>Wyświetlanie wyników testu jednostki na żywo

Jeśli używasz MSTest, xUnit lub NUnit testowania framework w programie Visual Studio 2017 lub nowszych widać na żywo wyniki testów jednostkowych w Interfejsie użytkownika programu Visual Studio.

1. Włącz testy z jednostkowe na żywo **testu** menu.

   ![Włącz testy jednostkowe na żywo](media/live-test-results-start.png) 

1. W oknie edytora kodu należy wyświetlić wyniki testów, jak zapisać i Edycja kodu.

   ![Wskaż i kliknij na wskaźnikach wyników testu](media/live-test-results-ui.png) 

1. Wskaż i kliknij na wskaźnikach wynik testu, aby uzyskać więcej informacji.

   ![Wyświetl wyniki testów](media/live-test-results-details.png) 

Aby uzyskać więcej informacji, zobacz [Live testów jednostkowych programu Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/).

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>Generowanie testów jednostkowych z IntelliTest

Po uruchomieniu IntelliTest, można łatwo Zobacz które testy kończą się niepowodzeniem i Dodaj wszelkie niezbędne kod, aby je naprawić. Można wybrać, które wygenerowane testy do zapisania do projektu testowego, aby zapewnić mechanizm regresji. Jak zmienić swój kod, należy ponownie uruchomić IntelliTest, aby zachować synchronizację ze zmianami kodu wygenerowane testy. Aby dowiedzieć się więcej, zobacz temat [Generowanie testów jednostek dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Generowanie testów jednostkowych z IntelliTest](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj Eksploratora testów do uruchamiania testów jednostkowych programu Visual Studio lub projektów testów jednostkowych innych firm, grupowanie testów w kategorii, filtrowanie listy testów i tworzenia, zapisywania i uruchom listy odtwarzania testów. Można również Debuguj testy i Analizuj pokrycie testu wydajności i kod. Aby dowiedzieć się więcej, zobacz temat [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md).

![Uruchamianie testów jednostkowych z Eksploratora testów](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Użyj pokrycie kodu, aby określić, ile kodu jest poddawana testom

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny obejmować lub pokrywać znaczną część kodu. Aby dowiedzieć się więcej, zobacz temat [pokrycia kodu używany do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

![Aby określić, ile kodu jest poddawana testom korzystanie z pokrycia kodu](media/codecoverage.png)

## <a name="q--a"></a>Pytania i odpowiedzi

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks"></a>
####Pytanie: czy można uruchamiać testów jednostkowych w programie Visual Studio użycie innej jednostki struktury testowej?

Odpowiedź: tak, użyj wtyczki dla tej platformy, że Visual Studio test runner może współpracować z tej struktury. Poniżej przedstawiono niektóre [testu jednostkowego wtyczek framework dla programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=246630).

1. Użyj Menedżera rozszerzeń programu Visual Studio można pobrać z wtyczki.
        
   ![Wybierz plug-in testów jednostkowych 3rd firm z Menedżera rozszerzeń](media/install3rdpartyunittestframeworks1.png) 

1. Pobierz z wtyczki z galerii programu Visual Studio w obszarze narzędzia/testowanie, lub wyszukaj go Jeśli znasz nazwę.
        
   ![Pobierz z wtyczki](media/install3rdpartyunittestframeworks2.png) 

1. Tworzenie projektu biblioteki klas.
        
   ![Tworzenie projektu biblioteki klas](media/create3rdpartyunittest1.png) 

   Dodaj projekt do rozwiązania.
    
   ![Nazwa projektu biblioteki klas i dodaj go](media/create3rdpartyunittest3.png) 

1. W projektu biblioteki klas Uruchom NuGet, aby zainstalować dodatek typu plug-in.

   ![Zarządzanie pakietami NuGet, aby zainstalować dodatek typu plug-in](media/create3rdpartyunittest3a.png) 

   [NuGet](https://www.nuget.org/) to rozszerzenie programu Visual Studio, która umożliwia dodawanie i aktualizowanie bibliotek i narzędzi dla projektów.

1. Zainstaluj z wtyczki. Jeśli znasz nazwę, możesz wyszukać jego online.

   ![Zainstaluj z framework 3rd firm](media/create3rdpartyunittest4.png) 

   Platformę odwołuje się do projektu.
        
   ![Dokumentacja dla platformy testów jednostkowych firmy 3rd została dodana do rozwiązania](media/create3rdpartyunittest6.png) 

1. W projektu biblioteki klas Dodaj odwołanie do projektu, który ma zostać przetestowana.
        
   ![Dodaj odwołanie do projektu](media/createunittest6.png) 

1. Wybierz projekt, który zawiera kod, który będzie testu.
        
   ![Wybierz projekt kodu do testowania](media/createunittest7.png) 

1. Kod testu jednostki.

   ![Dodaj kod, aby z testu jednostkowego](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>Zobacz także

* [Polecenie Utwórz testy jednostkowe](create-unit-tests-menu.md)
* [Generowanie testów z IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Uruchamianie testów za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Określić pokrycie kodu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Podnoszenie jakości kodu](improve-code-quality.md)
