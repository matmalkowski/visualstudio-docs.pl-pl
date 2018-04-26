---
title: Edytowanie scenariuszy testu obciążenia w programie Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: efc9c9af36e5484728b05db1171bb2e9bc30ba0b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="edit-load-test-scenarios"></a>Edytowanie scenariuszy testu obciążenia

Test obciążenia *scenariusza* określa wzorca obciążenia, mieszanki testów, rozkład przeglądarek i mieszany profil sieciowy. Scenariusze są ważne, ponieważ umożliwiają one Konfigurowanie testów do symulowania złożonych, realistyczne obciążeń.

Na przykład użytkownik może testowania witryną handlu elektronicznego z Internetu frontonu używane przez setki klientów równoczesnych przychodzących przez wiele prędkości połączenia i przy użyciu różnych przeglądarkach. Tej samej lokacji może być również funkcji administracji, która jest używana przez pracowników firmy, aby zaktualizować produktów i wyświetlić statystyki. Tych użytkowników wewnętrznych zazwyczaj będzie dostęp do witryny przy użyciu tej samej przeglądarce i szybkie połączenie sieci LAN. Czy chcesz Hermetyzowanie właściwości tych dwóch różnych grup użytkowników w różnych scenariuszach. Każdy scenariusz może zawierać typu wirtualnego użytkownika. W takim przypadku scenariusza testu obciążenia jest możliwe do reprezentowania wirtualnych klientów i innym scenariuszu można wprowadzić do reprezentowania wirtualnych użytkowników wewnętrznej witryny sieci Web.

## <a name="scenario-components"></a>Składniki scenariusza

Wszystkie opcje konfiguracji początkowej i ustawienia, które można określić podczas tworzenia testu obciążenia, można modyfikować później w edytorze testu obciążenia. Można również dodać nowych scenariuszy, ustawień i zbiory liczników do testu obciążenia.

![Scenariuszy testu obciążenia](../test/media/loadtesteditinscenarios.png)

Scenariusze zawierają następujące składniki:

|||
|-|-|
|Termin|Definicja|
|Rozkład przeglądarek|Symuluje, że wirtualne użytkownicy uzyskują dostęp do witryny sieci Web za pomocą różnych przeglądarek sieci Web.|
|Wzorzec obciążenia|Określa liczbę wirtualnych użytkowników, które są aktywne podczas testu obciążenia i szybkość uruchamiania nowych użytkowników. Na przykład: krok, stałe i opartego na celach.|
|Model mieszanki testów|Określa prawdopodobieństwo wirtualnego użytkownika wykonywanie testu danego scenariusza testu obciążenia. Na przykład: 20% możliwość uruchamiania TestA i możliwość uruchamiania TestB 80%. Model testu mieszanego powinien odzwierciedlać celów testu dla danego scenariusza.|
|Mieszanka testów|Test mieszany jest wybór testy wydajności i jednostki sieci Web wchodzących w skład tego scenariusza i dystrybucji tych testów.|
|Mieszany profil sieciowy|Symuluje, że wirtualne użytkownicy uzyskują dostęp do witryny sieci Web za pomocą różnych połączeń sieciowych. Mieszany profil sieciowy udostępnia opcje, które obejmują sieci LAN, modemu kablowego i inne opcje.|

