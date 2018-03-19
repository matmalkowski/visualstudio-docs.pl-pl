---
title: "Ustawienia uruchomienia testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: d278323bd816a801d94d2d1c18755111afa43eed
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="load-test-run-settings-properties"></a>Właściwości ustawień przebiegu testu obciążenia

Ustawienia przebiegu testu obciążenia określić różnych innych ustawień, takich jak czas trwania testu, poziom szczegółowości zbierania wyników i zbiory liczników, które są zbierane podczas uruchamiania testu. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Początkowego przebiegu ustawienie jest dodawany do testów obciążenia podczas tworzenia testu obciążenia za pomocą załadować Test Kreator nowego.

 W poniższych tabelach opisano różne właściwości dla ustawień uruchomienia testu obciążenia. Właściwości te można modyfikować, dopasowując do konkretnych wymagań dotyczących testowania obciążeniowego.

 Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień uruchomienia testu obciążenia](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Ogólne właściwości

|Właściwość|Definicja|
|--------------|----------------|
|**Opis**|Opis ustawienia uruchamiania.|
|**Maksymalny błąd według typu**|Maksymalna liczba błędów na typ do zapisania podczas testu obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli konieczne, ale spowoduje to również spowoduje zwiększenie rozmiaru i czasu przetwarzania wyniku testu obciążenia.|
|**Raportowanych adresów URL żądania maksymalna**|Maksymalna liczba unikatowych testu wydajności sieci Web żądania adresów URL, na którym raport wyników w teście obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli konieczne, ale spowoduje to również spowoduje zwiększenie rozmiaru i czasu przetwarzania wyniku testu obciążenia.|
|**Maksymalna naruszenia progu**|Maksymalna liczba naruszeń progu do zapisania podczas testu obciążenia.<br /><br /> Można zwiększyć tę liczbę, jeśli konieczne, ale spowoduje to również spowoduje zwiększenie rozmiaru i czasu przetwarzania wyniku testu obciążenia.|
|**Uruchom testy jednostkowe w domenie aplikacji**|Wartość logiczna określająca, czy podczas testu obciążenia zawiera testy jednostkowe oddzielna domena aplikacji ma być uruchamiany każdego zestawu testowego jednostki. Ustawienie domyślne to True.<br /><br /> Jeśli testy jednostkowe nie wymagają oddzielnego domeny lub app.config pliku aplikacji do poprawnego działania, testy jednostkowe mogą szybsze za pomocą ustawienia wartości tej właściwości, aby `False`.|
|**Nazwa**|Nazwa ustawienia Uruchom, w jakiej występuje w **parametrów uruchomieniowych** węzła **edytora testu obciążenia**.|
|**Poziom walidacji**|Definiuje najwyższego poziomu reguły sprawdzania poprawności, które zostanie uruchomione w teście obciążenia. Reguły sprawdzania poprawności są skojarzone z żądań testu wydajności sieci Web. Każda reguła sprawdzania poprawności ma poziom weryfikacji skojarzone: **wysokiej**, **średni**, lub **małej**. Tego testu obciążenia. ustawienia będzie określać weryfikacji, które reguły będzie uruchamiane podczas testu wydajności sieci Web w teście obciążenia. Na przykład, jeśli działa to ustawienie ma ustawioną **średni**, wszystkie reguły walidacji oznaczone jako **średni**, lub **małej** zostanie uruchomiona.|

## <a name="logging-properties"></a>Właściwości rejestrowania

|Właściwość|Definicja|
|--------------|----------------|
|**Dzienniki maksymalną testów**|Określa maksymalną liczbę dzienników testu do zapisania podczas testu obciążenia. Jeśli wprowadzono wartość maksymalną liczbę dzienników testu zostanie osiągnięty, test obciążenia zostanie zatrzymane zbieranie dzienników. W związku z tym dzienniki będą zbierane na początku testu nie zakończenia. Test obciążenia będzie nadal działać, dopóki zostanie zakończona.|
|**Zapisz częstotliwość zapisów w dzienniku dla ukończonych testów**|Określa częstotliwość, w którym zostanie zapisany dziennik testu. Liczba wskazuje, że jeden poza co podana liczba testów zostanie zapisany dziennik testu. Na przykład wprowadzenie wartości 10 określa, czy dziesiątym dniu, dwadzieścia, trzydziestą i tak dalej będą zapisywane w dzienniku testu. Ustawienie wartości 0 określa żadnych dzienników testu zostaną zapisane.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: Określ, jak często zapisywane są dzienniki testów](../test/how-to-specify-how-frequently-test-logs-are-saved.md)|
|**Zapisz dziennik podczas niepowodzenia testu**|Wartość logiczna, która określa, czy jeśli zapisywane są dzienniki testów, jeśli test zakończy się niepowodzeniem w teście obciążenia. Wartość domyślna to `True`.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: Określanie, czy niepowodzenia testu są zapisywane w dziennikach testów](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

 Aby uzyskać więcej informacji, zobacz [modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Właściwości wyników

|Właściwość|Definicja|
|--------------|----------------|
|**Typ magazynu**|Sposób przechowywania liczników wydajności, które są uzyskiwane w teście obciążenia. Dostępne są następujące opcje:<br /><br /> -   **Baza danych** -wymaga bazy danych SQL, który ma **magazynu wyników testów obciążenia**.<br />-   **Brak**.|
|**Magazynowania szczegółów chronometrażu**|To jest używany w celu określenia, które szczegóły będą przechowywane w **magazynu wyników testów obciążenia**. Dostępne są trzy wartości:<br /><br /> -   **AllIndividualDetails** — zbieranie i przechowywanie wartości poszczególnych czas dla każdego testu, transakcji i strony, które zostało Uruchom lub wystawiony podczas testu obciążenia w **magazynu wyników testów obciążenia**. Jest wymagany, jeśli zamierzasz używać wykresu aktywności wirtualnego użytkownika w analizatorze testów obciążenia.<br />     Aby uzyskać więcej informacji, zobacz [analizowanie wirtualnego działań użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Brak** — nie zbierają żadnych wartości poszczególnych czas. Jest to wartość domyślna dla programu Visual Studio 2013 Update 4 i nowszych wersjach.<br />-   **StatisticsOnly** — zbieranie i przechowywanie statystyk zamiast przechowywania poszczególnych czas wartości dla każdego testu, transakcji i strony, która została wykonana lub wystawiony podczas testu obciążenia w **magazynu wyników testów obciążenia**.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Właściwości śledzenia SQL

|Właściwość|Definicja|
|--------------|----------------|
|**Minimalny czas trwania operacji śledzenia SQL**|Minimalny czas trwania operacji SQL do przechwycenia przez śledzenie programu SQL Server, w milisekundach. Na przykład dzięki temu można zignorować operacji kończące szybko Jeśli próbujesz odnaleźć operacji SQL, które są wolne pod obciążeniem.|
|**Ciąg połączenia śledzenia SQL**|Parametry połączenia, które jest używane do dostępu do bazy danych do śledzenia.|
|**Katalog śledzenia SQL**|Lokalizacja, w którym plik śledzenia SQL jest umieszczany po zakończeniu śledzenia. Ten katalog musi mieć uprawnienia do zapisu dla programu SQL Server i Odczyt dla kontrolera.|
|**Włączonego śledzenia SQL**|Umożliwia to śledzenie operacji SQL. Wartość domyślna to `False`.|

## <a name="test-iterations-properties"></a>Właściwości iteracji testu

|Właściwość|Definicja|
|--------------|----------------|
|**Iteracje testu**|Określa liczbę pojedynczych testów do uruchomienia przed zakończeniem testu obciążenia. Ta właściwość jest stosowana tylko w przypadku właściwości "Użyj iteracjami testu" `True`.|
|**Użyj iteracjami testu**|Jeśli jest używana iteracje testu `True`, a następnie uruchamia test obciążenia, dopóki nie osiągnie liczbę pojedynczych testów zakończona w ramach testu obciążenia liczba, która jest określona przez właściwość "Iteracje testu". W takim przypadku na podstawie czasu ustawienia, które są Rozgrzewki czas trwania, uruchom czas i czas ochładzania są ignorowane. Jeśli jest "Użyj iteracjami testu" `False`Zastosuj ustawienia czasu, a "Iteracjami testu" jest ignorowany.|

 Aby uzyskać więcej informacji, zobacz [porady: Określanie liczby iteracji testowych w ustawieniach uruchamiania](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Właściwości chronometrażu

|Właściwość|Definicja|
|--------------|----------------|
|**Czas ochładzania**|Czas trwania okresu ochładzania testu wyrażoną w formacie hh: mm:. Poszczególne testy w ramach testu obciążenia może nadal działać po zakończeniu testu obciążenia. Podczas okresu ochładzania te testy nadal aż do chwili zakończenia lub zostanie osiągnięty koniec okresu ochładzania. Domyślnie jest Brak okresu ochładzania, a poszczególne testy są kończone po zakończeniu zgodnie z ustawieniem Uruchom czas trwania testu obciążenia.|
|**Czas trwania**|Długość testu, w formacie hh: mm:.|
|**Częstotliwość próbkowania**|Interwał, w której wartości licznika wydajności, w formacie hh: mm:.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Ciepłych się czas trwania**|Czasu między rozpoczęciem testu i kiedy rozpocząć rejestrowany w formacie hh: mm: próbek danych. Jest to często używane do wykonania kroków obciążenia wirtualnych użytkowników do osiągnięcia na poziomie obciążenia przed rozpoczęciem rejestrowania przykładowe wartości. Przykładowe wartości, które są przechwytywane przed zakończeniem okresu rozgrzania są wyświetlane w **analizatora testu obciążenia**.|

## <a name="webtest-connections-properties"></a>Właściwości połączenia w teście sieci Web

|Właściwość|Definicja|
|--------------|----------------|
|**Model połączenia w teście sieci Web**|Kontroluje do użycia połączenia z agentem testu obciążenia do serwera sieci Web dla testów wydajności sieci Web, które są uruchamiane w teście obciążenia. Dostępne są trzy opcje model połączenia testu sieci Web wydajności:<br /><br /> - **Connection Per User** modelu symuluje zachowania użytkownika, który jest prawdziwe przeglądarce. W przypadku symulacji programu Internet Explorer 6 lub Internet Explorer 7, każdego wirtualnego użytkownika, który jest uruchamianie testu wydajności sieci Web korzysta z jednego lub dwóch dedykowanych połączeń z serwerem sieci Web. Pierwszy połączenie zostanie nawiązane, gdy jest to pierwsze żądanie testu wydajności sieci Web. Drugie połączenie może być używany, gdy strona zawiera więcej niż jedno żądanie zależnych. Te żądania są wysyłane równolegle przy użyciu dwóch połączeń. Połączenia te są używane ponownie dla kolejnych żądań w teście wydajności sieci Web. Połączenia zostaną zamknięte po zakończeniu testu wydajności sieci Web. Wadą tego modelu jest, że liczba połączeń jest otwarty na komputerze agenta może być wysokie (maksymalnie dwa razy obciążenie użytkownikami). W rezultacie zasoby, które są wymagane do obsługi tej liczby połączeń wysokiej może ograniczyć obciążenie użytkownikami, które mogą być określane od agenta testu obciążenia pojedynczego. Gdy symulacji programu Internet Explorer 8, są obsługiwane sześciu równoczesnych połączeń.<br />- **Puli połączeń** modelu oszczędza zasoby na agenta testu obciążenia za pomocą udostępniania połączenia z serwerem sieci Web wśród wielu wirtualnych użytkowników testu wydajności sieci Web. Jeśli obciążenie użytkownikami przekracza rozmiar puli połączeń, testów wydajności sieci Web, które są uruchamiane przez różnych użytkowników wirtualnych będzie Udostępnianie połączenia. To może oznaczać, że jeden test wydajności sieci Web może być konieczne poczekanie przed generuje żądanie, używając innego testu wydajności sieci Web jest połączenie. Średni czas, który przed przesyła żądanie oczekuje testu wydajności sieci Web jest śledzony przez obciążenia testu licznika wydajności Średni czas oczekiwania połączenia. Liczba ta powinna być mniejsza niż średni czas odpowiedzi dla strony. Jeśli nie, prawdopodobnie jest za mały rozmiar puli połączeń.<br />- **Connection Per Test Iteration** modelu Określa użycie dedykowanych połączeń dla każdej iteracji testu.|
|**Rozmiar puli połączeń WebTest**|Określa maksymalną liczbę połączeń między agentem testu obciążenia i serwer sieci Web. Dotyczy to tylko **puli połączeń** modelu.|

##  <a name="LoadTestRunSettingsHowToChange"></a> Zmiana ustawień właściwości
 Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. Jednocześnie można używać tylko jednego ustawienia uruchamiania i należy określić uruchamiania ustawienia do użycia przez oznaczenie jej jako aktywne. Na przykład zobacz [porady: Wybierz aktywne ustawienie uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

### <a name="to-change-run-settings"></a>Aby zmienić ustawienia uruchamiania

1.  Otwórz testu obciążenia.

2.  Rozwiń węzeł **parametrów uruchomieniowych** folderu.

3.  Wybierz **parametrów uruchomieniowych** węzła.

4.  Na **widoku** menu, wybierz **okna właściwości**.

     **Okna właściwości** wyświetleniem i są wyświetlane właściwości dla wybranych ustawień uruchamiania.

5.  Użyj **okna właściwości** do zmiany ustawień uruchamiania. Na przykład zmienić czas trwania testu na **00:05:00** testu przez pięć minut.

    > [!NOTE]
    > Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).

6.  Po zakończeniu zmiany właściwości zapisać testu obciążenia. Na **pliku** menu, wybierz **zapisać**.

> [!NOTE]
> Mapowanie zestawu liczników należą również do parametrów uruchomieniowych. Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)