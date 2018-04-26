---
title: Tworzenie programu Visual Studio raportów wydajności testu obciążenia za pomocą programu Microsoft Excel
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b82a35ed56c0930b8d9c0ff8ec7bfcbd008a7648
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Porady: tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel

Można generować raportów testu obciążenia programu Microsoft Excel, które są oparte na dwóch lub więcej wyników testu. Dostępne są dwa typy raportów testu obciążenia:

-   **Uruchom porównanie** spowoduje to utworzenie zestaw raportów, który porównuje dane z dwóch wyników testu obciążenia przy użyciu tabel i wykresów słupkowych.

-   **Trend** mogą generować Analiza trendu na dwóch lub więcej wyników testu obciążenia. Wyniki są wyświetlane przy użyciu wykresów liniowych, ale dane są dostępne w raportach tabeli przestawnej.

> [!TIP]
> Można też ręcznie tworzyć raporty programu Microsoft Word przez kopiowanie i wklejanie danych z widok podsumowania, widoku wykresów i tabel widoku. Zobacz [porady: ręczne tworzenie raportu wydajności testu obciążenia za pomocą programu Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

 Albo może być stosowany do udostępniania danych wydajności z zainteresowanymi stronami i przekazywać czy ogólnej wydajności i kondycji systemu programu będzie niedługo lepsze np.

 Definicje raportów są przechowywane w bazie danych testu obciążenia. Podczas zapisywania raportu definicja raportu jest zapisywany w bazie danych i później mogą być ponownie używane.

 Ponadto skoroszytu programu Excel można udostępniać uczestników, aby uczestnicy projektu nie masz połączenia z bazą danych, aby wyświetlić raport.

> [!NOTE]
> Można udostępniać skoroszytu programu Excel. jednak tylko użytkownikom mającym zainstalowanego na komputerze programu Visual Studio będzie można zmodyfikować arkuszy kalkulacyjnych. Inni użytkownicy nie będą widzieć **raport testu obciążenia** opcji na Wstążce pakietu Office, ale będą mogli wyświetlać skoroszytu.

 Poniższej ilustracji przedstawiono przykładowy raport pokazujący korelacji między spadek szybkości transakcji (Aktualizuj koszyk) i zwyrodnienie licznika (% procesora). To wskazuje potencjalny problem w kodzie aplikacji, a nie bazy danych lub w sieci i są odpowiednimi kandydatami do diagnozowania za pomocą profilera platformy ASP.NET.

 ![Potencjalny problem w kodzie aplikacji](../test/media/lt_excel.png "LT_Excel")

 Raporty programu Excel albo można wygenerować w analizatora testu obciążenia za pomocą **Utwórz raport programu Excel** przycisku w pasku narzędzi lub z programu Excel za pomocą **raport testu obciążenia** opcji **testu obciążenia**  karty wstążki pakietu Office.

> [!NOTE]
> Jeśli dodasz komentarze do testu obciążenia, będą wyświetlane w raporcie programu Excel. Aby uzyskać więcej informacji, zobacz [porady: dodawanie komentarzy podczas analizowania testu obciążenia ukończone](../test/how-to-add-comments-on-a-completed-load-test.md).

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Do generowania raportów porównania testu obciążenia przy użyciu programu Excel

1.  Aby wygenerować raport, należy uruchomić testu obciążenia.

2.  Można utworzyć raportów testu obciążenia programu Excel na dwa sposoby:

    1.  Po zakończeniu pracy w teście obciążenia **wyników testu obciążenia** wybierz pozycję **Utwórz raport programu Excel** przycisku w pasku narzędzi.

        > [!NOTE]
        > Jeśli **Utwórz raport programu Excel** przycisk jest wyłączony na pasku narzędzi przeglądarki wyników testu wydajności sieci Web, może być konieczne uruchomienie programu Microsoft Excel jeden czas przed jest włączone. Po zainstalowaniu programu Visual Studio Enterprise, Visual Studio Enterprise obciążenia testu dodatek jest kopiowany do komputera dla programu Microsoft Excel; Jednak aby ukończyć proces instalacji dodatku należy uruchomić program Microsoft Excel.

     Program Microsoft Excel otwiera z **Generuj raport testu obciążenia** kreatora.

     —lub—

    1.  Otwórz program Microsoft Excel, wybierz **testu obciążenia** kartę na Wstążce pakietu Office, a następnie wybierz pozycję **raport testu obciążenia**.

         **Generuj raport testu obciążenia** zostanie wyświetlony Kreator.

    2.  W **wybierz bazę danych zawierającą testy obciążenia** w obszarze **nazwy serwera**, wpisz nazwę serwera, zawierającego wyniki testu obciążenia.

    3.  W **Databasename** listy rozwijanej wybierz bazę danych zawierającą wyników testu obciążenia.

3.  W **jak chcesz wygenerować raport** Sprawdź, czy **Utwórz raport** jest zaznaczone, a następnie wybierz **dalej**.

4.  W **typ raportu chcesz wygenerować** Sprawdź, czy **Uruchom porównanie** jest zaznaczone, a następnie wybierz **dalej**.

5.  W **szczegóły raportu testu obciążenia Enter** wpisz nazwę dla raportu w **Nazwa raportu**.

6.  Wybierz test obciążenia, aby wygenerować raport, a następnie wybierz pozycję **dalej**.

7.  W **wybierz przebiegi do raportu** w obszarze **wybierz co najmniej jeden przebieg do dodania do raportu**, wybierz dwa załadować wyniki testów, które chcesz porównać w raporcie, a następnie wybierz pozycję **dalej**.

    > [!NOTE]
    > Porównanie raportu dotyczącego wyników testów obciążenia dwóch można generować tylko. Jeśli zostanie wybrany wynik testu albo obciążenia jeden lub więcej niż dwa wyniki testu obciążenia, zostanie wyświetlony komunikat ostrzegawczy.

8.  W **Wybierz liczniki do raportu** w obszarze **wybierz na lub większej liczby liczników w celu dodania do raportu** rozwijania listy liczników jest dostępna Dostosowywanie raportu. Wybierz liczniki, które chcesz porównać dwa przebiegi wybranego testu w raporcie, a następnie wybierz pozycję **Zakończ**.

9. Raport skoroszytu programu Excel jest generowany z arkusza kalkulacyjnego następujące karty:

    -   **Spis treści** — Wyświetla nazwę raportu testu obciążenia i udostępnia spis treści z łączami do różnych kart w raporcie.

    -   **Uruchamia -** zawiera szczegółowe informacje, na których dwa przebiegi są porównywane w raporcie.

    -   **Test porównawczy -** szczegółowe wykres słupkowy na regresji wydajności i ulepszenia między dwa przebiegi porównywane.

    -   **Porównanie strony -** zawiera wykres słupkowy i wydajności procent porównania danych między dwa przebiegi na różnych stronach w uruchomień testów.

    -   **Porównanie - maszyny** umożliwia porównanie danych między dwa przebiegi oparte na maszynach, które były używane.

    -   **Błąd porównania -** porównuje typy błędów napotkano między dwa przebiegi i liczby wystąpień.

    > [!TIP]
    > Raporty lepsze kilka właściwości są dostępne w testów obciążenia oraz testy wydajności sieci Web umożliwiające bardziej rozbudowane raporty. Żądanie strony ma dwie właściwości, które są przedstawiane w raportach: cel i nazwy raportowania. Czas odpowiedzi strony będą raportowane przed cel i raportowania nazwa będzie używana zamiast adresu URL w raportach. W czasie testu obciążenia Uruchom ustawienia w obszarze Zarządzanie zbiorami liczników tagów właściwości są prezentowane w nazw maszynę raport. Jest to bardzo przydatne do opisywania rolę określonego komputera w raporcie.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Aby wygenerować raporty o trendach testu obciążenia przy użyciu programu Excel

1.  Aby wygenerować raport, należy uruchomić testu obciążenia.

2.  Można utworzyć raportów testu obciążenia programu Excel na dwa sposoby:

    1.  Po zakończeniu pracy w teście obciążenia **wyników testu obciążenia** wybierz pozycję **Utwórz raport programu Excel** przycisku w pasku narzędzi.

        > [!NOTE]
        > Jeśli **Utwórz raport programu Excel** przycisk jest wyłączony na pasku narzędzi przeglądarki wyników testu wydajności sieci Web, może być konieczne uruchomienie programu Microsoft Excel jeden czas przed jest włączone. Po zainstalowaniu programu Visual Studio Enterprise, Visual Studio Enterprise obciążenia testu dodatek jest kopiowany do komputera dla programu Microsoft Excel; Jednak aby ukończyć proces instalacji dodatku należy uruchomić program Microsoft Excel.

     Program Microsoft Excel otwiera z **Generuj raport testu obciążenia** kreatora.

     —lub—

    1.  Otwórz program Microsoft Excel, wybierz **testu obciążenia** kartę na Wstążce pakietu Office, a następnie wybierz pozycję **raport testu obciążenia**.

         **Generuj raport testu obciążenia** zostanie wyświetlony Kreator.

    2.  W **wybierz bazę danych zawierającą testy obciążenia** w obszarze **nazwy serwera**, wpisz nazwę serwera, zawierającego wyniki testu obciążenia.

    3.  W **Databasename** listy rozwijanej wybierz bazę danych zawierającą wyników testu obciążenia.

3.  W **jak chcesz wygenerować raport** Sprawdź, czy **Utwórz raport** jest zaznaczone, a następnie wybierz **dalej**.

4.  W **typ raportu chcesz wygenerować** Sprawdź, czy **Trend** jest zaznaczone, a następnie wybierz **dalej**.

5.  W **szczegóły raportu testu obciążenia Enter** wpisz nazwę dla raportu w **Nazwa raportu**.

6.  Wybierz test obciążenia, aby wygenerować raport, a następnie wybierz pozycję **dalej**.

7.  W **wybierz przebiegi do raportu** w obszarze **wybierz co najmniej jeden przebieg do dodania do raportu**, wybierz wyniki testu obciążenia, które chcesz porównać w raporcie, a następnie wybierz pozycję **dalej**.

8.  W **Wybierz liczniki do raportu** w obszarze **wybierz na lub większej liczby liczników w celu dodania do raportu**, można dostosować raport, jest rozwijana lista liczników. Wybierz liczniki, które chcesz porównać do analizy trendów i wybierz polecenie **Zakończ**.

10. Raport jest generowany z tabeli treści, która ma linki do różnych kart skoroszytu programu Excel generowane w raporcie. Łącza są oparte na wybrane w raporcie trendu liczniki. Na przykład jeśli liczniki domyślna wybrana w kroku 7, następnie raportu spowoduje wygenerowanie danych, które są prezentowane w osobnych kartach w programie Excel dla każdego licznika opisanych w kroku 7. Dane, które jest generowany dla każdego licznika są prezentowane w stylu trend wykresy.

    > [!TIP]
    > Raporty lepsze kilka właściwości są dostępne w testów obciążenia oraz testy wydajności sieci Web umożliwiające bardziej rozbudowane raporty. Żądanie strony ma dwie właściwości, które są przedstawiane w raportach: cel i nazwy raportowania. Czas odpowiedzi strony będą raportowane przed cel i raportowania nazwa będzie używana zamiast adresu URL w raportach. W czasie testu obciążenia Uruchom ustawienia w obszarze Zarządzanie zbiorami liczników tagów właściwości są prezentowane w nazw maszynę raport. Jest to bardzo przydatne do opisywania rolę określonego komputera w raporcie.

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Wyniki testu obciążenia i raporty zawierają potencjalnie poufnych informacji, które mogą służyć do tworzenia złamanie komputera lub sieci. Wyniki testu obciążenia i raporty zawierają nazwy komputera i parametry połączenia. Należy pamiętać o tym kiedy raportów testu obciążenia są udostępniane innym osobom.

## <a name="see-also"></a>Zobacz także

- [Raportowanie wyników testów obciążenia do potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md)