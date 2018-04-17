---
title: Wzorce obciążenia testowania w programie Visual Studio obciążenia | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7a6d9054bb12290d29247c09263a3854f2ea0dad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Edytowanie wzorców obciążenia w celu modelowania aktywności wirtualnych użytkowników

Właściwości wzorca obciążenia Określ, jak obciążenia symulowanego użytkownika jest uwzględniany podczas testu obciążenia. Program Visual Studio udostępnia trzy wzorców obciążenia wbudowanych: stała, kroku i opartego na celach. Wybierz wzorzec obciążenia oraz dostosować właściwości do odpowiednich poziomów cele testu obciążenia.

Wzorcu obciążenia jest składnikiem scenariusza. Scenariusze, wraz z ich wzorców obciążenia zdefiniowanych w skład testu obciążenia.

> [!NOTE]
> W wszystkich wzorców obciążenia obciążenia, które generuje Visual Studio jest symulowane ładunek wirtualnych użytkowników.

## <a name="load-patterns"></a>Wzorce obciążenia

### <a name="constant"></a>Stała

 Wzorzec obciążenia stałej służy do określania obciążenie użytkownikami, który nie ulega zmianie podczas testu obciążenia. Na przykład po uruchomieniu testu dymu w aplikacji sieci Web, możesz ustawić światła, stałych obciążenia 10 użytkowników.

