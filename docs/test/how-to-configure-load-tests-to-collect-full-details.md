---
title: Zbieranie wszystkich szczegółów dla użytkowników wirtualnych testy obciążeniowe w programie Visual Studio
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
ms.openlocfilehash: 70930a09f01450d59b44678ebd26d7e742af7294
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379628"
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>Porady: Konfigurowanie testów do zbierania szczegółowych informacji umożliwiających włączenie działań wirtualnego użytkownika w wynikach testu obciążenia

Aby użyć **wykres aktywności wirtualnych użytkowników** dla testu obciążenia, należy skonfigurować test obciążenia w celu zbierania szczegółowych informacji. Aby skonfigurować test obciążenia, aby to zrobić, wybierz **wszystkie szczegółowe dane** ustawienie **przechowywanie informacji** właściwości skojarzonej z testu obciążenia. W tym trybie testu obciążeniowego będzie zbierać szczegółowe informacje dotyczące każdego testu, strony i transakcji.

 Jeśli uaktualniasz projekt z poprzedniej wersji programu Visual Studio test obciążeniowy, wykonaj kroki poniższej procedury w celu umożliwienia zbierania pełnych szczegółów.

 **Wszystkie szczegółowe dane** ustawienie **przechowywanie informacji** właściwość można ustawić na dowolną z następujących opcji:

-   **Wszystkie szczegółowe dane:** zbiera i przechowuje dane o poszczególnych chronometrażach dla każdego testu, transakcji i strony podczas testu.

    > [!NOTE]
    > **Wszystkie szczegółowe dane** należy wybrać opcję, aby włączyć informacje o danych użytkownika wirtualnego w wyniki testu obciążenia.

-   **Brak:** nie gromadzi żadnych indywidualnych szczegółów chronometrażu. Jednakże wartości średnie są nadal dostępne.

-   **Tylko statystyki:** przechowuje dane o poszczególnych chronometrażach, ale tylko jako danych percentyl. Oszczędza to zasoby miejsca.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Aby skonfigurować właściwości magazynowania szczegółów chronometrażu w teście obciążeniowym

1.  Otwórz test obciążenia w **edytora testu obciążenia**.

2.  Rozwiń **parametrów uruchomieniowych** węzła w teście obciążeniowym.

3.  Wybierz polecenie dotyczące wykonywania ustawień, które chcesz skonfigurować, na przykład **Uruchom ustawienia1 [aktywne]**.

4.  Otwórz **właściwości** okna. Na **widoku** menu, wybierz opcję **okno właściwości**.

5.  W obszarze **wyniki** kategorii, wybierz **przechowywanie informacji** właściwości i wybierz pozycję **wszystkie szczegółowe dane**.

     Po skonfigurowaniu **wszystkie szczegółowe dane** ustawienie **przechowywanie informacji** właściwości, można uruchamiać obciążenia testowania i wyświetlania **wykres aktywności wirtualnych użytkowników**. Aby uzyskać więcej informacji, zobacz [porady: analizowanie, co robią użytkownicy wirtualni podczas testu obciążeniowego](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: Używanie wykresu wirtualnego aktywności użytkownika umożliwiającego Wyizolowanie problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)