---
title: Kod testu jednostkowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: "62"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: a60e3236769cbaf35a9b232629834a8b8d52a852
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="unit-test-your-code"></a>Testowanie jednostek kodu
Testy jednostkowe zapewniają deweloperów i testerów szybko wyszukać błędy logikę w metod klas w [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)], [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)], i [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] projektów.  
  
 Narzędzia do testów jednostkowych obejmują:  
  
1.  **Eksplorator testów.** Eksplorator testów pozwala uruchomić testy jednostkowe i obejrzeć ich wyniki. Eksplorator testów może użyć dowolnego środowiska testów jednostkowych, włączając w to środowiska innych producentów, które posiadają adapter dla Eksploratora.  
  
2.  **Framework dla kodu zarządzanego testów jednostkowych firmy Microsoft.** Środowisko testów jednostkowych Microsoft dla kodu zarządzanego jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu środowiska .NET.  
  
3.  **Framework testów jednostkowych firmy Microsoft dla języka C++.** Środowisko testów jednostkowych Microsoft dla języka C++ jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu natywnego.  Google Test, Boost.Test i CTest struktury są dołączone do programu Visual Studio i karty innych firm są dostępne dla platform dodatkowych testów. Aby uzyskać więcej informacji, zobacz [pisania testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md). 
  
4.  **Kod narzędzia pokrycia.** Można określić ilość kodu produktu, jaką bada test jednostkowy jednym poleceniem w Eksploratorze testów.  
  
5.  **Microsoft Fakes framework izolacji.** Środowisko izolacji Microsoft Fakes może stworzyć zastępcze klasy i metody dla kodu produkcyjnego i systemowego, który tworzy zależności w testowanym kodzie. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.  
  
 Można również użyć [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) do eksplorowania kodu .NET do generowania danych testowych i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie, jest generowany wprowadzania testu który wykona tej instrukcji. Analizy przypadków jest wykonywane dla każdego gałąź warunkowa w kodzie.  
  
## <a name="key-tasks"></a>Główne zadania  
 Należy skorzystać z następujących tematów, aby lepiej zrozumieć i z łatwością tworzyć testy jednostkowe:  
  
|Zadania|Skojarzone tematy|  
|-----------|-----------------------|  
|**Szybki Start i wskazówki:** Użyj następujących tematach, aby dowiedzieć się testowania w programie Visual Studio z przykładów kodu jednostek.|-   [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Szybki Start: Test programowanie sterowane za pomocą narzędzia Eksplorator testów](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Testowanie kodu natywnego za pomocą narzędzia Eksplorator testów jednostkowych](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Testy jednostkowe za pomocą narzędzia Eksplorator testów:** Dowiedz się, jak narzędzia Eksplorator testów mogą pomóc tworzyć bardziej wydajnie i efektywnie testów jednostkowych.|-   [Teście jednostkowym](../test/unit-test-basics.md)<br />-   [Tworzenie projektu testu jednostki](../test/create-a-unit-test-project.md)<br />-   [Uruchom testy jednostkowe za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)<br />-   [Uaktualnianie z programu Visual Studio 2010 testy jednostkowe](http://msdn.microsoft.com/en-us/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Testy jednostkowe kodu zarządzanego:**|-   [Pisanie testów jednostkowych dla .NET Framework za pomocą Frameworka testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Kod w języku C++ testy jednostkowe**|-   [Pisanie testów jednostkowych dla C/C++ Framework testów jednostkowych Microsoft dla języka C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Izolowanie testów jednostkowych**|-   [Izolowanie testowanego pomocą struktury Microsoft Fakes kodu](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Umożliwia określenie, jaka część kodu projektu jest testowana przy użyciu testów jednostkowych pokrycia kodu:** więcej informacji na temat funkcji pokrycia kodu [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)] narzędzia do testowania.|-   [Korzystanie z pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Wykonywać analizy wydajności i obciążenia za pomocą testów obciążenia dla testów jednostkowych:** można tworzyć testu obciążenia i Dodaj testy jednostkowe do niej zdiagnozować wydajności i podkreślają problemy w aplikacji. **Uwaga:** tworzenie i używanie testów obciążenia wymaga programu Visual Studio Enterprise.|-   [Tworzenie i edytowanie testów obciążenia](http://msdn.microsoft.com/en-us/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Porady: Dodawanie testów wydajności sieci Web i testów jednostkowych do scenariusza testu obciążenia](http://msdn.microsoft.com/en-us/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Porady: usuwanie testów sieci Web i testów jednostkowych z scenariusza testu obciążenia](http://msdn.microsoft.com/en-us/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Określają i wymuszają bramki jakości:** można utworzyć bramki jakości do wymuszania, że testy są uruchamiane przed kodu zostanie zaznaczona w celu zapewnienia jakości kodu.|-   [Określają i wymuszają bramki jakości](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Rozszerzanie jednostki typu testowego:** funkcji można dodawać do testów, które mogą nie być w ramach testów jednostkowych. Na przykład można dodać właściwość testu, która określa, czy test powinien być uruchomiony w kontekście zwykłego użytkownika. Można również rozszerzyć środowisko o dodanie atrybutów wiersza do metody i użyć danych w tym wierszu wewnątrz testu.|Przykładowy kod jak rozszerzyć jednostki struktury testowej, można znaleźć w następującej [witrynę sieci Web](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Ustawianie opcji testowania:** na przykład określić, gdzie są przechowywane wyniki testu.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Zadania powiązane  
 [Przeglądanie wyników testu w programie Microsoft Test Manager](http://msdn.microsoft.com/en-us/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Opisuje wyniki testów i sposoby pracy z nimi, włączając w to sposób ich wyświetlania, zapisywania i usuwania.  
  
 [Uruchamianie testów systemowych przy użyciu programu Microsoft Visual Studio](/devops-test-docs/test/running-automated-tests-using-microsoft-visual-studio)  
  
 Zawiera linki do informacji o korzystaniu z programu Visual Studio zamiast [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] Uruchamianie testów automatycznych.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Zawiera opis przestrzeni nazw UnitTesting, obejmujący atrybuty, wyjątki, potwierdzenia i inne klasy, które obsługują testy jednostkowe.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 W tym artykule opisano UnitTesting.Web przestrzeni nazw rozszerza UnitTesting przestrzeń nazw, zapewniając obsługę [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] i testów jednostkowych usługi sieci Web.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 [Channel 9: Testowanie aplikacji platformy uniwersalnej systemu Windows utworzony przy użyciu języka XAML jednostkowe](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Fora  
 [Testy jednostkowe programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testy jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Tematy pomocy  
 [Indeks zawartości dla testów jednostkowych](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Zobacz też  
 [Podnoszenie jakości kodu](/visualstudio/test/improve-code-quality)   
 [Testowanie aplikacji](/devops-test-docs/test/test-apps-early-and-often)
