---
title: 'Porady: synchronizowanie zestawu reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bb6f97495eec73e52751f79d92e2f078bd13b24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Porady: synchronizowanie zestawu reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego

Możesz zsynchronizować ustawienia analizy kodu dla projektów kodu z zasadami ewidencjonowania projektu zespołowego, określając zestaw reguł, który zawiera co najmniej reguły, które są określone w regule ustawienie zasad ewidencjonowania. Twoje realizacji developer można poinformować o nazwę i lokalizację zestawu reguł dla zasad ewidencjonowania. Jedną z następujących opcji umożliwia upewnij się, że analiza kodu dla projektu używa poprawny zestaw reguł:

-   Zasady ewidencjonowania korzysta z jednego z zestawów reguł wbudowanych firmy Microsoft, Otwórz okno dialogowe właściwości dla projektu kodu, wyświetlona strona analizy kodu i wybierz regułę, ustaw na stronie Ustawienia projektu kodu analizy kodu. Microsoft zestawów reguł standardowe są automatycznie instalowane z programem Visual Studio są ustawione na tylko do odczytu i nie można edytować. Jeśli nie edytowania zestawów reguł, reguł w zasadzie i zestawów reguł lokalnych gwarancję do dopasowania.

-   Jeśli zasady ewidencjonowania używa niestandardowego zestawu reguł, wykonaj operację pobierania w pliku zestawu reguł w kontroli wersji, aby utworzyć kopię lokalną. Następnie można określić lokalizacji lokalnej w ustawienia analizy kodu dla kodu projektu. Zasady dotrą do dopasowania, jeśli zestaw reguł dla zasad ewidencjonowania jest aktualny.

     Jeśli mapujesz lokalizację kontroli wersji na folder lokalny, który znajduje się w tej samej relacji do katalogu głównego projektu zespołowego w postaci kodu projektu lokalizacja reguły jest ustawiana za pomocą ścieżki względnej. Ścieżka względna gwarantuje, że ustawienie projektu kodu dla analizy kodu mogą być przenoszone do innych komputerów.

-   Dostosuj kopię zestawu reguł dla zasad ewidencjonowania dla projektu kodu. Upewnij się, że nowy zestaw reguł zawiera wszystkie reguły w ramach zasad ewidencjonowania i innymi regułami, które chcesz dołączyć. Należy się upewnić, że zestaw reguł zawiera wszystkie reguły w regule ustawienie zasad ewidencjonowania.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Aby określić regułę standard Microsoft Ustaw

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij przycisk **właściwości**.

2.  Kliknij przycisk **analiza kodu**.

3.  W **Uruchom ten zestaw reguł** kliknij zestaw reguł zasad ewidencjonowania.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Aby określić zestaw reguł niestandardowych zasad ewidencjonowania

1.  Jeśli to konieczne, należy wykonać operację pobrania w pliku zestawu reguł, który określa zasady ewidencjonowania.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij przycisk **właściwości**.

3.  Kliknij przycisk **analiza kodu**.

4.  W **Uruchom ten zestaw reguł** kliknij  **\<Przeglądaj >**.

5.  W **Otwórz** oknie dialogowym Określ plik zestawu reguł zasad ewidencjonowania.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Aby utworzyć regułę niestandardową ustawić projekt kodu

1.  Wykonaj jedną z procedur we wcześniejszej części tego tematu, aby wybrać zasadami ewidencjonowania projektu zespołowego na stronie analizy kodu w oknie dialogowym Ustawienia projektu.

2.  Kliknij przycisk **Otwórz**.

3.  Dodawanie lub usuwanie reguł za pomocą [edytorze zestawu reguł](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4.  Zapisz reguły zmodyfikowany plik .ruleset na komputerze lokalnym lub ścieżką UNC.

5.  Otwórz okno dialogowe właściwości dla kodu projektu i wyświetlić **analizy kodu** strony.

6.  W **Uruchom ten zestaw reguł** kliknij  **\<Przeglądaj >**.

7.  W **Otwórz** oknie dialogowym Określ pliku zestawu reguł.