#### <a name="constant-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca obciążenia stałej

 Ze stałego wzorca obciążenia jest używany do uruchamiania tego samego obciążenia użytkownika podczas uruchomienia testu obciążenia. Należy zachować ostrożność przy użyciu ze stałego wzorca obciążenia mającego liczba użytkowników wysokiej; wykonanie tej dlatego żądanie nierozsądne i wypadku na umieścić serwer lub serwery na początku testu obciążenia. Na przykład jeśli test obciążenia zawiera testu sieci Web, która rozpoczyna się od żądania do strony głównej i skonfigurować testu obciążenia z stałej obciążenia 1000 użytkowników, test obciążenia zostanie przesłać pierwszych 1000 żądań do strony głównej tak szybko jak to możliwe. Nie można realistyczne symulację rzeczywistych dostęp do witryny sieci Web. Aby temu zaradzić, rozważ użycie wzorca obciążenia krokowego zwiększającą się stopniowo do 1000 użytkowników, lub określ okres rozgrzewania ustawień uruchamiania testu obciążenia. Jeśli okres rozgrzewania jest określony, test obciążenia zostanie automatycznie zwiększenie obciążenia stopniowo w okresie rozgrzewania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień Uruchom scenariusz](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Krok

 Krokowego wzorca obciążenia pozwala określić obciążenie użytkownikami, która zwiększa z czasem do zdefiniowanych maksymalne obciążenie użytkownikami. Dla obciążeń wykonywanie krok po kroku, należy określić **początkowa liczba użytkowników**, **maksymalna liczba użytkowników**, **krok czas trwania (w sekundach)**, i **liczbę użytkowników**.

 Na przykład obciążenia kroku z **początkowej użytkownika** licznik równy jeden, **maksymalna liczba użytkowników** 100, **krok czas trwania (w sekundach)** 10, a **liczbę użytkowników** 1 tworzy wzorca obciążenia użytkownika, który rozpoczyna się od 1, zwiększy się o 1 co 10 sekund, dopóki nie osiągnie 100 użytkowników.

> [!NOTE]
>  Jeśli test całkowity czas trwania jest krótszy niż czas, który jest wymagany do kroku maksymalnie maksymalne obciążenie użytkownikami, testu zatrzyma się po czas trwania i nie osiąga maksymalna liczba użytkowników docelowych.

 Celem krok umożliwia zwiększenie obciążenia, dopóki serwer osiągnie punkt gdzie wydajności znacznie zmniejsza. W miarę wzrostu obciążenia serwera po pewnym czasie będzie brakować zasobów. Obciążenie kroku jest sposób określenia liczby użytkowników, w którym dzieje się tak. Z wykonywania krokowego obciążenia masz również monitorowanie zasobów agenta ściśle, aby upewnić się, że agenci mogą wytwarzać żądaną obciążenia.

 Zwykle należy przeprowadzić kilka działa, których czas trwania kroku innego użytkownika krok liczby i, dzięki czemu można uzyskać dobrą miary dla danego obciążenia. Często obciążeń Pokaż kolekcji początkowej dla każdego kroku podczas dodawania użytkowników. Gospodarstwa obciążenia w tym szybkość służy do pomiaru wydajności systemu, po systemie odzyskiwania z kolekcji początkowej.

#### <a name="step-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca obciążenia kroku

 Krokowego wzorca obciążenia może służyć do zwiększa obciążenie serwera lub serwerów uruchomień testów obciążenia, tak aby były widoczne, jak wydajność może być różna miarę wzrostu obciążenia użytkownika. Na przykład, aby zobaczyć, jak wykonać serwer lub serwery miarę wzrostu obciążenia użytkownika do 2000 użytkowników, może uruchomić testu obciążenia 10 godzin przy użyciu krokowego wzorca obciążenia, który ma następujące właściwości:

-   Początkowa liczba użytkowników: 100

-   Maksymalna liczba użytkowników: 2000

-   Czas trwania kroku (w sekundach): 1800

-   Czas (w sekundach) do zwiększenia kroku: 20

-   Liczba użytkowników krok: 100

 Te ustawienia uruchomić test obciążenia w ciągu 30 minut (1800 w sekundach) na użytkownika ładuje 100, 200, 300 i maksymalnie 2000 użytkowników. **Czas do zwiększenia kroku** właściwości warto szczególnej uwagi, ponieważ jest tylko jeden z tych właściwości, która nie jest dostępna do wyboru w Kreatorze nowego testu obciążenia. Ta właściwość umożliwia zwiększenie od jednego kroku do następnego (na przykład od 100 do 200 użytkowników) występuje stopniowo zamiast natychmiast. W tym przykładzie obciążenie użytkownikami zostanie zwiększona od 100 do 200 użytkowników w okresie sekundę 20 (wzrost pięciu użytkowników co sekundę). Aby uzyskać więcej informacji, zobacz [porady: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Opartego na celach

 Wzorca obciążenia opartego na celach przypomina krokowego wzorca, ale dopasowuje obciążenie użytkownikami, na podstawie progów licznika wydajności i korekty obciążenia okresowe użytkownika. Obciążenia opartego na celach są przydatne w wielu różnych celów:

-   Maksymalizacja dane wyjściowe z agentów: pomiar klucza ograniczanie metryki dla agenta, aby zmaksymalizować dane wyjściowe agentów. Zazwyczaj jest Procesora; Jednak może to również być pamięci.

-   Osiągnięcia pewnego poziomu zasobów docelowych, zwykle procesora CPU, na serwerze docelowym, następnie pomiarowe przepływności na tym poziomie. Dzięki temu można wykonać porównania do rozpoczęcia realizacji przepływności, biorąc pod uwagę spójne poziom użycia zasobów na serwerze.

-   Osiągnięcie poziomu przepływności docelowej na serwerze.

 W poniższej tabeli przykładzie opartego na celach wzorca z następującymi ustawieniami właściwości:

|Grupa właściwości|Właściwość|Wartość|
|--------------------|--------------|-----------|
|Licznik wydajności|Kategoria|Procesor|
|Licznik wydajności|Komputer|ContosoServer1|
|Licznik wydajności|Licznik|Czas procesora (%)|
|Licznik wydajności|Wystąpienie|_Total|
|Zakres docelowy dla licznika wydajności|Górną granicę|90|
|Zakres docelowy dla licznika wydajności|Niski zakończenia|70|
|Limity liczby użytkowników|Początkowa liczba użytkowników|1|
|Limity liczby użytkowników|Maksymalna liczba użytkowników|100|
|Limity liczby użytkowników|Maksymalne zmniejszenie liczby użytkowników|5|
|Limity liczby użytkowników|Maksymalne zwiększenie liczby użytkowników|5|
|Limity liczby użytkowników|Minimalna liczba użytkowników|1|

 Te ustawienia powodują **analizatora testu obciążenia** dostosowanie obciążenie użytkownikami od 1 do 100 podczas testu w taki sposób, który **licznika** dla `% Processor Time` z ruchów WebServer01 między `70%`i `90%.`

 Rozmiar każdej korekty obciążenia użytkownika jest określany przez **maksymalne zwiększenie liczby użytkowników** i **maksymalne zmniejszenie liczby użytkowników** ustawienia. Limity liczby użytkowników są ustawiane przez **maksymalna liczba użytkowników** i **minimalna liczba użytkowników** właściwości.

#### <a name="goal-based-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca obciążenia opartego na celach

 Wzorca obciążenia opartego na celach jest przydatne, jeśli chcesz określić liczbę użytkowników, którzy mogą obsługiwać systemu przed osiągnie pewnego poziomu wykorzystania zasobów. Ta opcja działa najlepiej, gdy już zidentyfikowano zasobów ograniczające (to znaczy wąskie gardło) w systemie.

 Na przykład załóżmy, że znasz procesora CPU na serwerze bazy danych jest ograniczanie zasobów w systemie, czy chcesz sprawdzić, ilu użytkowników mogą być obsługiwane, gdy procesora CPU na serwerze bazy danych jest zajęty około 75 procent. Można użyć wzorca obciążenia opartego na celach, który ma celem utrzymania wartością wydajność licznika "% czasu procesora" od 70 procent do 80 procent.

 Rzecz do Zwróć uwagę na to, czy innego zasobu jest ograniczanie przepływności systemu. Takie zasoby może spowodować cel, który jest określony przez wzorca obciążenia opartego na celach do nigdy nie można nawiązać połączenia. Ponadto obciążenie użytkownikami będą nadal podstawę do wartości określonej dla **maksymalna liczba użytkowników** zostanie osiągnięty. Nie jest to zazwyczaj odpowiednie obciążenia, więc należy uważać o wybór licznika wydajności we wzorcu obciążenia opartego na celach.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Określenie wzorca obciążenia początkowej podczas testu obciążenia:** podczas tworzenia testu obciążenia za pomocą nowego załadować Test kreatora, wybierz wzorzec obciążenia.|-   [Zmiana wzorca obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md#EditingLoadPatternsChanging)|
|**Edytowanie wzorzec obciążenia dla testu obciążenia:** po utworzeniu testu obciążenia można edytować wzorca obciążenia w edytorze testu obciążenia.|-   [Porady: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Określanie, czy scenariusza testu wirtualnych użytkowników w obciążenia powinny obejmować dane pamięci podręcznej sieci Web:** można zmienić **procent nowych użytkowników** właściwość wpływ na sposób, w którym testu obciążenia symuluje sieci Web, która buforowanie Czy można wykonać przez przeglądarkę sieci Web dla wirtualnych użytkowników.|-   [Porady: Określanie wartości procentowej użytkowników wirtualnych korzystających z danych pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Określanie czasu narastania kroku dla wzorca obciążenia krokowego:** **czas do zwiększenia kroku** właściwość umożliwia zwiększenie od jednego kroku do następnego (na przykład od 100 do 200 użytkowników) występuje stopniowo zamiast natychmiast.|-   [Porady: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="changing-the-load-pattern"></a>Zmiana wzorca obciążenia

 Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** można zmienić właściwości wzorca obciążenia skojarzone ze scenariuszem do poziomu, które spełniają cele testu.

> [!NOTE]
>  Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

 Wzorzec obciążenia określa liczbę wirtualnych użytkowników active podczas testu obciążenia i szybkości, jaką nowi użytkownicy są dodawani. Możesz wybrać spośród trzech wzorców dostępne: krok wzorzec, stała i opartego na celach. Aby uzyskać więcej informacji, zobacz [określenie liczby wirtualnych użytkowników z wzorców obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
>  Możesz również zmienić właściwości obciążenia programowo przy użyciu wtyczki testu obciążenia. Aby uzyskać więcej informacji, zobacz [porady: tworzenie wtyczek testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Aby zmienić wzorca obciążenia

1.  Otwórz testu obciążenia.

2.  W **edytora testu obciążenia**, w folderze scenariusze rozwiń scenariusz chcesz edytować wzorzec obciążenia dla i wybierz wzorzec obciążenia dla scenariusza.

    > [!NOTE]
    > Treść węzła wzorzec obciążenia, jest wyświetlany w drzewie scenariusza testów obciążenia, odzwierciedla profilu obciążenia, który można wybrać podczas tworzenia obciążenia testu. Może być albo **stałej profilu obciążenia** lub **profilu obciążenia krok**.

3.  Naciśnij klawisz **F4** do wyświetlenia okna właściwości.

     **Wzorca obciążenia** i **parametry** kategorie są wyświetlane w oknie właściwości.

4.  (Opcjonalnie) Zmień **wzorzec** właściwości w **wzorca obciążenia** kategorii.

     Opcje dla **wzorzec** właściwości są **krok**, **stałej**, i **oparty na celach**. Aby uzyskać więcej informacji na temat typów wzorzec obciążenia, zobacz [określenie liczby wirtualnych użytkowników z wzorców obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5.  (Opcjonalnie) W **parametry** kategorii, zmień wartości.

    > [!NOTE]
    > Wartości można ustawić dla **parametry** różnią się zgodnie z wartością, które zostały wybrane do **wzorzec** właściwości.

6.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowego wzorca obciążenia.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Porady: Określanie wartości procentowej użytkowników wirtualnych korzystających z danych pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Porady: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)