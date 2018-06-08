---
title: Visual Studio wydajności porady i wskazówki
ms.date: 08/31/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08b2e1087b97cb16a52a8abdf8f204fd0f3a0bfb
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845200"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio wydajności porady i wskazówki

Visual Studio wydajności zalecenia są przeznaczone dla sytuacje małej ilości pamięci, które mogą wystąpić w rzadkich przypadkach. W takich sytuacjach może zoptymalizować niektóre funkcje programu Visual Studio, które nie może być używany. Poniższe porady nie są przeznaczone jako ogólne zalecenia.

> [!NOTE]
> Daj nam znać, jeśli masz trudności z używaniem produktu z powodu problemów dotyczących pamięci, za pomocą [narzędzie opinii](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="use-a-64-bit-os"></a>Użyj 64-bitowego systemu operacyjnego

Po uaktualnieniu do wersji 64-bitowe systemu z 32-bitowej wersji systemu Windows, należy rozwinąć ilość dostępnej pamięci wirtualnej dla programu Visual Studio, od 2 do 4 GB. Dzięki temu Visual Studio do obsługi obciążeń znacznie większe, mimo że jest to proces 32-bitowy.

Aby uzyskać więcej informacji, zobacz [limity pamięci](https://msdn.microsoft.com/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits) i [/largeaddressaware w systemie 64-bitowym systemie Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Wyłącz automatyczne plików przywracania

Visual Studio ponownie automatycznie otwiera dokumenty, które pozostawiono otwarte w poprzedniej sesji. To może przedłużyć czas potrzebny do załadowania rozwiązania przez maksymalnie 30% lub więcej, w zależności od typu projektu i dokumenty otwierany. Projektanci, takich jak formularze systemu Windows i języka XAML i niektóre pliki obsługi języka JavaScript i typescript można otwierać się powoli.

Visual Studio powiadamia w żółty pasek podczas przywracania automatyczne dokumentu powoduje rozwiązanie znacznie mniejszą załadować. Możesz wyłączyć automatyczne plików otworzyć ponownie wykonaj następujące czynności:

1. Wybierz **narzędzia** > **opcje** otworzyć **opcje** okno dialogowe.

1. Na **projekty i rozwiązania** > **ogólne** pozycję Anuluj wybór **ponownie otworzyć dokumenty na ładowania rozwiązania**.

Jeśli wyłączysz Przywracanie plików automatyczne szybko przejść do plików, który chcesz otworzyć jest przy użyciu [przejdź do](../ide/go-to.md). Wybierz **Edytuj** > **przejdź do** > **przejdź do wszystkich**, lub naciśnij klawisz **Ctrl**+**T** .

## <a name="configure-debugging-options"></a>Skonfiguruj opcje debugowania

Jeśli użytkownik zwykle zaczyna brakować pamięci podczas sesji debugowania, wydajność można zoptymalizować w co najmniej jeden zmiany konfiguracji.

- **Włącz opcję tylko mój kod**

    Najprostsza optymalizacji jest umożliwienie **tylko mój kod** funkcji, która tylko ładuje symbole dla projektu. Włączenie tej funkcji może spowodować znaczne pamięci, zapisywania do debugowania aplikacji zarządzanych (.NET). Ta opcja jest już włączona domyślnie w niektórych typów projektów.

    Aby włączyć **tylko mój kod**, wybierz **narzędzia** > **opcje** > **debugowanie**  >   **Ogólne**, a następnie wybierz **Włącz opcję tylko mój kod**.

- **Określ symbole ładowania**

    Debugowanie natywnych ładowanie plików symboli (*.pdb*) jest kosztowna pod względem zasobów pamięci. Można skonfigurować ustawienia symbol debuger w celu zachowywania pamięci. Zazwyczaj należy skonfigurować rozwiązania można ładować tylko moduły z projektu.

    Aby określić ładowanie symboli, wybierz **narzędzia** > **opcje** > **debugowanie** > **symbole**.

    Ustaw opcje **tylko określonych modułów** zamiast **wszystkie moduły** , a następnie określ modułów, które należy załadować. Podczas debugowania, można również prawym przyciskiem myszy w określonych modułach **modułów** okna, aby jawnie objąć moduł ładowania symboli. (Aby otworzyć okno podczas debugowania, wybierz **debugowania** > **Windows** > **modułów**.)

    Aby uzyskać więcej informacji, zobacz [zrozumieć pliki symboli](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Wyłącz narzędzia diagnostyczne**

    Zalecane jest, wyłącz profilowanie procesora CPU po użyciu. Ta funkcja może używać dużych ilości zasobów. Po włączeniu profilowanie procesora CPU, ten stan jest trwały między sesjami kolejnych debugowania, więc warto jawnie wyłączony, po zakończeniu. Możesz zapisać niektórych zasobów przez wyłączenie narzędzia diagnostyczne podczas debugowania, jeśli nie potrzebujesz funkcji podana.

    Aby wyłączyć **narzędzia diagnostyczne**, Uruchom sesję debugowania, wybierz **narzędzia** > **opcje** > **włączyć diagnostyki Narzędzia**i usuń zaznaczenie opcji.

    Aby uzyskać więcej informacji, zobacz [narzędziach profilowania](../profiling/profiling-tools.md).

## <a name="disable-tools-and-extensions"></a>Wyłącz narzędzia i rozszerzenia

Niektóre narzędzia lub rozszerzeń można wyłączyć w celu zwiększenia wydajności.

> [!TIP]
> Problemy z wydajnością można odizolować często wyłączając rozszerzenia co w czasie i ponowne sprawdzanie wydajności.

### <a name="managed-language-service-roslyn"></a>Zarządzane usługi języka (Roslyn)

Aby uzyskać informacje dotyczące wydajności platformy kompilatora .NET ("Roslyn"), zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Wyłącz Pełna analiza rozwiązania**

    Visual Studio dokonuje analizy całego rozwiązania w celu zapewnienia bogate środowisko o błędach przed wywołaniem kompilacji. Ta funkcja jest przydatna do identyfikowania błędów tak szybko, jak to możliwe. Jednak dla dużych rozwiązań tej funkcji można zużywają zasoby pamięci znaczące. Jeśli wystąpią problemy podobne lub wykorzystania pamięci, możesz wyłączyć tego środowiska, aby zwolnić zasoby. Domyślnie ta opcja jest włączona dla programu Visual Basic i wyłączone dla C#.

    Aby wyłączyć **pełnej analizy rozwiązania**, wybierz **narzędzia** > **opcje** > **Edytor tekstu**, a następnie wybierz pozycję albo **Visual Basic** lub **C#**. Wybierz **zaawansowane** i usuń zaznaczenie **Włącz pełną analizę rozwiązania**.

- **Wyłączanie funkcji CodeLens**

    Wykonuje program Visual Studio **Znajdź wszystkie odwołania** zadań dla każdej metody, która jest wyświetlana. CodeLens dostarcza funkcje takie jak wyświetlanie wbudowanego liczba odwołań. Praca jest wykonywana w ramach osobnej operacji, takich jak *ServiceHub.RoslynCodeAnalysisService32*. W dużych rozwiązaniach lub w systemach ograniczonego zasobów ta funkcja może mieć znaczący wpływ na wydajność. Jeśli wystąpią problemy z pamięcią, na przykład podczas ładowania dużych rozwiązanie na komputer 4 GB lub wysokie użycie procesora CPU dla tego procesu, CodeLens, aby zwolnić zasoby można wyłączyć.

    Aby wyłączyć **CodeLens**, wybierz **narzędzia** > **opcje** > **Edytor tekstu**  >   **Wszystkie języki** > **CodeLens**i Wyłącz tę funkcję.

    > [!NOTE]
    > CodeLens są dostępne w wersjach Professional i Enterprise programu Visual Studio.

### <a name="other-tools-and-extensions"></a>Inne narzędzia i rozszerzenia

- **Wyłącz rozszerzenia**

    Rozszerzenia są dodawane do programu Visual Studio składniki dodatkowe oprogramowanie, które udostępnia nowych funkcji lub rozszerzanie funkcjonalności istniejących. Rozszerzenia często może być źródłem problemów zasobów pamięci. Jeśli występują problemy z pamięcią zasobów, spróbuj wyłączyć rozszerzenia co w czasie, aby zobaczyć, jak wpływa na scenariuszu lub przepływ pracy.

    Aby wyłączyć rozszerzenia, przejdź do **narzędzia** > **rozszerzenia i aktualizacje**i Wyłącz określone rozszerzenie.

- **Wyłącz projektanta XAML**

    Projektant XAML jest domyślnie włączona, ale tylko w przypadku otwarcia wykorzystuje zasoby *.xaml* pliku. Praca z plikami XAML, ale nie chcesz korzystać z funkcji projektanta, należy wyłączyć tę funkcję, aby zwolnić część pamięci.

    Aby wyłączyć **projektanta XAML**, przejdź do **narzędzia** > **opcje** > **projektanta XAML**  >  **Włącz projektanta XAML**i usuń zaznaczenie opcji.

- **Usuń obciążeń**

    Instalator programu Visual Studio umożliwia usunięcie obciążeń, które nie są już używane. Ta akcja upraszcza koszt uruchamiania i środowiska uruchomieniowego przez pominięcie pakiety i zestawy, które nie są już potrzebne.

## <a name="force-a-garbage-collection"></a>Wymuś wyrzucania elementów bezużytecznych

Środowisko CLR używa systemu zarządzania pamięci kolekcji pamięci. W tym systemie czasami pamięć jest używana przez obiekty, które nie są już potrzebne. Ten stan jest tymczasowa. Moduł zbierający elementy bezużyteczne spowoduje zwolnienie tej pamięci na podstawie jego wydajności i heurystyki użycia zasobów. Można wymusić CLR zbierać wszystkie nieużywane pamięci za pomocą klawisz skrótu w programie Visual Studio. Jeśli istnieje znaczną ilość pamięci oczekiwania dla kolekcji i wymusić wyrzucania elementów bezużytecznych, powinny pojawić się użycie pamięci przez *devenv.exe* procesu drop **Menedżera zadań**. Jest to rzadko niezbędne do używania tej metody. Jednak po ukończeniu kosztowna operacja (np. pełna kompilacja, sesji debugowania lub rozwiązanie zdarzenia open) ułatwia możesz określić, ile pamięci naprawdę jest używany przez proces. Ponieważ Visual Studio jest mieszana (zarządzanego i natywnego), jest czasami możliwe alokatora macierzystego i moduł zbierający elementy bezużyteczne konkurują o zasoby pamięci ograniczone. W warunkach wysokie użycie pamięci może pomóc wymusić modułu zbierającego elementy bezużyteczne do uruchomienia.

Aby wymusić wyrzucania elementów bezużytecznych, użyj klawiszy skrótu: **Ctrl**+**Alt**+**Shift**+**F12**, **Ctrl**+**Alt**+**Shift**+**F12** (go naciśnij dwa razy klawisz).

Jeśli wymuszanie wyrzucanie elementów bezużytecznych niezawodnie sprawia, że scenariusz pracy pliku raportu za pomocą narzędzia opinii programu Visual Studio to zachowanie jest prawdopodobnie usterki.

Aby uzyskać szczegółowy opis moduł garbage collector środowiska CLR, zobacz [podstawy dotyczące wyrzucania elementów bezużytecznych](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Załadowanie rozwiązania szybsze (blog Visual Studio)](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)