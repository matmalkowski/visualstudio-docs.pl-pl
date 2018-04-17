---
title: 'Szybki Start: Analiza kodu dla C/C++ | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: efba8b220bc078436921c437f0cb382870b3277b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-code-analysis-for-cc"></a>Szybki Start: Analiza kodu dla C/C++

Aby poprawy jakości aplikacji, należy regularnie uruchamiania analizy kodu dla kodu C lub C++. To może pomóc w znalezieniu typowych problemów, naruszeń dobrym rozwiązaniem programowania lub usterek, które są trudne do odnajdywania testy. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ przeszukuje analizy kodu dla kodu określonych wzorców, które są prawidłowe, ale nadal można utworzyć problemy lub innym osobom korzystającym z kodu.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurowanie zestawów reguł dla projektu

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla nazwy projektu, a następnie wybierz pozycję **właściwości**.

2. Poniższe kroki są opcjonalne:

    1. W **konfiguracji** i **platformy** listy, wybierz platformę kompilacji konfiguracji i obiekt docelowy.

    2. Domyślnie analizy kodu nie raportuje ostrzeżenia z kodu, który jest automatycznie generowany przez zewnętrznych narzędzi. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.

        > [!NOTE]
        > Ta opcja nie odrzuca błędy analizy kodu i ostrzeżeń z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Jednocześnie można wyświetlać i obsługa kodu źródłowego dla formularza lub szablonu.

3. Aby uruchomić kod — analiza za każdym razem, gdy projekt jest utworzony przy użyciu wybranej konfiguracji, wybierz **Włącz analizę kodu dla C/C++ podczas kompilacji** pole wyboru. Można również uruchomić kod — analiza ręcznie, otwierając **Analizuj** menu, a następnie wybierając **Uruchom analizę kodu na** *ProjectName*.

4. W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:

    - Wybierz zestaw reguł, który ma być używany.

    - Wybierz  **\<Przeglądaj >** określ zestaw istniejącej reguły niestandardowe, których nie ma na liście.

    - Zdefiniuj [niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Zestawy reguł standardu C/C++

Visual Studio zawiera dwa standardowe zestawy reguł dla natywnego kodu:

|Zestaw reguł|Opis|
|--------------|-----------------|
|Zalecane reguły kodu natywnego firmy Microsoft Minimum|Ten zestaw reguł koncentruje się na najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|
|Zalecane reguły kodu natywnego firmy Microsoft|Ten zestaw reguł obejmuje szerokiej gamy problemów. Zawiera wszystkie reguły Microsoft Native Minimum reguł zalecanych.|

## <a name="run-code-analysis"></a>Przeprowadzanie analizy kodu

Na stronie analizy kodu na stronach właściwości projektu można skonfigurować analizy kodu do każdego czas wykonywania kompilacji projektu. Kod — analiza można również uruchomić ręcznie.

Aby uruchamiać analizę kodu dla rozwiązania:

- Na **kompilacji** menu, wybierz **uruchamiania analizy kodu dla rozwiązania**.

 Aby uruchamiać analizy kodu w projekcie:

- W Eksploratorze rozwiązań wybierz nazwę projektu.

- Na **kompilacji** menu, wybierz **Uruchom analizę kodu na** *Nazwa projektu*.

 Jest skompilowany projekt lub rozwiązanie i uruchamia analizy kodu. Wyniki są wyświetlane na liście błędów.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizowanie i rozwiązywanie ostrzeżenia analizy kodu

Do analizowania określone ostrzeżenia, wybierz tytuł ostrzeżenia na liście błędów. Ostrzeżenie rozszerza się, aby wyświetlić dodatkowe informacje o problemie. Jeśli to możliwe, analizy kodu wyświetla numery wierszy i logiki analizy, które doprowadziło do tego ostrzeżenia. Aby uzyskać szczegółowe informacje na temat tego ostrzeżenia, w tym możliwe rozwiązania problemu należy wybrać identyfikator ostrzeżenia, aby wyświetlić jego odpowiedni temat Pomocy online.

Po wybraniu ostrzeżenie wiersza kodu, która spowodowała ostrzeżenie zostanie wyróżniona w edytorze kodu programu Visual Studio.

Po zidentyfikowaniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, czy ostrzeżenia nie jest już widoczna na liście błędów i nie ma Twojego poprawka nie zgłaszany ostrzeżenia nowego.

## <a name="suppress-code-analysis-warnings"></a>Pomijanie ostrzeżeń analizy kodu

Brak razy podczas może zdecydować, czy nie, aby naprawić ostrzeżenia analizy kodu. Możesz określić rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo, że ten problem może wystąpić w implementacji rzeczywistych kodu. Lub może uważasz, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Ostrzeżeń indywidualnych można pominąć, tak aby nie były widoczne na liście błędów.

Aby wyłączyć ostrzeżenia:

1. Jeśli nie są wyświetlane szczegółowe informacje, wybierz tytuł ostrzeżenia, aby go rozwinąć.

2. Wybierz **akcje** łącze umieszczone u dołu ostrzeżenia.

3. Wybierz **Pomiń komunikat** , a następnie wybierz **źródła w**.

 Wstawia komunikat z pominięciem `#pragma warning (disable:` *WarningId* `)` który powoduje pominięcie ostrzeżenia dla wiersza kodu.

## <a name="create-work-items-for-code-analysis-warnings"></a>Tworzenie elementów roboczych dla kod analizy ostrzeżenia

Funkcja śledzenia elementu roboczego służy do dziennika błędów z poziomu programu Visual Studio. Aby użyć tej funkcji, należy połączyć do wystąpienia programu Team Foundation Server.

**Aby utworzyć element roboczy dla co najmniej jedno ostrzeżenie kodu C/C++**

1. Na liście błędów Rozwiń i wybierz ostrzeżenia

2. Menu skrótów dla ostrzeżenia, należy wybrać **Utwórz element roboczy**, a następnie wybierz typ elementu roboczego.

3. Program Visual Studio pojedynczym elemencie roboczym wybranego ostrzeżenia i wyświetla element roboczy w oknie dokumentu IDE.

4. Dodaj wszelkie dodatkowe informacje, a następnie wybierz pozycję **zapisać element roboczy**.

## <a name="search-and-filter-code-analysis-results"></a>Wyszukiwanie i filtrowanie wyników analizy kodu

Możesz przeszukać długich list komunikaty ostrzegawcze i można filtrować ostrzeżeń w rozwiązań dotyczących wielu projektów.

- **Aby ostrzeżeń filtru tytuł lub identyfikator ostrzeżenia**: Wprowadź słowo kluczowe w polu wyszukiwania.

- **Aby ostrzeżeń filtru według ważności**: Domyślnie komunikaty analizy kodu są przypisane ważność **ostrzeżenie**. Można przypisać ważność jeden lub więcej komunikatów jako **błąd** w zestawie reguł niestandardowych. Na **ważność** kolumny **listy błędów**, wybierz strzałkę listy rozwijanej, a następnie ikonę filtru. Wybierz **ostrzeżenie** lub **błąd** do wyświetlenia tylko komunikaty, które są przypisane im wagi. Wybierz **Zaznacz wszystko** Aby wyświetlić wszystkie komunikaty.

## <a name="see-also"></a>Zobacz także

[Analiza kodu dla C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)