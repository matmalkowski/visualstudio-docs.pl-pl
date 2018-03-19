---
title: "Ustawienia o właściwości magazynowania szczegółów chronometrażu dla testu obciążenia uruchamiania programu Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 7921f2b3438885f78588f23694537a95cc7841e3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Porady: określanie właściwości magazynowania szczegółów chronometrażu dla ustawień uruchomienia testu obciążenia

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić ustawienia, aby spełnić potrzeby testowania i cele.

Można edytować ustawienia wykonywania **magazynowania szczegółów chronometrażu** wartość właściwości w **właściwości** okna. **Magazynowania szczegółów chronometrażu** właściwość można ustawić dla każdego z następujących opcji:

-   **Wszystkie szczegóły poszczególnych:** zbiera i przechowuje poszczególne dane chronometrażu dla każdego testu, transakcji i strony biorącej testu.

    > [!NOTE]
    > **Wszystkie szczegóły poszczególnych** musi być zaznaczona opcja informacji danych wirtualnego użytkownika w wynikach testów obciążenia. Aby uzyskać więcej informacji, zobacz [analizowanie wirtualnego działań użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

-   **Brak:** nie zbiera żadnych szczegółów poszczególnych czas. Jednak wartości średnie są nadal dostępne.

-   **Statystyka tylko:** przechowuje dane poszczególnych czas, ale tylko jako danych percentyl. Spowoduje to zapisanie zasobów miejsca.

 **Zagadnienia dotyczące właściwości magazynowania szczegółów chronometrażu**

 Jeśli **magazynowania szczegółów chronometrażu** właściwość jest włączona, a następnie czas wykonywania każdego poszczególnych testu, transakcji i strony podczas testu obciążenia będą przechowywane w repozytorium wyników testów obciążenia. Dzięki temu danych percentyl 90 i 95 ma być wyświetlany w analizatorze testów obciążenia w tabelach testy, transakcji i strony.

 Jeśli **magazynowania szczegółów chronometrażu** właściwość jest włączona, ustawiając dla jej wartość albo **StatisticsOnly** lub **AllIndividualDetails**, wszystkie poszczególne testy, stron i Transakcje jest mierzony i danych percentyl jest obliczana na podstawie danych poszczególnych czas. Różnica jest to, że z **StatisticsOnly** opcji, po obliczeniu danych percentyl poszczególnych czas dane zostaną usunięte z repozytorium. Zmniejsza to ilość miejsca, która jest wymagana w repozytorium szczegółów chronometrażu są używane. Jednak warto przetwarzania danych szczegółów chronometrażu w inny sposób za pomocą narzędzi SQL, w którym to przypadku **AllIndividualDetails** opcja powinna być używana, dzięki czemu dane szczegółów chronometrażu są dostępne do przetworzenia. Ponadto jeśli właściwość jest ustawiona **AllIndividualDetails**, a następnie można analizowanie aktywności wirtualnego użytkownika za pomocą wykresu aktywności wirtualnego użytkownika w analizatorze testu obciążenia, po zakończeniu testu obciążenia uruchomione. Aby uzyskać więcej informacji, zobacz [analizowanie wirtualnego działań użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

 Ilość miejsca wymaganego w repozytorium wyników testów obciążenia do przechowywania danych szczegółów chronometrażu mogą być bardzo duże, szczególnie w przypadku testów obciążenia jest już uruchomiona. Ponadto czas przechowywania tych danych w teście obciążenia, które repozytorium wyników na końcu testu obciążenia jest dłuższy, ponieważ te dane są przechowywane w agentach testu obciążenia do momentu zakończenia testu obciążenia wykonywania, które dane są przechowywane w repozytorium. **Magazynowania szczegółów chronometrażu** właściwości jest domyślnie włączona. Jeśli jest to problem w środowisku do testowania, możesz ustawić **magazynowania szczegółów chronometrażu** do **Brak**.

 Dane chronometrażu szczegółowe informacje są przechowywane w pliku LoadTestItemResults.dat podczas uruchamiania i są wysyłane do kontrolera, po zakończeniu testu obciążenia. Dla testu obciążenia uruchomione przez długi czas trwania rozmiar pliku jest duży. Jeśli na komputerze agenta nie jest wystarczająco dużo miejsca, będzie to problemu.

 Jeśli uaktualniasz projektu w poprzedniej wersji programu Visual Studio test obciążenia, poniżej procedurę można włączyć kolekcji szczegółach.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Aby skonfigurować właściwości magazynowania szczegółów chronometrażu w teście obciążenia

1.  Otwórz testu obciążenia w edytorze testu obciążenia.

2.  Rozwiń węzeł **parametrów uruchomieniowych** węzła w teście obciążenia.

3.  Wybierz ustawienia wykonywania, które chcesz skonfigurować, na przykład **Settings1 Uruchom [Active]**.

4.  Otwórz okno właściwości. Na **widoku** menu, wybierz opcję **okna właściwości**.

5.  W obszarze **wyniki** kategorii, wybierz **magazynowania szczegółów chronometrażu** właściwości i wybierz **wszystkie szczegóły poszczególnych**.

     Po skonfigurowaniu **wszystkie szczegóły poszczególnych** ustawienie **magazynowania szczegółów chronometrażu** właściwości, można uruchomić testu obciążenia i wyświetlić wirtualnego wykres aktywności użytkownika. Aby uzyskać więcej informacji, zobacz [porady: analizowanie co wirtualnych użytkowników są czynności podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Wskazówki: Używanie wykres aktywności użytkownika wirtualnego do izolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)