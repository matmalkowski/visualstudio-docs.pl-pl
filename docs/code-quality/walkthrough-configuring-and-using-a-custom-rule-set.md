---
title: 'Wskazówki: Konfigurowanie i używanie niestandardowego zestawu reguł | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b72a86f10c6e864406929fdccfb59bdd9393752e
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Wskazówki: konfigurowanie niestandardowego zestawu reguł i korzystanie z niego

W tym przewodniku pokazano, jak używać narzędzi analizy kodu, które zostały skonfigurowane do używania niestandardowych *zestaw reguł* w bibliotece klas. Możesz wybrać zestaw reguł, które odnoszą się do typ projektu, do którego określony dla rozwiązania lub wybrać alternatywny reguły zestawów do konkretna potrzeba, takie jak skanowanie starszego kodu dla problemów, które można naprawić w sposób nierozdzielający zrealizowania. W obu przypadkach można również dostosować dostrajania wymogami projektu zestawów reguł.  
  
W tym przewodniku będzie krok za pomocą tych procesów:  
  
-   Utwórz bibliotekę klas.  
  
-   Wybierz **podstawowe reguły wskazówek dotyczących projektowania Microsoft** zestawu reguł analizy kodu.  
  
-   Dodaj swój kod do klasy.  
  
-   Uruchom analizę kodu.  
  
-   Dostosowywanie zestawu reguł.  
  
-   Uruchom analizę kodu i zobacz, jak działa zachowanie dostosowywania zestawu reguł.  
  
## <a name="using-rule-sets-with-code-analysis"></a>Korzystanie z zestawów reguł analizy kodu

Najpierw utwórz prostą klasę.  
  
### <a name="create-a-class-library"></a>Tworzenie biblioteki klas  
  
1.  Na **pliku** menu, kliknij przycisk **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **typów projektów**, kliknij przycisk **Visual C#**.  
  
3.  W obszarze **Visual C#**, wybierz pozycję **biblioteki klas**.  
  
4.  W **nazwa** polu tekstowym **RuleSetSample** , a następnie kliknij przycisk **OK**.  
  
 Następnie należy wybrać **podstawowe reguły wskazówek dotyczących projektowania Microsoft** zestaw reguł i zapisać go z projektu.  
  
### <a name="select-a-code-analysis-rule-set"></a>Wybierz zestaw reguł analizy kodu  
  
1.  Na **Analizuj** menu, kliknij przycisk **Konfigurowanie analizy kodu dla RuleSetSample**.  
  
     Ustawienia konfiguracji dla analizy kodu będą wyświetlane.  
  
