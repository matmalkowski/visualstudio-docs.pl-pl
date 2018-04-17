---
title: Analizowanie aktywności wirtualnego użytkownika testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 5f874b070e726374a20e821508115b5798f40b80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analizowanie aktywności wirtualnego użytkownika testów obciążenia w widoku szczegółów analizatora testu obciążenia

**Wykres aktywności użytkownika wirtualnego**

 ![Wykres aktywności użytkownika wirtualnego](../test/media/virtual_actchart.png "Virtual_ActChart")

 Widok szczegółów wyświetla wirtualnego wykres aktywności użytkownika, który służy do wizualnego analizowanie, co poszczególnych wirtualnych użytkowników podczas ładowania testów. Wykres aktywności użytkownika wirtualnego umożliwia Zobacz wzorców aktywności użytkownika, wzorce obciążenia skorelowania testy zakończone niepowodzeniem lub wolne i żądań z innych działań wirtualnego użytkownika w temacie. Wirtualnego wykres aktywności użytkownika mogą również ułatwić określenie wzrostów użycia procesora CPU, przerwy w żądań na sekundę i jakie testów lub stron były uruchomione podczas wzrostów i porzucania.

> [!NOTE]
> Przed uruchomieniem testu obciążenia, dla którego chcesz użyć wykres szczegóły aktywności wirtualnego użytkownika, należy sprawdzić, czy **magazynowania szczegółów chronometrażu** właściwość jest ustawiona na **AllIndividualDetails** opcji za pomocą Edytor testów obciążenia wydajności. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zbierania szczegółowych informacji umożliwiających włączyć wirtualnego wykres aktywności użytkownika](../test/how-to-configure-load-tests-to-collect-full-details.md).

 **Panel szczegółów legendy**

 ![Panel szczegółów legendy](../test/media/ltest_detailslegend.png "LTest_DetailsLegend")

 Panel szczegółów Legenda jest widoczna w wirtualnej wykres aktywności użytkownika. Szczegóły legendy okienko umożliwia filtrowanie testów, stron i transakcji dla kilku różnych kryteriów. Na przykład możesz usunąć niektóre testy z widoku, lub Usuń wszystkie testy pomyślne lub usunąć testy, których nie powiodła się z niektórych błędów. Można również usunąć wszystkie testy, które nie mają dzienników.

 Można wyróżnić testy, których nie powiodła się, który zawiera wszystkie testy nie powiodły się pokolorowane kolorem czerwonym. Można też wyróżnić testy, które mają dzienników testu. Testy z dziennikami będzie kolor na zielono.

 **Filtrowanie wyników panelu**

 ![Filtrowanie wyników panel](../test/media/ltest_filterresults.png "LTest_FilterResults")

 Panel wyników filtru jest widoczny w wirtualnej wykres aktywności użytkownika. Panel wyników filtru można filtrować według następujących czynności:

-   **Pokaż tylko wyniki z dziennikami** wyświetla tylko wyniki mających dzienników testu skojarzonych z nimi.

-   **Pokaż wyniki pomyślnie** wyświetla wyniki powiodło się.

-   **Pokaż wyniki z błędami** wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone — tematy|
|-----------|-----------------------|
|**Skonfiguruj test obciążenia w celu użycia wirtualnej wykres aktywności użytkownika:** przed uruchomieniem testu obciążenia, który chcesz wyświetlić dane o aktywności użytkownika wirtualnego na, należy najpierw skonfigurować ustawienia właściwości testów obciążenia.|-   [Porady: Konfigurowanie zbierania szczegółowych, aby włączyć wykres aktywności użytkownika wirtualnego](../test/how-to-configure-load-tests-to-collect-full-details.md)|
|**Uruchamianie testów obciążenia:** po utworzeniu testu obciążenia i skonfigurować go w celu włączenia zbierania danych aktywności wirtualnego użytkownika, należy uruchomić testu, dopóki nie zostanie ukończone, aby wyświetlić wirtualnego wykres aktywności użytkownika.||
|**Wyświetlanie wyników testu obciążenia, które zawierają dane o aktywności wirtualnego użytkownika:** po testów obciążenia zostało utworzone, skonfigurowane i zakończy działanie, można wyświetlić dane o aktywności wirtualnego użytkownika przy użyciu wirtualnego wykres aktywności użytkownika.|-   [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Porady: analizowanie, co użytkownicy wirtualni podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Wyizolować problemy z wydajnością w testach obciążenia:** można wyizolować problemy z wydajnością w teście obciążenia sieci wirtualnych wykres aktywności użytkownika.|-   [Wskazówki: Używanie wykres aktywności użytkownika wirtualnego do izolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)