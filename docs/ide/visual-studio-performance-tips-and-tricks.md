---
title: "I porady dotyczące wydajności programu Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
caps.latest.revision: "1"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b703fd45732e3fd083a5c95b68647f67dce57b3a
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Wydajność programu Visual Studio — porady i wskazówki

Visual Studio wydajności zalecenia są przeznaczone dla sytuacje małej ilości pamięci, które mogą wystąpić w rzadkich przypadkach. W takich sytuacjach może zoptymalizować niektóre funkcje programu Visual Studio, które nie może być używany. Poniższe porady nie są przeznaczone jako ogólne zalecenia.

> [!NOTE]
> Jeśli masz trudności z używaniem produktu z powodu problemów dotyczących pamięci, Daj nam znać za pomocą narzędzia opinii.

## <a name="optimize-your-environment"></a>Optymalizowanie środowiska

- **Użyj 64-bitowy system operacyjny**

    Po uaktualnieniu do wersji 64-bitowe systemu z 32-bitowej wersji systemu Windows, należy rozwinąć ilość dostępnej pamięci wirtualnej dla programu Visual Studio, od 2 do 4 GB. Dzięki temu Visual Studio do obsługi obciążeń znacznie większe, mimo że jest to proces 32-bitowy.

    Aby uzyskać więcej informacji, zobacz [limity pamięci](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits) i [na 64-bitowym systemie Windows przy użyciu/largeaddressaware](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="configure-solution-and-projects"></a>Skonfiguruj rozwiązanie i projekty

Jeśli masz bardzo dużym rozwiązaniem z wielu projektów, może korzystać dzięki optymalizacji następujące:

- **Zwolnienia projektów**

    Można ręcznie Zwolnij rzadko używane poszczególnych projektów z Eksploratora rozwiązań za pomocą menu kontekstowym kliknij prawym przyciskiem myszy.

- **Refaktoryzuj rozwiązania**

    Rozwiązania można podzielić na kilka mniejszych plików rozwiązania z często używanych projektów. Ta refaktoryzacji powinno być znacznie zmniejszyć użycie pamięci przepływu pracy. Mniejsze rozwiązań także załadować szybciej.

## <a name="configure-debugging-options"></a>Skonfiguruj opcje debugowania
Jeśli użytkownik zwykle zaczyna brakować pamięci podczas sesji debugowania, wydajność można zoptymalizować w co najmniej jeden zmiany konfiguracji.

- **Włącz opcję tylko mój kod**

    Najprostsza optymalizacji jest umożliwienie **tylko mój kod** funkcji, która tylko ładuje symbole dla projektu. Włączenie tej funkcji może spowodować znaczne pamięci, zapisywania do debugowania aplikacji zarządzanych (.NET). Ta opcja jest już włączona domyślnie w niektórych typów projektów.

    Aby włączyć **tylko mój kod**, wybierz **Narzędzia > Opcje > debugowanie > Ogólne**, a następnie wybierz **Włącz opcję tylko mój kod**.

- **Określ symbole ładowania**

    Debugowanie natywnych ładowanie plików symboli (.pdb) jest kosztowna pod względem zasobów pamięci. Można skonfigurować ustawienia symbol debuger w celu zachowywania pamięci. Zazwyczaj należy skonfigurować rozwiązania można ładować tylko moduły z projektu.

    Aby określić ładowanie symboli, wybierz **Narzędzia > Opcje > debugowanie > symbole**.

    Ustaw opcje **tylko określonych modułów** zamiast **wszystkie moduły** , a następnie określ modułów, które należy załadować. Podczas debugowania, można również prawym przyciskiem myszy w określonych modułach **modułów** okna, aby jawnie objąć moduł ładowania symboli. (Aby otworzyć okno podczas debugowania, wybierz **debugowania > Windows > modułów**.)

    Aby uzyskać więcej informacji, zobacz [Opis plików symboli](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Wyłącz narzędzia diagnostyczne**

    Zalecane jest, wyłącz profilowanie procesora CPU po użyciu. Ta funkcja może używać dużych ilości zasobów. Po włączeniu profilowanie procesora CPU, ten stan jest trwały między sesjami kolejnych debugowania, więc warto jawnie wyłączony, po zakończeniu. Możesz zapisać niektórych zasobów przez wyłączenie narzędzia diagnostyczne podczas debugowania, jeśli nie potrzebujesz funkcji podana.

    Aby wyłączyć narzędzia diagnostyczne, Uruchom sesję debugowania, wybierz **Narzędzia > Opcje > Włącz narzędzia diagnostyczne**i usuń zaznaczenie opcji.

    Aby uzyskać więcej informacji, zobacz [narzędziach profilowania](../profiling/profiling-tools.md).

## <a name="disable-tools-and-extensions"></a>Wyłącz narzędzia i rozszerzenia
Niektóre narzędzia lub rozszerzenia może ją wyłączyć, aby zwiększyć wydajność.

> [!TIP]
> Problemy z wydajnością można odizolować często wyłączając rozszerzenia co w czasie i ponowne sprawdzanie wydajności.

### <a name="managed-language-services-roslyn"></a>Usługi językowe zarządzanych (Roslyn)

Aby uzyskać informacje dotyczące wydajności Roslyn, zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań] (https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Wyłącz Pełna analiza rozwiązania**

    Visual Studio dokonuje analizy całego rozwiązania w celu zapewnienia bogate środowisko o błędach przed wywołaniem kompilacji. Ta funkcja jest przydatna do identyfikowania błędów tak szybko, jak to możliwe. Jednak dla bardzo dużych rozwiązań tej funkcji można zużywają zasoby pamięci znaczące. Jeśli wystąpią problemy podobne lub wykorzystania pamięci, możesz wyłączyć tego środowiska, aby zwolnić zasoby. Domyślnie ta opcja jest włączona dla programu Visual Basic i wyłączone dla C#.

    Aby wyłączyć **pełnej analizy rozwiązania**, wybierz **Narzędzia > Opcje > Edytor tekstu >< Visual Basic lub C# >**. Następnie wybierz pozycję **zaawansowane** i usuń zaznaczenie **Włącz pełną analizę rozwiązania**.

- **Wyłączanie funkcji CodeLens**

    Wykonuje program Visual Studio **Znajdź wszystkie odwołania** zadań dla każdej metody, która jest wyświetlana. CodeLens dostarcza funkcje takie jak wyświetlanie wbudowanego liczba odwołań. Praca jest wykonywana w ramach osobnej operacji (na przykład ServiceHub.RoslynCodeAnalysisService32). W bardzo dużych rozwiązaniach lub w systemach zasobów ograniczone ta funkcja może mieć znaczący wpływ na wydajność, nawet jeśli jest uruchamiane przy niskim priorytecie. Jeśli występują wysokiej Procesora w tym procesie, lub problemów pamięci (na przykład podczas ładowania z dużym rozwiązaniem na maszynie 4 GB), można spróbować wyłączenie tej funkcji, aby zwolnić zasoby.

    Aby wyłączyć CodeLens, wybierz **Narzędzia > Opcje > Edytor tekstu > wszystkie języki > CodeLens**i Wyłącz funkcję.

    Ta funkcja jest dostępna w programie Visual Studio Professional i Visual Studio Enterprise.

### <a name="other-tools-and-extensions"></a>Inne narzędzia i rozszerzenia

- **Wyłącz rozszerzenia**

    Rozszerzenia są dodawane do programu Visual Studio składniki dodatkowe oprogramowanie, które udostępnia nowych funkcji lub rozszerzanie funkcjonalności istniejących. Rozszerzenia często może być źródłem problemów zasobów pamięci. Jeśli występują problemy z pamięcią zasobów, spróbuj wyłączyć rozszerzenia co w czasie, aby zobaczyć, jak wpływa na scenariuszu lub przepływ pracy.

    Aby wyłączyć rozszerzenia, przejdź do **narzędzia | Rozszerzenia i aktualizacje**i Wyłącz określone rozszerzenie.

- **Wyłącz projektanta XAML**

    Projektant XAML jest domyślnie włączona, ale tylko w przypadku otwarcia wykorzystuje zasoby. Plik XAML. Praca z plikami XAML, ale nie chcesz korzystać z funkcji projektanta, należy wyłączyć tę funkcję, aby zwolnić część pamięci.

    Aby wyłączyć projektanta XAML, przejdź do **Narzędzia > Opcje > projektanta XAML > Włącz projektanta XAML**i usuń zaznaczenie opcji.

- **Usuń obciążeń**

    Instalator programu Visual Studio umożliwia usunięcie obciążeń, które nie są już używane. Ta akcja upraszcza koszt uruchamiania i środowiska uruchomieniowego przez pominięcie pakiety i zestawy, które nie są już potrzebne.

## <a name="force-a-garbage-collection"></a>Wymuś wyrzucania elementów bezużytecznych

Środowisko CLR używa systemu zarządzania pamięci kolekcji pamięci. W tym systemie czasami pamięć jest używana przez obiekty, które nie są już potrzebne. Ten stan jest tymczasowa. Moduł zbierający elementy bezużyteczne spowoduje zwolnienie tej pamięci na podstawie jego wydajności i heurystyki użycia zasobów. Można wymusić CLR zbierać wszystkie nieużywane pamięci za pomocą klawisz skrótu w programie Visual Studio. Jeśli istnieje znaczną ilość pamięci oczekiwania dla kolekcji i wymusić wyrzucania elementów bezużytecznych, użycie pamięci przez proces devenv.exe drop w Menedżerze zadań powinna zostać wyświetlona. Jest to rzadko niezbędne do używania tej metody. Jednak po ukończeniu kosztowna operacja (np. pełna kompilacja, sesji debugowania lub rozwiązanie zdarzenia open) ułatwia możesz określić, ile pamięci naprawdę jest używany przez proces. Ponieważ Visual Studio jest mieszana (zarządzanego i natywnego), jest czasami możliwe alokatora macierzystego i moduł zbierający elementy bezużyteczne konkurują o zasoby pamięci ograniczone. W warunkach wysokie użycie pamięci może pomóc wymusić modułu zbierającego elementy bezużyteczne do uruchomienia.

Aby wymusić wyrzucania elementów bezużytecznych, użyj klawiszy skrótu: **Ctrl + Alt + Shift + F12**, **Ctrl + Alt + Shift + F12** (go naciśnij dwa razy klawisz).

Jeśli wymuszanie wyrzucanie elementów bezużytecznych niezawodnie sprawia, że scenariusz pracy pliku raportu za pomocą narzędzia opinii programu Visual Studio to zachowanie jest prawdopodobnie usterki.

Aby uzyskać szczegółowy opis moduł garbage collector środowiska CLR, zobacz [podstawowych z wyrzucanie elementów bezużytecznych](https://msdn.microsoft.com/en-us/library/ee787088(v=vs.110).aspx).

## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/index.md)
