---
title: What's New in testy jednostkowe na żywo
ms.date: 10-11-2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
- Live Unit Testing What's New
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 8e6e0a812839dac9ad8962e12a610a82cb56a1fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="whats-new-in-live-unit-testing"></a>What's New in testy jednostkowe na żywo

W tym temacie przedstawiono nowe funkcje dodane do testowania jednostki na żywo w każdej wersji programu Visual Studio w programie Visual Studio 2017 wersji 15 ustęp 3. Omówienie sposobu użycia testów jednostkowych na żywo, zobacz [Live testów jednostkowych z programu Visual Studio 2017](live-unit-testing.md).

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-154"></a>What's new in Live testów jednostkowych dla programu Visual Studio 2017 wersji 15.4

Począwszy od programu Visual Studio 2017 wersji 15.4 Live testów jednostkowych obejmuje i ulepszeń w wielu obszarach:

- **Ulepszona możliwość odnajdowania**. Dla użytkowników, którzy nie wiadomo, które na żywo testów jednostkowych funkcji istnieje, środowiska IDE programu Visual Studio zawiera złoty pasek, który wymienia na żywo testów jednostkowych przy każdym otwarciu rozwiązania, które obejmują testy jednostek, ale testów jednostkowych na żywo nie jest włączone. Informacje przedstawione w pasku gold umożliwia użytkownikowi Dowiedz się więcej o Live testów jednostkowych i włącz ją. Złoty pasek również Wyświetla informacje, gdy nie są spełnione wymagania wstępne dotyczące Live testów jednostkowych. Należą do nich następujące elementy:

   - Brak adapterów testowych.
   - Starsze wersje adapterów testowych są obecne.
   - Przywracanie pakietów NuGet, które odwołują się rozwiązania jest wymagana. 

- **Integracja z powiadomienia Centrum zadań**. Środowiska IDE programu Visual Studio zawiera obecnie tła na żywo testów jednostkowych przetwarzania powiadomienia w Centrum zadań, dzięki czemu użytkownicy mogą łatwo stwierdzić, co się dzieje po włączeniu na żywo testów jednostkowych. To rozwiązuje problem klucza uruchamiania testów jednostkowych na żywo w dużym rozwiązaniem. Wcześniej, kilka minut do momentu pojawił się ikony pokrycia, użytkownicy nie mógł określić czy Live testów jednostkowych naprawdę włączono oraz czy został pracy. Nie już!

- **Obsługa MSTest framework w wersji 1**: Live testów jednostkowych już działa z trzech jednostki popularnych platform testowych: xUnit, NUnit i MSTest. Live testów jednostkowych tylko pracowała stosowania projektów testów jednostkowych MSTest MS Test version 2. Począwszy od programu Visual Studio 2017 wersji 15.4 teraz obsługuje ona również MSTest także w wersji 1. 

- **Niezawodność i wydajność**: teraz Live testów jednostkowych gwarantuje, że system lepiej może wykryć, gdy projekty nie ukończono ładowania w pełni i zapobiega awarii na żywo testów jednostkowych. Tworzenie wydajności ulepszenia także uniknąć reevaluating projektów MSBuild, gdy systemowi, że nic w projekcie pliku została zmieniona.  

- **Ulepszenia interfejsu użytkownika różne**: skomplikowana **aktywnego testu ustawić — dołączania/wykluczania** gestu kliknij prawym przyciskiem myszy opcję została zmieniona na **Live jednostki testowania dołączania/wykluczania**. **Zresetować oczyszczania** opcja **testu**, **Live testów jednostkowych** menu został usunięty. Jest teraz dostępny po wybraniu **narzędzia**, **opcje**, **Live testów jednostkowych** i wybierając **Usuń dane utrwalone**.

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-153"></a>What's new in Live testów jednostkowych dla programu Visual Studio 2017 wersji 15 ustęp 3

Począwszy od programu Visual Studio 2017 wersji 15 ustęp 3, testów jednostkowych na żywo funkcji i ulepszeń w dwóch głównych obszarów:

- Obsługa platformy .NET Core i .NET Standard. Za pomocą testów jednostkowych na żywo na rozwiązań platformy .NET Core i .NET Standard napisany w języku C# lub Visual Basic.
 
-  Ulepszenia wydajności. Można zauważyć, że wydajność jest znacznie szybsze po pierwszej pełnej kompilowanie i Uruchamianie testów w obszarze Live testów jednostkowych. Należy także zauważyć zwiększenie wydajności znaczących w kolejnych uruchamia testów jednostkowych na żywo na tym samym rozwiązaniu. Teraz możemy utrwalenia danych wygenerowanych przez Live testów jednostkowych i był jak najbardziej aktualne testami. 
 
Oprócz tych dodatków głównych Live testów jednostkowych zawiera następujące udoskonalenia: 

- Nowa ikona zlewce teraz jest używany do odróżnienia metody testowej regularne metody. Ikona pusty zlewce wskazuje, że specyficznego testu nie jest uwzględniony w Live testów jednostkowych. 

- Po kliknięciu przycisku dla metody testowej, w oknie podręcznym interfejsu użytkownika ikony pokrycia testów jednostkowych na żywo, masz teraz opcję, aby debugować testu bezpośrednio w tym kontekście, w oknie interfejsu użytkownika i bez konieczności opuszczania edytora kodu. Jest to szczególnie przydatne, gdy patrzy testu nie powiodło się.  

- Dodano kilka dodatkowych opcji można skonfigurować do narzędzia/Opcje/Live jednostki testowanie/ogólne. Można cap pamięć używana na potrzeby testów jednostkowych na żywo. Można również Określ ścieżkę do pliku danych utrwalonych Live testów jednostkowych dla rozwiązania otwarte. 

- Dodano kilka elementów menu dodatkowe pod menu paska z testu/Live testów jednostkowych. **Resetuj wyczyść** powoduje usunięcie danych i generuje go ponownie. **Opcja** przechodzi do narzędzia/Opcje/Live jednostki testowanie/ogólne.
  
- Można teraz używać następujące atrybuty określone w kodzie źródłowym chcesz wykluczyć metody testowe docelowych z testów jednostkowych na żywo:
   - Dla xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
   - Dla NUnit: `[Category("SkipWhenLiveUnitTesting")]`
   - Dla przełącznika MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz także
[Wprowadzenie do testowania jednostek na żywo](live-unit-testing-intro.md)   
[Testy jednostkowe za pomocą programu Visual Studio 2017 na żywo](live-unit-testing.md)

