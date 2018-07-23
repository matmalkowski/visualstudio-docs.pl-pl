---
title: Eksportowanie wyników testu obciążenia w programie Visual Studio
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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 080bdfd79ee1fce4015fc2db9a695cb55c417165
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178773"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Porady: eksportowanie wyników testu obciążenia z repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyników testów obciążenia w repozytorium wyników testów obciążeniowych](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testu obciążeniowego można zarządzać z edytora testu obciążenia, używając **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe. Można otworzyć, importować, eksportować i usuwać wyniki testu obciążenia.

## <a name="to-export-results-from-a-repository"></a>Aby wyeksportować wyniki z repozytorium

1.  Od wydajności sieci web i obciążenia projektu testowego, otwórz test obciążenia.

2.  Na osadzonym pasku narzędzi wybierz **Otwórz i Zarządzaj wynikami**.

     **Otwórz i Zarządzaj wynikami testu obciążenia** zostanie wyświetlone okno dialogowe.

3.  W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążeniowego**, wybierz kontroler. Wybierz  **\<lokalnie - bez kontrolera >** aby przejść do wyników przechowywanych lokalnie.

4.  W **Pokaż wyniki następującego testu obciążeniowego**, zaznacz test obciążeniowy, którego wyniki chcesz wyświetlić. Wybierz  **\<Pokaż wyniki wszystkich testów >** aby zobaczyć wszystkie wyniki wszystkich testów.

     Jeśli wyniki testów obciążenia są dostępne, są wyświetlane w **wyniki testu obciążeniowego** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, i **opis** zawiera opcjonalny opis dodawany przed uruchomieniem testu. **Opis** krótkie opisy, które zostały wprowadzone w kolumnie jest wyświetlana **komentarze dotyczące analizy** dla tego wyniku testu.

5.  W **wyniki testu obciążeniowego** Wybierz wynik. Można użyć klawisza Shift i/lub klawisza Ctrl, aby zaznaczyć więcej wyników i wyeksportować je do jednego pliku.

6.  Wybierz **wyeksportować**.

     **Eksportuj wyniki testu obciążenia** pojawi się okno dialogowe.

7.  W **nazwy pliku** polu, wpisz nazwę, a następnie wybierz **Zapisz**.

     Wyniki zostaną wyeksportowane do pliku archiwum.

    > [!NOTE]
    > **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe pozostaje otwarty, po wyświetleniu wyników.

## <a name="see-also"></a>Zobacz także

- [Zarządzenie wynikami testów obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Porady: usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: importowanie wyników testu obciążenia z repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)