---
title: "Porady: importowanie wyników testu obciążenia do repozytorium w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 1d9f94641fe3249e6aa36b01b408abd66781b81f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Porady: importowanie wyników testu obciążenia do repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyników testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

 Wyniki testu obciążenia można zarządzać w edytorze testu obciążenia za pomocą **otwarte i zarządzanie wynikami testów obciążenia** okno dialogowe. Można otworzyć, importowanie, eksportowanie i usuwanie wyników testu obciążenia.

## <a name="to-import-results-into-a-repository"></a>Aby zaimportować wyników do repozytorium

1.  W projekcie testów wydajności i testów obciążeniowych sieci Web otwórz test obciążeniowy.

2.  Na pasku narzędzi osadzony, wybierz **otwarte i zarządzanie wynikami**.

     **Otwarte i zarządzanie wynikami testów obciążenia** zostanie wyświetlone okno dialogowe.

3.  W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążenia**, wybierz kontroler. Wybierz  **\<lokalnego >** do wyników dostępu przechowywane lokalnie.

     Jeśli wyniki testu obciążenia są dostępne, pojawią się one w **wyników testów obciążenia** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, a **opis** zawiera opcjonalny opis, który zostanie dodany przed uruchomieniem testu.

4.  Wybierz **importu**.

     **Importuj wyniki testu obciążenia** zostanie wyświetlone okno dialogowe.

5.  W **nazwę pliku** wpisz nazwę pliku wyników testu zarchiwizowane, a następnie wybierz pozycję **Otwórz**.

     \- lub -

     Przejdź do pliku, a następnie wybierz pozycję **Otwórz**.

    > [!NOTE]
    > Pliku wyników testu zarchiwizowany, który został określony w tym kroku musi został utworzony przez wykonanie operacji eksportowania.

     Wyniki zostały zaimportowane i są wyświetlane w **wyników testów obciążenia** listy.

## <a name="see-also"></a>Zobacz także

- [Zarządzenie wynikami testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)