---
title: 'Szybki Start: Analiza kodu dla C/C++ | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33080a55043f9c88fa8e44a71a863e3a62ab3a1b
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="quick-start-code-analysis-for-cc"></a>Szybki start: Analiza kodu dla C/C++
Aby poprawy jakości aplikacji, należy regularnie uruchamiania analizy kodu dla kodu C lub C++. To może pomóc w znalezieniu typowych problemów, naruszeń dobrym rozwiązaniem programowania lub usterek, które są trudne do odnajdywania testy. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ przeszukuje analizy kodu dla kodu określonych wzorców, które są prawidłowe, ale nadal można utworzyć problemy lub innym osobom korzystającym z kodu.  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Konfigurowanie zestawów reguł dla projektu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Przeprowadzanie analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analizowanie i rozwiązywanie ostrzeżenia analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Pomijanie ostrzeżeń analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Tworzenie elementów pracy dla kod analizy ostrzeżenia](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Wyszukiwanie i filtrowanie wyników analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a>Konfigurowanie zestawów reguł dla projektu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla nazwy projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  Poniższe kroki są opcjonalne:  
  
    1.  W **konfiguracji** i **platformy** listy, wybierz platformę kompilacji konfiguracji i obiekt docelowy.  
  
    2.  Domyślnie analizy kodu nie raportuje ostrzeżenia z kodu, który jest automatycznie generowany przez zewnętrznych narzędzi. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.  
  
        > [!NOTE]
        >  Ta opcja nie odrzuca błędy analizy kodu i ostrzeżeń z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Jednocześnie można wyświetlać i obsługa kodu źródłowego dla formularza lub szablonu.  
  
3.  Aby uruchomić kod — analiza za każdym razem, gdy projekt jest utworzony przy użyciu wybranej konfiguracji, wybierz **Włącz analizę kodu dla C/C++ podczas kompilacji** pole wyboru. Można również uruchomić kod — analiza ręcznie, otwierając **Analizuj** menu, a następnie wybierając **Uruchom analizę kodu na** *ProjectName*.  
  
4.  W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:  
  
    -   Wybierz zestaw reguł, który ma być używany.  
  
    -   Wybierz  **\<Przeglądaj >** określ zestaw istniejącej reguły niestandardowe, których nie ma na liście.  
  
    -   Definiowanie niestandardowego zestawu reguł.  
  
         Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Zestawy reguł standardu C/C++  
 Visual Studio zawiera dwa standardowe zestawy reguł dla natywnego kodu:  
  
|Zestaw reguł|Opis|  
|--------------|-----------------|  
|Zalecane reguły kodu natywnego firmy Microsoft Minimum|Ten zestaw reguł koncentruje się na najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|  
|Zalecane reguły kodu natywnego firmy Microsoft|Ten zestaw reguł obejmuje szerokiej gamy problemów. Zawiera wszystkie reguły Microsoft Native Minimum reguł zalecanych.|  
  
##  <a name="BKMK_Run"></a>Przeprowadzanie analizy kodu  
 Na stronie analizy kodu na stronach właściwości projektu można skonfigurować analizy kodu do każdego czas wykonywania kompilacji projektu. Kod — analiza można również uruchomić ręcznie.  
  
 Aby uruchamiać analizę kodu dla rozwiązania:  
  
-   Na **kompilacji** menu, wybierz **uruchamiania analizy kodu dla rozwiązania**.  
  
 Aby uruchamiać analizy kodu w projekcie:  
  
-   W Eksploratorze rozwiązań wybierz nazwę projektu.  
  
-   Na **kompilacji** menu, wybierz **Uruchom analizę kodu na** *Nazwa projektu*.  
  
 Jest skompilowany projekt lub rozwiązanie i uruchamia analizy kodu. Wyniki są wyświetlane w oknie analizy kodu.  
  
##  <a name="BKMK_Analyze"></a>Analizowanie i rozwiązywanie ostrzeżenia analizy kodu  
 Do analizowania określone ostrzeżenia, wybierz tytuł ostrzeżenia w oknie analizy kodu. Ostrzeżenie rozszerza się, aby wyświetlić dodatkowe informacje o problemie. Jeśli to możliwe, analizy kodu wyświetla numery wierszy i logiki analizy, które doprowadziło do tego ostrzeżenia. Aby uzyskać szczegółowe informacje na temat tego ostrzeżenia, w tym możliwe rozwiązania problemu należy wybrać identyfikator ostrzeżenia, aby wyświetlić tematu pomocy w bibliotece MSND dla wiadomości.  
  
 Po rozwinięciu ostrzeżenie wiersza kodu, która spowodowała ostrzeżenie zostanie wyróżniona w edytorze kodu programu Visual Studio.  
  
 Po zidentyfikowaniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenia nie jest już widoczna w oknie analizy kodu i nie ma Twojego poprawka nie zgłaszany nowego ostrzeżenia.  
  
> [!TIP]
>  Można ponownie uruchomić analizy kodu w oknie analizy kodu. Wybierz **Analizuj** przycisk i wybierz zakres analizy. Można ponownie uruchomić analizy całego rozwiązania lub wybranego projektu.  
  
##  <a name="BKMK_Suppress"></a>Pomijanie ostrzeżeń analizy kodu  
 Brak razy podczas może zdecydować, czy nie, aby naprawić ostrzeżenia analizy kodu. Możesz określić rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo, że ten problem może wystąpić w implementacji rzeczywistych kodu. Lub może uważasz, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Ostrzeżeń indywidualnych można pominąć, tak aby nie były widoczne w oknie analizy kodu.  
  
 Aby wyłączyć ostrzeżenia:  
  
1.  Jeśli nie są wyświetlane szczegółowe informacje, wybierz tytuł ostrzeżenia, aby go rozwinąć.  
  
2.  Wybierz **akcje** łącze umieszczone u dołu ostrzeżenia.  
  
3.  Wybierz **Pomiń komunikat** , a następnie wybierz **źródła w**.  
  
 Wstawia komunikat z pominięciem `#pragma warning (disable:` *WarningId* `)` który powoduje pominięcie ostrzeżenia dla wiersza kodu.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a>Tworzenie elementów pracy dla kod analizy ostrzeżenia  
 Funkcja śledzenia elementu roboczego służy do dziennika błędów z poziomu programu Visual Studio. Aby użyć tej funkcji, należy połączyć do wystąpienia programu Team Foundation Server.  
  
 **Aby utworzyć element roboczy dla co najmniej jedno ostrzeżenie kodu C/C++**  
  
1.  W oknie analizy kodu Rozwiń i wybierz ostrzeżenia  
  
2.  Menu skrótów dla ostrzeżenia, należy wybrać **Utwórz element roboczy**, a następnie wybierz typ elementu roboczego.  
  
3.  Program Visual Studio pojedynczym elemencie roboczym wybranego ostrzeżenia i wyświetla element roboczy w oknie dokumentu IDE.  
  
4.  Dodaj wszelkie dodatkowe informacje, a następnie wybierz pozycję **zapisać element roboczy**.  
  
##  <a name="BKMK_Search"></a>Wyszukiwanie i filtrowanie wyników analizy kodu  
 Możesz przeszukać długich list komunikaty ostrzegawcze i można filtrować ostrzeżeń w rozwiązań dotyczących wielu projektów.  
  
1.  **Aby ostrzeżeń filtru tytuł lub identyfikator ostrzeżenia**: Wprowadź słowa kluczowe w **filtru** pola tekstowego.  
  
2.  **Aby ostrzeżeń filtru przez projekt**: W rozwiązaniu do wielu projektów, wybierz jeden lub więcej projektów na liście u góry rogu okna analizy kodu. Wybierz nazwę rozwiązania, aby wyświetlić wszystkie ostrzeżenia.  
  
3.  **Aby ostrzeżeń filtru według ważności**: Domyślnie komunikaty analizy kodu są przypisane ważność **ostrzeżenie**. Można przypisać ważność jeden lub więcej komunikatów jako **błąd** w zestawie reguł niestandardowych. Wybierz **ostrzeżenie** lub **błąd** do wyświetlenia tylko komunikaty, które są przypisane im wagi. Wybierz **wszystkie** Aby wyświetlić wszystkie komunikaty.