---
title: Poprawa jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b76793a2be80e194f9056280614a9e9646c462d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628770"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Udoskonalanie jakości kodu z zasadami ewidencjowania projektu zespołowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [udoskonalanie jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego](https://docs.microsoft.com/visualstudio/code-quality/enhancing-code-quality-with-team-project-check-in-policies).  
  
Gdy używasz Team Foundation Version Control (TFVC), można utworzyć zasady ewidencjonowania dla projektów zespołowych. Aby wymusić rozwiązań, które zachęcają do lepszego kodu i bardziej skutecznego rozwoju oprogramowania. Zasady ewidencjonowania to reguły, które są ustawiane na poziomie projektu zespołu i wymuszane na komputerach deweloperów, zanim będzie mógł zostać zaewidencjonowany kod.  
  
 Można określić te zespołu projektu zasad ewidencjonowania:  
  
-   **Kompilacje**: wymaga, że błędy kompilacji, które zostały utworzone podczas kompilacji muszą zostać usunięte przed zaewidencjonowaniem.  
  
-   **Komentarzy do zestawu zmian**: wymaga od użytkowników podania komentarz podczas ewidencjonowania zmiany.  
  
-   **Analiza kodu**: wymaga uruchamiania analizy kodu przed zaewidencjonowaniem.  
  
-   **Elementy robocze**: wymaga skojarzone z ewidencjonowanym jeden lub więcej elementów roboczych.  
  
> [!IMPORTANT]
>  Aby użyć zasad ewidencjonowania, musisz mieć połączenie do [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pomocnicza|  
|----------|------------------------|  
|**Tworzenie i używanie zasad ewidencjonowania:** utworzyć zasady ewidencjonowania w przy użyciu ustawień projektu zespołowego [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Ustawianie i wymuszanie bram jakości](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Tworzenie i używanie zasad ewidencjonowania analizy kodu:** można wybrać ze standardowego zestawu reguł analizy kodu lub można utworzyć niestandardowy zestaw.|[Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
|Zadanie|Zawartość pomocnicza|  
|----------|------------------------|  
|**Konfigurowanie środowiska deweloperskiego:** przed można utworzyć lub zmodyfikować kod, należy ustawić środowiska deweloperskie i testowe przy użyciu odpowiedniego kodu źródłowego. Jeśli pracujesz z bazami danych, musi również mieć dostęp do ich reprezentacji w trybie offline.|[Konfigurowanie środowisk](http://msdn.microsoft.com/en-us/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Użyj analizy kodu w procesie tworzenia:** członkowie zespołu uruchamiają analizę kodu na swoich komputerach roboczych. W programie Visual Studio deweloperzy skonfigurować i uruchamiają analizę kodu dla poszczególnych projektów kodu, wyświetlanie oraz analizować problemy znalezione przez przebiegi i Utwórz elementy robocze dla ostrzeżeń.|[Analizowanie jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Tworzenie i Uruchamianie testów jednostkowych:** testy jednostkowe pozwalają deweloperom i testerom w szybki sposób sprawdzić występowanie błędów logicznych w metodach klas w projektach C#, Visual Basic .NET i C++. Test jednostkowy można utworzyć jeden raz i uruchamiany za każdym razem zmianie kodu źródłowego, aby upewnić się, że zostały wprowadzone żadne błędy.|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|  
|**Śledzenie elementów roboczych i defektów:** elementów roboczych można użyć do śledzenia i zarządzania pracą i informacjami o projekcie zespołowym. Element roboczy jest bazy danych rekord [!INCLUDE[esprfound](../includes/esprfound-md.md)] używa do śledzenia przypisania i postępu prac. Można użyć różnych rodzajów elementów roboczych do śledzenia różnych typów pracy takich jak wymagań klientów, błędów produktu i zadań programistycznych.|[Śledzenie pracy i zarządzanie przepływem pracy &#91;przekierowanie&#93;](http://msdn.microsoft.com/en-us/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: testowanie jednostkowe: testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)