2.  W **Uruchom ten zestaw reguł** listy rozwijanej wybierz **Microsoft wszystkie reguły**.  
  
     Aby uzyskać więcej informacji na temat zestawów reguł dostępne, zobacz [odwołanie zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md).  
  
     W menu Plik kliknij polecenie **zapisać wybrane elementy** można zaktualizować pliku projektu o informacji na temat zestawu reguł, które wybrano i jego ustawień.  
  
    > [!TIP]
    >  W przypadku rzeczywistych dobrym rozwiązaniem dla priorytetyzowanie problemy, które mają być docelowe dla analizy kodu jest zacząć **reguł zalecanych Minimum** zestaw reguł i rozwiązanie problemów, żądane i stopniowego dodawania więcej reguł lub reguła ustawia Aby odnaleźć i rozwiązać dodatkowe problemy.  
  
 Następnie dodasz kod do biblioteki klasy, która będzie używana do pokazu naruszenia CA1704 "Identyfikatory powinny być napisane poprawnie" reguł analizy kodu. Aby uzyskać więcej informacji, zobacz [CA1704: identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
### <a name="add-your-own-code"></a>Dodaj swój kod  
  
-   W Eksploratorze rozwiązań Otwórz plik Class1.cs i zastąpić istniejący kod z następujących czynności:  
  
    ```csharp
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }
    ```
  
Teraz można uruchamiać analizę kodu w projekcie RuleSetSample i wyszukaj wszelkie błędy i ostrzeżenia wygenerowane w oknie Lista błędów.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Przeprowadź analizę kodu na projekt RuleSetSample  
  
1.  Na **Analizuj** menu, kliknij przycisk **Uruchom analizę kodu na RuleSetSample**.  
  
2.  Kliknij w oknie Lista błędów **ostrzeżenia** , a następnie kliknij przycisk **opis** nagłówek kolumny, aby posortować ostrzeżenia alfanumerycznie.  
  
     W przypadku aplikacji rzeczywistych czy Usuń wszelkie naruszenia reguły warto w tym momencie ustalania, lub opcjonalnie wyłączyć lub pominąć reguły, jeśli można stwierdzić, że nie warto ustalania. Aby uzyskać więcej informacji, zobacz [tłumienie ostrzeżeń](../code-quality/in-source-suppression-overview.md).
  
3.  Zwróć uwagę, CA1704 ostrzeżenia. Te naruszeń w tej regule wskazują, że "rozważ podanie bardziej zrozumiałej nazwy parametrów." W kodzie można rozwiązać ten problem, albo można wyłączyć reguły, zgodnie z objaśnieniem w następnej procedurze.  
  
 Następnie będzie można dostosować zestaw reguł, do wykluczenia ostrzeżenie CA1704, "Identyfikatory powinny być napisane poprawnie".  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Dostosowywanie zestawu dla projektu można wyłączyć reguły określonych reguł  
  
1.  Na **Analizuj** menu, kliknij przycisk **Konfigurowanie analizy kodu dla RuleSetSample**.  
  
2.  W **Uruchom ten zestaw reguł** listy rozwijanej liście, upewnij się, że **Microsoft wszystkie reguły** reguły zestawu nadal jest podświetlona, a następnie kliknij przycisk **Otwórz**. Zostanie wyświetlona strona zestawu reguł.  
  
3.  Rozwiń węzeł kategorii Microsoft.Naming, a następnie wybierz ostrzeżenie CA1704.  
  
4.  W obszarze **akcji** kolumny wybierz **None.** CA1704 zapobiega wyświetlaniu jako ostrzeżenia lub błędu w oknie Lista błędów.  
  
     Teraz jest odpowiedni moment, aby wypróbować różne przycisków paska narzędzi i opcji, aby zapoznać się z nimi filtrowania. Na przykład można użyć **Group By** listy rozwijanej, aby pomóc w lokalizacji określonej reguły lub kategoria reguł. Innym przykładem jest, że można używać **Ukryj wyłączone reguły** przycisk na pasku narzędzi strony zestawu reguł do ukrywania lub pokazywania wszystkie reguły z **akcji** kolumny ustawioną **Brak**. Może to być przydatne, jeśli chcesz skanować dla wszystkich reguł, które można wyłączona, aby sprawdzić, czy nadal chcesz je wyłączyć.  
  
5.  W menu Widok kliknij przycisk okna właściwości. Typ **Moje zestawu reguł niestandardowych** w polu nazwy okna narzędzia właściwości. Spowoduje to zmianę nazwę wyświetlaną dla nowego zestawu reguł w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE.  
  
6.  Na **pliku** menu, kliknij przycisk **Zapisz wszystkie Rules.ruleset Microsoft** Aby zapisać dostosowane reguły zestaw. Przejdź do folderu głównego projektu. W **nazwę pliku** polu tekstowym **MyCustomRuleSet**. Teraz można wybrać zestaw reguł niestandardowych do użytku z projektu.  
  
Nowy zestaw reguł utworzony należy teraz skonfigurować ustawienia projektu, aby określić, czy chcesz użyć nowej reguły ustawić z nim.  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Określ nową regułę, ustaw do użycia z projektu  
  
1.  W Eksploratorze rozwiązań kliknij projekt prawym przyciskiem myszy, a następnie wybierz **właściwości**.  
  
2.  W **właściwości** , kliknij pozycję **analizy kodu**.  
  
     W **Uruchom ten zestaw reguł** listy rozwijanej, kliknij przycisk  **\<Przeglądaj... >**. Przejdź do folderu głównego projektu kodu, a następnie wybierz **MyCustomRuleSet.ruleset**. Jest to nowy zestaw reguł utworzony w poprzedniej procedurze.  
  
3.  Na **pliku** menu, kliknij przycisk **zapisać** można zapisać konfiguracji projektu. Można teraz używać niestandardowego zestawu reguł projektu.  
  
 Na koniec zostanie uruchomiony ponownie przy użyciu MyCustomRuleSet zestawu reguł analizy kodu. Zwróć uwagę, w oknie Lista błędów nie wyświetla naruszenia CA1704 reguły wydajności.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Przeprowadź analizę kodu na projekt RuleSetSample po raz drugi  
  
1.  Na **Analizuj** menu, kliknij przycisk **Uruchom analizę kodu na RuleSetSample**.  
  
2.  W oknie Lista błędów, zwróć uwagę, że po kliknięciu **ostrzeżenia**, nie są już wyświetlane naruszenia CA1704 ostrzeżenie reguły "Identyfikatory powinny być napisane poprawnie".  
  
## <a name="see-also"></a>Zobacz także

[Porady: Konfigurowanie analizy kodu dla projektu zarządzanego kodu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[Informacje o zestawie reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md)