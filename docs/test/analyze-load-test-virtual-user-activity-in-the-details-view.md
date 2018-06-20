---
title: Analizowanie aktywności wirtualnego użytkownika testów obciążenia w programie Visual Studio
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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 5ab42b66fca32dc5325ce0cb4d78fbb53df8b90f
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36233798"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analizowanie aktywności wirtualnego użytkownika testów obciążenia w widoku szczegółów analizatora testu obciążenia

**Wykres aktywności użytkownika wirtualnego**

 ![Wykres aktywności użytkownika wirtualnego](../test/media/virtual_actchart.png)

 **Szczegóły** wyświetlić Wyświetla **wykres aktywności użytkownika wirtualnego**, który służy do wizualnego analizowanie poszczególnych wirtualnych użytkowników czy podczas testu obciążenia. **Wykres aktywności użytkownika wirtualnego** umożliwia Zobacz wzorców aktywności użytkownika, wzorce obciążenia, skorelowania testy zakończone niepowodzeniem lub wolne i wyświetlania żądań z innych działań wirtualnego użytkownika. **Wykres aktywności użytkownika wirtualnego** można także ustalić gwałtowny wzrost użycia procesora CPU, przerwy w żądań na sekundę, Pomoc i co testów lub stron, które były uruchomione podczas wzrostów i porzucania.

> [!NOTE]
> Przed uruchomieniem testu obciążenia, dla którego chcesz użyć **wykres szczegóły aktywności użytkownika wirtualnego**, należy sprawdzić, czy **magazynowania szczegółów chronometrażu** właściwość jest ustawiona na  **AllIndividualDetails** opcji za pomocą edytora testu obciążenia wydajności. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zbierania szczegółowych, aby włączyć wykres aktywności użytkownika wirtualnego](../test/how-to-configure-load-tests-to-collect-full-details.md).

 **Panel szczegółów legendy**

 ![Panel szczegółów legendy](../test/media/ltest_detailslegend.png)

 Jest widoczna w panelu szczegółów legendy **wykres aktywności użytkownika wirtualnego**. Szczegóły legendy okienko umożliwia filtrowanie testów, stron i transakcji dla kilku różnych kryteriów. Na przykład możesz usunąć niektóre testy z widoku, lub Usuń wszystkie testy pomyślne lub usunąć testy, których nie powiodła się z niektórych błędów. Można również usunąć wszystkie testy, które nie mają dzienników.

 Można wyróżnić testy, których nie powiodła się, który zawiera wszystkie testy nie powiodły się pokolorowane kolorem czerwonym. Można też wyróżnić testy, które mają dzienników testu. Testy z dziennikami będzie kolor na zielono.

 **Filtrowanie wyników panelu**

 ![Panel wyników filtru](../test/media/ltest_filterresults.png)

 Jest widoczna w panelu wyników filtr **wykres aktywności użytkownika wirtualnego**. Panel wyników filtru można filtrować według następujących czynności:

-   **Pokaż tylko wyniki z dziennikami** wyświetla tylko wyniki mających dzienników testu skojarzonych z nimi.

-   **Pokaż wyniki pomyślnie** wyświetla wyniki powiodło się.

-   **Pokaż wyniki z błędami** wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone — tematy|
|-----------|-----------------------|
|**Skonfiguruj test obciążenia w celu użycia wirtualnej wykres aktywności użytkownika:** przed uruchomieniem testu obciążenia, który chcesz wyświetlić dane o aktywności użytkownika wirtualnego na, należy najpierw skonfigurować ustawienia właściwości testów obciążenia.|-   [Porady: Konfigurowanie zbierania szczegółowych, aby włączyć wykres aktywności użytkownika wirtualnego](../test/how-to-configure-load-tests-to-collect-full-details.md)|
|**Uruchamianie testów obciążenia:** po utworzeniu testu obciążenia i skonfigurować go w celu włączenia zbierania danych aktywności wirtualnego użytkownika, należy uruchomić testu do czasu ukończenia w wymagany do wyświetlania **wykres aktywności użytkownika wirtualnego**.||
|**Wyświetlanie wyników testu obciążenia, które zawierają dane o aktywności wirtualnego użytkownika:** po testów obciążenia zostało utworzone, skonfigurowane i zakończy działanie, można wyświetlić dane o aktywności wirtualnego użytkownika używając **wykres aktywności użytkownika wirtualnego** .|-   [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Porady: analizowanie, co użytkownicy wirtualni podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Wyizolować problemy z wydajnością w testach obciążenia:** można użyć **wykres aktywności użytkownika wirtualnego** Aby wyizolować problemy z wydajnością w teście obciążenia sieci.|-   [Wskazówki: Używanie wykres aktywności użytkownika wirtualnego do izolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)