---
title: Edytowanie modeli testów mieszanych w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 591bdaa84d143dc3b639990530a68246dc00385a
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425338"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Edytuj mieszanego modelu testu w celu określania prawdopodobieństwa uruchamiania testu przez użytkownika wirtualnego

*Model testu mieszanego* określa prawdopodobieństwo wirtualnego użytkownika wykonywanie testu danego scenariusza testu obciążenia. Umożliwia to bardziej realistycznie symulować obciążenia. Zamiast tylko jeden przepływ pracy za pośrednictwem aplikacji może mieć wielu przepływów pracy, czyli bliżej zbliżenia interakcje użytkowników końcowych z aplikacji.

## <a name="test-mix-model-options"></a>Opcje Model mieszanki testów

Można określić jedną z następujących opcji model testu mieszanego dla danego scenariusza testu obciążenia:

-   **Na podstawie całkowitej liczby testów:** Określa, który test wydajności lub jednostce sieci Web jest uruchamiany, gdy wirtualny użytkownik rozpoczyna iterację testu. Po zakończeniu testu obciążenia liczba uruchomień poszczególnego testu pasuje dystrybucji przypisanych testu. Ten model testu mieszanego należy użyć, jeśli test mieszany oparty jest w procentach transakcji w dzienniku usług IIS lub w danych produkcyjnych.

-   **Na podstawie liczby wirtualnych użytkowników:** Określa procent wirtualnych użytkowników, którzy uruchomią poszczególnego testu wydajności lub jednostce sieci Web. W dowolnym momencie w teście obciążenia liczba użytkowników korzystających z poszczególnego testu pasuje przypisanej dystrybucji. Ten model testu mieszanego należy użyć, gdy mieszanki testów oparty jest na procencie użytkowników z uruchomionymi poszczególnego testu.

-   **Oparty na tempie użytkownika:** w trakcie testu obciążenia każdego testu wydajności sieci Web lub testu jednostkowego jest uruchamiany określoną liczbę razy na użytkowników na godzinę. Ten model testu mieszanego należy używać wirtualnych użytkowników, aby uruchomić test na konkretnej stronie, wszędzie w teście obciążenia.

-   **Na podstawie numeru sekwencyjnego:** każdy wirtualny użytkownik uruchamia testy sieci Web wydajności lub jednostki w kolejności, że testy są zdefiniowane w scenariuszu. Wirtualny użytkownik kontynuuje, okrągło testów w następującej kolejności, aż do ukończenia testu obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Określanie testu mieszanego dla testu obciążenia:** podczas tworzenia testu obciążenia załadować Test Kreatora nowego Określ ustawienia dla testu obciążenia. W Kreatorze nowego testu obciążenia wybierz istniejącą witrynę sieci Web i testów jednostkowych, aby dodać do scenariusza początkowej. Po dodaniu testy do scenariusza, należy określić testu mieszanego dla tego scenariusza.<br /><br /> Załaduj opcje modelowania umożliwia bardziej dokładnie przewidzieć oczekiwane wykorzystanie rzeczywistych witryny sieci Web lub aplikacji, która obciążenia testowania. Należy to zrobić, ponieważ test obciążenia, który nie jest oparty na modelu dokładne obciążenia mogą generować błędne wyniki.|-   [Emulowanie oczekiwanego wykorzystania witryny sieci Web lub aplikacji](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Edytuj model testu mieszanego:** można zmienić scenariusza testu obciążenia, aby użyć jednej z mieszanego modelu testu za pomocą edytora testu obciążenia.||
|**Skonfiguruj tempo opóźnienie model użytkownika realizowanych testu mieszanego:** Jeśli danego scenariusza testu obciążenia jest skonfigurowany do używania **oparty na tempie model testu mieszanego użytkownika**, można określić sposób dystrybucji opóźnienie Pacing skonfigurowany.|-   [Porady: Zastosuj rozkład do opóźnienia kroku, korzystając z użytkownikiem tempie Model testu mieszanego](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Zmień Model testu mieszanego w scenariuszu

Po utworzeniu testu obciążenia za pomocą **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić właściwości scenariuszy, aby spełnić potrzeby testowania i cele.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

Za pomocą edytora testu obciążenia, można zmienić model testu mieszanego w scenariuszu testu obciążenia, edytując **typu testu mieszanego** właściwości w oknie właściwości.

### <a name="to-change-the-test-mix-model"></a>Aby zmienić model testu mieszanego

1.  Otwórz testu obciążenia.

     Zostanie wyświetlone edytora testu obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

2.  W **scenariusze** folderu drzewa testu obciążenia, wybierz węzeł scenariusz, dla którego chcesz określić maksymalną liczbę iteracji testowych.

3.  Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane.

4.  W **typ testu mieszanego** właściwości, kliknij przycisk wielokropka ( **...** ).

     Zostanie wyświetlone okno dialogowe Edytowanie testu mieszanego.

5.  Wybierz z listy rozwijanej w obszarze **model testu mieszanego** i wybierz model testu mieszanego, który ma być używany dla tego scenariusza.

6.  (Opcjonalnie) Modyfikowanie mieszanki testów przy użyciu **Dodaj**, **Usuń** i **dystrybucji** suwaki dystrybucji i przycisków. Aby uzyskać więcej informacji, zobacz [edytowanie mieszanki testów, aby określić, które testy będą załączone w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7.  (Opcjonalnie) Określ testu sieci Web wydajności i jednostki, aby zainicjować ani kończyć się przy użyciu pola wyboru i wybierając żądane testy. Aby uzyskać więcej informacji, zobacz [emulowanie oczekuje wykorzystania witryny sieci Web lub aplikacji](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8.  Wybierz **OK**.

     **Właściwości** okno wyświetla nowy model testu mieszanego dla **typu testu mieszanego** właściwości.

9. Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowej **typu testu mieszanego** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)