Scenariusz ma kilka właściwości, które można edytować za pomocą edytora testu obciążenia. Aby uzyskać więcej informacji, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Dodaj sztuczne człowieka pauzy w danym scenariuszu:** wziąć pod uwagę czas jest używany do symulowania człowieka zachowanie, które powoduje, że osoby między interakcji z witryną sieci Web. Czasów reakcji wystąpić żądań w teście wydajności sieci Web oraz między iteracji testowych w scenariuszu testu obciążenia. Może być przydatne podczas tworzenia bardziej dokładne symulacje obciążenia przy użyciu czasów reakcji w teście obciążenia.|-   [Edytowanie czasów reakcji w celu symulowania opóźnienia człowieka witryny sieci Web](../test/edit-think-times-in-load-test-scenarios.md)|
|**Określ liczbę wirtualnych użytkowników dla danego scenariusza:** można skonfigurować właściwości wzorca obciążenia, aby określić, jak obciążenia symulowanego użytkownika jest uwzględniany podczas testu obciążenia. Pobierz trzech wzorców obciążenia wbudowanych: stała, kroku i opartego na celach. Wybierz wzorzec obciążenia oraz dostosować właściwości do odpowiednich poziomów cele testu obciążenia.|-   [Edytowanie wzorców obciążenia w celu modelowania aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Skonfiguruj prawdopodobieństwo użytkownikiem wirtualnego Uruchamianie testu w scenariuszu:** można użyć mieszanki testów, który określa prawdopodobieństwo wirtualnego użytkownika wykonywanie testu danego scenariusza testu obciążenia. Umożliwia to bardziej realistycznie symulować obciążenia. Zamiast tylko jeden przepływ pracy za pośrednictwem aplikacji może mieć wielu przepływów pracy, czyli bliżej zbliżenia interakcje użytkowników końcowych z aplikacji.|-   [Edytowanie modeli testów mieszanych](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Dodawanie lub usuwanie testu sieci Web wydajności lub jednostka scenariusza testu obciążenia:** można dodawać i usuwać wydajności lub jednostka testu sieci Web w scenariuszu testu obciążenia. Test obciążenia zawiera jeden lub więcej scenariuszy, z których każdy zawiera jeden lub więcej testów sieci Web wydajności lub jednostki.|-   [Edytowanie mieszanki testów](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Skonfiguruj mieszany profil sieciowy odpowiednie dla danego scenariusza:** przy użyciu mieszany profil sieciowy, można symulować obciążenia sieciowego bardziej realistycznie w scenariuszu testu obciążenia. Obciążenia jest generowany przy użyciu heterogenicznych mieszane typy sieci zamiast jednego typu jednej sieci. Możesz utworzyć bliżej zbliżenia interakcje użytkowników końcowych z aplikacji. Model mieszanki sieci powinien odzwierciedlać cele tego scenariusza.|-   [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Wybierz odpowiednie rozkład przeglądarek sieci Web dla danego scenariusza:** przy użyciu rozkład przeglądarek, można symulować obciążenia sieci Web bardziej realistycznie w scenariuszu testu obciążenia. Obciążenia jest generowany przy użyciu heterogenicznych różnych przeglądarkach zamiast jednej pojedynczego przeglądarki. Możesz utworzyć bliżej zbliżenia przeglądarek, które będą używane z aplikacjami.|-   [Określanie typów przeglądarek sieci Web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Skonfiguruj ustawienia iteracji testu dla danego scenariusza:** scenariusza testu obciążenia, aby skonfigurować ustawienia iteracji testu za pomocą edytora testu obciążenia i w oknie właściwości można edytować. Domyślnie scenariusza skonfigurowano nie maksymalnej liczby iteracji testu. Opcjonalnie można skonfigurować maksymalna liczba iteracji w scenariuszu i jak długo, aby wstrzymać między nimi.|-   [Konfigurowanie iteracji testowych dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Skonfiguruj ustawienia opóźnienie dla danego scenariusza:** za pomocą edytora testu obciążenia i w oknie właściwości, można określić opóźnienie przed uruchomieniem scenariusza w teście obciążenia. Przykład kiedy warto użyć **czas rozpoczęcia opóźnienie** właściwość jest konieczne będzie jeden scenariusz, aby rozpocząć tworzenie elementów, które wykorzystuje inny scenariusz. Można opóźnić odbierającą scenariusza, aby włączyć tworzenie scenariusza, aby wypełnić niektóre dane.|-   [Konfigurowanie opóźnień uruchamiania scenariuszy](../test/configure-scenario-start-delays.md)|
|**Określ komputerach zdalnych do użycia w scenariuszu testu obciążenia:** po utworzeniu testu obciążenia można edytować właściwości Twojego scenariusza testów obciążenia wskazująca agentów testowych, które chcesz dołączyć. Aby uzyskać więcej informacji, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).|-   [Porady: Określanie agentów testowych](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Zobacz także

- [Edytowania testów obciążenia](../test/edit-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)