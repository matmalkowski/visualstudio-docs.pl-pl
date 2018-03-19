---
title: "Analizowanie wyników testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 2e44b6818d30c3452259b4249c047b40bd70bf43
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Porady: uzyskiwanie dostępu do wyników testu obciążenia w celu przeprowadzenia analizy

Po uruchomieniu testu obciążenia w edytorze testu obciążenia automatycznego otwierania wyników testu obciążenia i uruchamianie testu obciążenia jest wyświetlana w analizatorze testu obciążenia. Po uruchomieniu testu obciążenia z wiersza polecenia, można ręcznie dostępu wyników testu obciążenia.

Wynik testu obciążenia do testu obciążenia ukończone zawiera próbek licznika wydajności i informacje o błędzie, okresowo zebrane z komputerów na mocy testu. Duża liczba próbek licznika wydajności mogą być zbierane w trakcie uruchomienia testu obciążenia. Zbierane dane dotyczące wydajności zależy od długości uruchomienie testu, interwał próbkowania, liczbę komputerów w ramach testu, liczbę liczników zbieranych, modułów zbierających dane, które są skonfigurowane i poziomy rejestrowania. Dla testów obciążenia duża ilość zbieranych danych wydajności można łatwo kilku gigabajtów. Aby uzyskać więcej informacji, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

## <a name="to-access-a-load-test-result"></a>Aby uzyskać dostępu do wyniku testu obciążenia

1.  W projekcie testów wydajności i testów obciążeniowych sieci Web otwórz test obciążeniowy.

2.  Na pasku narzędzi edytora testu obciążenia, wybierz **otwarte i zarządzanie wynikami** przycisku.

     **Otwarte i zarządzanie wynikami** zostanie wyświetlone okno dialogowe.

3.  W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążenia**, wybierz kontroler. Wybierz  **\<lokalnego >-żaden kontroler** do wyników dostępu przechowywane lokalnie.

4.  W **Pokaż wyniki dla następującego testu obciążenia**, wybierz testu obciążenia, którego chcesz wyświetlić wyniki. Wybierz  **\<Pokaż wyniki wszystkich testów >** Aby wyświetlić wszystkie wyniki wszystkich testów.

     Jeśli wyniki testu obciążenia są dostępne, pojawią się one w **wyników testów obciążenia** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, a **opis** zawiera opcjonalny opis, który zostanie dodany przed uruchomieniem testu.

    > [!NOTE]
    > Wyniki są wyświetlane najnowsze wyniki na początku listy.

5.  W **wyników testów obciążenia** Wybierz wyniki testu obciążenia, aby analiza i wybierz pozycję **Otwórz**.

6.  Zostanie wyświetlone analizatora testu obciążenia. Wynik testu obciążenia wybrany jest wyświetlany w widoku podsumowania. Aby uzyskać więcej informacji, zobacz [omówienie podsumowanie wyników testu obciążenia](../test/load-test-results-summary-overview.md).

     Możesz zarządzać innych aspektów wyników testów obciążenia w okno dialogowe otwarte i zarządzanie wynikami, w tym importowanie, eksportowanie i usuwanie wyników testu obciążenia. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyników testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)