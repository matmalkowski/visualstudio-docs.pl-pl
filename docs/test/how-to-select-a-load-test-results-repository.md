---
title: "Porady: Wybieranie repozytorium wyników testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: a85606196b701f98e8fb65b4e92b3896ef7a6b2c
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-select-a-load-test-results-repository"></a>Porady: wybieranie repozytorium wyników testu obciążenia

Nie są ograniczone do magazynu lokalnego wyników. Często testów obciążenia są uruchamiane na zdalnym zestaw komputerów agenta. Agenci, razem z kontrolerem, można wygenerować więcej symulowanym obciążeniem niż dowolnego pojedynczego komputera. Aby uzyskać więcej informacji, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Mogą zostać zapisane wyniki testu z agentów programu lub komputera lokalnego do dowolnego serwera SQL, na którym utworzono magazynu wyników testów obciążenia. W obu przypadkach należy określić, które chcesz przechowywać wyniki testu obciążenia przy użyciu okna administrować kontrolerami testów.

Aby uzyskać więcej informacji na temat agentów, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

## <a name="identify-a-results-store-for-load-test-data"></a>Identyfikowanie magazynu wyników dla danych testu obciążenia

1.  W **Eksploratora rozwiązań**, otwórz plik testu obciążenia.

2.  Z **testu obciążenia** narzędzi wybierz **Zarządzanie kontrolerami testów**. Zostanie wyświetlone okno dialogowe Zarządzanie aplikacją Test Controller. Jeśli używasz agenta zdalnego, musisz wybrać kontrolera.

     ![Właściwości połączenia magazynu wyników testów obciążenia](../test/media/loadtestconnectionproperties.png "LoadTestConnectionProperties") właściwości połączenia magazynu wyników testów obciążenia

3.  W **magazynu wyników testu obciążenia**, kliknij (...), aby wyświetlić **właściwości połączenia** okno dialogowe.

4.  W **nazwy serwera**, wpisz nazwę serwera, na którym uruchomiono `LoadTest` skryptów.

    > [!TIP]
    > Jeśli używasz programu SQL Express na komputerze lokalnym do magazynu testów obciążenia, wprowadź \<NazwaKomputera > \sqlexpress (na przykład **MyComputer\sqlexpress**).

5.  W obszarze **Zaloguj się do serwera**, można wybrać **uwierzytelnianie systemu Windows**. Można określić nazwę użytkownika i hasło, ale jeśli to zrobisz, należy wybrać opcję **Zapisz moje hasło**.

6.  W obszarze **połączenie z bazą danych**, wybierz **wybierz lub wprowadź nazwę bazy danych**. Wybierz **LoadTest** w polu listy rozwijanej.

7.  Wybierz **OK**. Można przetestować połączenie, wybierając **Testuj połączenie**.

8.  Wybierz **Zamknij** w **Zarządzanie aplikacją Test Controller** okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [Zarządzenie wynikami testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md)