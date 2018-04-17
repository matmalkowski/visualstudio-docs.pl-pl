---
title: Eksportuj wyniki testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: ce17cba842faf56205d5769bbcccfcdce8db6fec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Porady: eksportowanie wyników testu obciążenia z repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyników testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testu obciążenia można zarządzać w edytorze testu obciążenia za pomocą **otwarte i zarządzanie wynikami testów obciążenia** okno dialogowe. Można otworzyć, importowanie, eksportowanie i usuwanie wyników testu obciążenia.

## <a name="to-export-results-from-a-repository"></a>Aby wyeksportować wyniki z repozytorium

1.  W projekcie testów wydajności i testów obciążeniowych sieci Web otwórz test obciążeniowy.

2.  Na pasku narzędzi osadzony, wybierz **otwarte i zarządzanie wynikami**.

     **Otwarte i zarządzanie wynikami testów obciążenia** zostanie wyświetlone okno dialogowe.

3.  W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążenia**, wybierz kontroler. Wybierz  **\<lokalnej — nie kontrolera >** do wyników dostępu przechowywane lokalnie.

4.  W **Pokaż wyniki dla następującego testu obciążenia**, wybierz testu obciążenia, którego chcesz wyświetlić wyniki. Wybierz  **\<Pokaż wyniki wszystkich testów >** Aby wyświetlić wszystkie wyniki wszystkich testów.

     Jeśli wyniki testu obciążenia są dostępne, pojawią się one w **wyników testów obciążenia** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, a **opis** zawiera opcjonalny opis, który zostanie dodany przed uruchomieniem testu. **Opis** kolumny zawiera krótkie opisy, które zostały wprowadzone w **komentarze analizy** dla tego wyniku testu.

5.  W **wyników testów obciążenia** Wybierz wynik. Można użyć klawisza Shift i/lub klawisza Ctrl, aby zaznaczyć więcej wyników i wyeksportować je do jednego pliku.

6.  Wybierz **wyeksportować**.

     **Eksportowanie wyników testów obciążenia** zostanie wyświetlone okno dialogowe.

7.  W **nazwę pliku** wpisz nazwę, a następnie wybierz pozycję **zapisać**.

     Wyniki zostaną wyeksportowane do pliku archiwum.

    > [!NOTE]
    > **Otwarte i zarządzanie wynikami testów obciążenia** okno dialogowe pozostanie otwarte po zostaną wyświetlone wyniki.

## <a name="see-also"></a>Zobacz także

- [Zarządzenie wynikami testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Porady: usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)