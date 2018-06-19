---
title: Zbieranie wszystkich szczegółów dla wirtualnych użytkowników dla obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cac171d6f0e1bcd91a89be799497b84dc15fc5a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967099"
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>Porady: konfigurowanie testów obciążenia w celu zbierania szczegółowych informacji umożliwiających włączenie działań wirtualnego użytkownika w wynikach testu

Aby użyć wirtualnego wykres aktywności użytkownika podczas testu obciążenia, należy skonfigurować test obciążenia w celu zbierania szczegółowych informacji. Aby skonfigurować testu obciążenia, aby to zrobić, wybierz **wszystkie szczegóły poszczególnych** ustawienie **magazynowania szczegółów chronometrażu** właściwości skojarzonej z testu obciążenia. W tym trybie testów obciążenia zbierze szczegółowe informacje na temat każdego testu, strony i transakcji.

 Jeśli uaktualniasz projektu w poprzedniej wersji programu Visual Studio test obciążenia, wykonaj kroki poniższej procedury można włączyć kolekcji szczegółach.

 **Wszystkie szczegóły poszczególnych** ustawienie **magazynowania szczegółów chronometrażu** właściwość można ustawić dla każdego z następujących opcji:

-   **Wszystkie szczegóły poszczególnych:** zbiera i przechowuje poszczególne dane chronometrażu dla każdego testu, transakcji i strony biorącej testu.

    > [!NOTE]
    > **Wszystkie szczegóły poszczególnych** musi być zaznaczona opcja informacji danych wirtualnego użytkownika w wynikach testów obciążenia.

-   **Brak:** nie zbiera żadnych szczegółów poszczególnych czas. Jednak wartości średnie są nadal dostępne.

-   **Statystyka tylko:** przechowuje dane poszczególnych czas, ale tylko jako danych percentyl. Spowoduje to zapisanie zasobów miejsca.

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