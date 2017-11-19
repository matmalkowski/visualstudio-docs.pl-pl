---
title: "Wskazówki: Debugowanie aplikacji równoległych | Dokumentacja firmy Microsoft"
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a532c2e238528ea32492aae22b001ab0955f8c6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio"></a>Wskazówki: Debugowanie aplikacji równoległych w programie Visual Studio
Ten przewodnik przedstawia sposób użycia **zadań równoległych** i **stosów równoległych** systemu windows do debugowania aplikacji równoległych. Te okna ułatwić zrozumienie i sprawdź zachowania w czasie wykonywania kod, który używa [zadań biblioteki równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) lub [współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime). Ten przewodnik zawiera przykładowy kod, który ma wbudowane punktów przerwania. Po dzieli kodu, wskazówki przedstawia sposób użycia **zadań równoległych** i **stosów równoległych** systemu windows do zbadania go.  
  
 Ten przewodnik zawiera następujące zadania:  
  
-   Jak wyświetlić stosy wywołań wszystkich wątków w jednym widoku.  
  
-   Jak wyświetlić listę `System.Threading.Tasks.Task` wystąpień, które są tworzone w aplikacji.  
  
-   Jak wyświetlić stosy wywołań rzeczywistych zadań zamiast wątków.  
  
-   Jak można nawigować do kodu z **zadań równoległych** i **stosów równoległych** systemu windows.  
  
-   Jak windows radzenia sobie z skalowania za pomocą grupowania, powiększanie i inne powiązane funkcje.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku założono, że **tylko mój kod** jest włączona (ona jest domyślnie włączona w nowszych wersjach programu Visual Studio). Na **narzędzia** menu, kliknij przycisk **opcje**, rozwiń węzeł **debugowanie** węzła, wybierz opcję **ogólne**, a następnie wybierz **włączyć Tylko mój kod (tylko zarządzane)**. Jeśli ta funkcja nie jest ustawiona, można nadal używać tego przewodnika, ale wyniki mogą się różnić od przedstawionych na ilustracjach.  
  
## <a name="c-sample"></a>Przykład C#  
 Użycie próbki C#, w tym przewodniku założono również, że kod zewnętrzny jest ukryty. Do przełączania, czy kod zewnętrzny jest wyświetlany, kliknij prawym przyciskiem myszy **nazwa** nagłówek tabeli **stos wywołań** okna, a następnie zaznacz lub usuń zaznaczenie **Pokaż kod zewnętrzny**. Jeśli ta funkcja nie jest ustawiona, można nadal używać tego przewodnika, ale wyniki mogą się różnić od przedstawionych na ilustracjach.  
  
## <a name="c-sample"></a>Przykład w języku C++  
 Jeśli używasz próbka C++, możesz zignorować odwołania do zewnętrznego kodu w tym temacie. Kod zewnętrzny dotyczy tylko przykładowe C#.  
  
## <a name="illustrations"></a>Ilustracje  
 Na ilustracjach w tym temacie rejestrowane na komputerze czterordzeniowe próbki C#. Mimo że inne konfiguracje, można użyć w tym przewodniku, ilustracje mogą się różnić od wyświetlanych na komputerze.  
  
## <a name="creating-the-sample-project"></a>Tworzenie projektu próbki  
 Przykładowy kod w tym przewodniku jest dla aplikacji, która nie działa. Celem jest tak, aby zrozumieć sposób debugowanie aplikacji równoległych przy użyciu narzędzia systemu windows.  
  
#### <a name="to-create-the-sample-project"></a>Aby utworzyć przykładowy projekt  
  
1.  W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **zainstalowane szablony** okienku, wybierz opcję Visual C#, Visual Basic lub Visual C++. W przypadku języków zarządzanego upewnij się, że [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jest wyświetlana w polu framework.  
  
3.  Wybierz **aplikacji konsoli** , a następnie kliknij przycisk **OK**. Pozostają w konfiguracji debugowania, która jest ustawiona domyślnie.  
  
4.  Otwórz plik kodu .cpp, .cs lub .vb w projekcie. Usuń jego zawartość w celu utworzenia pliku kodu puste.  
  
5.  Wklej następujący kod do wybrany język do pliku kodu puste.  
  
 [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
 [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
 [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]  
  
1.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
2.  Na **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**.  
  
     Zwróć uwagę, że istnieją cztery wywołania `Debugger.Break` (`DebugBreak` w przykładowym C++) w związku z tym nie trzeba wstawić punktów przerwania; tylko działania aplikacji spowoduje jego przerwanie w debugerze maksymalnie cztery razy.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Przy użyciu równoległe stosów okna: widoku wątków  
 Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**. Poczekaj na pierwszy punkt przerwania do trafiony.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Aby wyświetlić stos wywołań jest jeden wątek  
  
1.  Na **debugowania** menu wskaż **Windows** , a następnie kliknij przycisk **wątków**. Dock **wątków** okna w dolnej części programu Visual Studio.  
  
2.  Na **debugowania** menu wskaż **Windows** , a następnie kliknij przycisk **stos wywołań**. Dock **stos wywołań** okna w dolnej części programu Visual Studio.  
  
3.  Kliknij dwukrotnie wątek **wątków** okno do bieżącego. Bieżące wątki ma żółta strzałka. Po zmianie bieżącego wątku, jego stos wywołań jest wyświetlany w **stos wywołań** okna.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Aby sprawdzić okna stosów równoległych  
  
1.  Na **debugowania** menu wskaż **Windows** , a następnie kliknij przycisk **stosów równoległych**. Upewnij się, że **wątków** jest zaznaczone pole w lewym górnym rogu.  
  
     Za pomocą **stosów równoległych** okna, można wyświetlić wiele stosy wywołań jednocześnie w jednym widoku. Na poniższej ilustracji pokazano **stosów równoległych** okna powyżej **stos wywołań** okna.  
  
     ![Widok okna stosów równoległych wątków](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")  
  
     Stos wywołań wątku głównego pojawia się w jednym polu i stosy wywołań na inne wątki cztery są pogrupowane w innym polu. Cztery wątki są grupowane razem, ponieważ ich ramek stosu używają tego samego kontekstów metody; oznacza to, że są one w tej samej metody: `A`, `B`, i `C`. Do widoku wątków identyfikatorów i nazw wątków, które współużytkują tego samego pola, umieść kursor nad nagłówek (**4 wątków**). Bieżący wątek jest wyświetlany w pogrubienie, jak pokazano na poniższej ilustracji.  
  
     ![Etykietka narzędzia, pokazujący wątku identyfikatorów i nazw](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")  
  
     Żółta strzałka wskazuje ramki stosu active bieżącego wątku. Aby uzyskać więcej informacji, umieść kursor nad nim  
  
     ![Etykietki narzędzia w ramce stosu active](../debugger/media/pdb_walkthrough_1b.png "PDB_Walkthrough_1B")  
  
     Można ustawić ilość szczegółów do wyświetlenia ramek stosu (**nazwy modułu**, **typy parametrów**, **nazwy parametrów**, **wartości parametrów**, **Numery wierszy** i **przesunięcia bajtów**) klikając prawym przyciskiem myszy **stos wywołań** okna.  
  
     Niebieskie wyróżnienie wokół pola wskazuje, czy bieżący wątek jest częścią tego pola. Bieżący wątek jest również wskazywane przez ramki stosu pogrubienia w etykietce narzędzia. Po dwukrotnym kliknięciu wątku głównego okna wątki, można zaobserwować, który niebieskie wyróżnienie w **stosów równoległych** okna przenosi odpowiednio.  
  
     ![Wyróżnione wątku głównego okna stosów równoległych](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie do drugiego punktu przerwania  
  
1.  Aby wznowić wykonywanie do momentu drugi punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**. Na poniższej ilustracji przedstawiono drzewa wątku na drugi punkt przerwania.  
  
     ![Okno stosów równoległych, który zawiera wiele gałęzi](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")  
  
     W pierwszym punktem przerwania wszystkie cztery wątki próby z S.A S.B S.C metod. Czy informacje są nadal widoczny w **stosów równoległych** okna, ale cztery wątki osiągnięcia postępu dalej. Jeden z nich nadal S.D, a następnie PD Inny nadal S.F, S.G i S.H. Dwa inne nadal S.I i S.J oraz z Brak jednej z nich próby S.K i innych nadal zewnętrznego kodu innych użytkowników.  
  
     Aktywuj przez pole nagłówka, na przykład **1 wątku** lub **2 wątkach**, aby wyświetlić wątku identyfikatory wątków. Można umieść kursor nad ramek stosu, aby zobaczyć wątku identyfikatorów oraz inne szczegóły ramki. Niebieskie wyróżnienie wskazuje bieżący wątek i żółta strzałka wskazuje ramki stosu active bieżącego wątku.  
  
     Ikona ręczników wątków (nakładających się niebieski i czerwony waved linii) wskazuje ramek stosu aktywnych wątków innych niż bieżące. W **stos wywołań** okna, kliknij dwukrotnie S.B można przełączać ramki. **Stosów równoległych** okna wskazuje bieżącą ramkę stosu bieżącego wątku, korzystając z ikony zielony zakrzywioną strzałką.  
  
     W **wątków** okna, Przełącz między wątkami i że widoku w **stosów równoległych** okna jest aktualizowany.  
  
     Można przełączyć do innego wątku lub do innej ramki inny wątek przy użyciu menu skrótów w **stosów równoległych** okna. Na przykład, kliknij prawym przyciskiem myszy S.J, wskaż polecenie **Przełącz do ramki**, a następnie kliknij przycisk polecenia.  
  
     ![Równoległych stosów ścieżka wykonywania](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")  
  
     Kliknij prawym przyciskiem myszy S.C, a następnie wskaż **Przełącz do ramki**. Jedno z poleceń ma znacznik wyboru, który wskazuje ramki stosu bieżącego wątku. Możesz przełączyć się do tej ramki tego samego wątku (przeniesie zieloną strzałkę), lub możesz przełączyć się do innego wątku (niebieskie wyróżnienie przenosi także). Na poniższej ilustracji przedstawiono podmenu.  
  
     ![Stosy menu Opcje 2 C podczas bieżącej J](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")  
  
     W przypadku skojarzone z ramki stosu tylko jeden kontekst — metoda Wyświetla pole nagłówka **1 wątku** i może przełączyć się do niego przez dwukrotne kliknięcie. Po dwukrotnym kliknięciu kontekstu metoda ma więcej niż 1 ramkę skojarzonych z nim, następnie menu automatycznie wyskakującej. Po aktywowaniu przez kontekstów — metoda zauważyć czarny trójkąt po prawej stronie. Kliknięcie tego trójkąt wyświetla również menu skrótów.  
  
     Dla dużych aplikacji, które mają wiele wątków można skupić się na tylko ich podzbiór wątków. **Stosów równoległych** można wyświetlić w oknie stosy wywołań tylko w przypadku oflagowane wątki. Na pasku narzędzi kliknij **Pokaż tylko oflagowane** przycisk obok pola listy.  
  
     ![Puste okno stosów równoległych i etykietka narzędzia](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")  
  
     Następnie w **wątków** okna, Flaga wątki jeden po drugim, aby zobaczyć, jak pojawiają się w ich stosy wywołań **stosów równoległych** okna. Aby Flaga wątków, użyj menu skrótów lub pierwszej komórki wątku. Kliknij przycisk **Pokaż tylko oflagowane** przycisku paska narzędzi ponownie, aby wyświetlić wszystkie wątki.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie do momentu trzeci punktu przerwania  
  
1.  Aby wznowić wykonywanie do momentu trzeci punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
     Wiele wątków znajdują się w tej samej metody, ale metoda nie jest na początku stos wywołań, metoda pojawia się w różnych pól. Przykładem w bieżącym punkt przerwania jest S.L, który trzech wątków w nim i jest wyświetlany w trzech pól. Kliknij dwukrotnie Brak miejsca  
  
     ![Ścieżka wykonywania w okna stosów równoległych](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")  
  
     Należy zauważyć, że S.L jest pogrubiony w dwóch polach, tak aby były widoczne else gdzie jest dostępny. Jeśli chcesz zobaczyć ramek, które wywołanie S.L i które ramki wywołania, kliknij przycisk **Przełącz widok metody** przycisk na pasku narzędzi. Na poniższej ilustracji przedstawiono widok metody **stosów równoległych** okna.  
  
     ![Metoda widok okna stosów równoległych](../debugger/media/pdw_walkthrough_4.png "PDW_Walkthrough_4")  
  
     Zwróć uwagę, jak diagram przestawiać na wybranej metody i znajduje się ona w polu środku widoku. Callees i wywoływania pojawiają się u góry i u dołu. Kliknij przycisk **Przełącz widok metody** przycisk ponownie, aby wyjść z tego trybu.  
  
     Menu skrótów **stosów równoległych** okno zawiera również następujące inne elementy.  
  
    -   **Wyświetlacz** przełącza numery w etykietkach narzędzi między dziesiętnego i szesnastkową.  
  
    -   **Obciążenia informacje o symbolach** i **ustawienia** Otwórz odpowiednich okien dialogowych.  
  
    -   **Przejdź do kodu źródłowego** i **przejść do dezasemblacji** Przejdź w edytorze wybranej metody.  
  
    -   **Pokaż kod zewnętrzny** Wyświetla wszystkie ramki, nawet jeśli nie są w kodzie użytkownika. Wypróbuj na diagramie Rozwiń, aby pomieścić dodatkowe ramki, (które mogą być nieaktywne, ponieważ nie masz symbole dla nich).  
  
     Jeśli masz dużych diagramów i krok do następnego punktu przerwania, może być widok, aby automatycznie przewiń do ramki stosu active bieżącego wątku; oznacza to, że wątek najpierw trafiony punkt przerwania. W **stosów równoległych** okna, upewnij się, że **automatycznie przewiń do bieżącej ramki stosu** znajduje się na przycisk na pasku narzędzi.  
  
     ![Autoscrolling okna stosów równoległych](../debugger/media/pdb_walkthrough_4a.png "PDB_Walkthrough_4A")  
  
2.  Przed kontynuowaniem w **stosów równoległych** okna, przewiń do końca w lewo i w dół do końca.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie do momentu czwarty punktu przerwania  
  
1.  Aby wznowić wykonywania, dopóki czwarty punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
     Powiadomienie jak autoscrolled widoku w miejscu. Przełącz wątków w **wątków** ramki stosu okna lub przełącznika **stos wywołań** okna i zwróć uwagę, jak widok zawsze autoscrolls do poprawnej ramki. Wyłącz **automatycznie przewiń do bieżącej ramki narzędzie** opcji i wyświetlanie różnicy.  
  
     **Widok** pomaga również w dużych diagramów w **stosów równoległych** okna. Widać **widok** przez kliknięcie przycisku między paski przewijania w prawym dolnym rogu okna, jak pokazano na poniższej ilustracji.  
  
     ![Ptaka &#45; oka wyświetlenia okna stosów równoległych](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")  
  
     Można przenieść prostokąt szybko przesuwanie na diagramie.  
  
     Przenoszenie diagramu w dowolnym kierunku w inny sposób jest pusty obszar diagramu, kliknij i przeciągnij w to miejsce.  
  
     Aby powiększyć i diagramu, naciśnij i przytrzymaj klawisz CTRL podczas przenoszenia kółka myszy. Alternatywnie kliknij przycisk Powiększenie na pasku narzędzi, a następnie użyć narzędzia powiększenia.  
  
     ![Powiększenie stosów w okna stosów równoległych](../debugger/media/pdb_walkthrough_5a.png "PDB_Walkthrough_5A")  
  
     Stosy można wyświetlić w kierunku góra dół zamiast dołu do góry, klikając **narzędzia** menu, klikając pozycję **opcje**, a następnie zaznacz lub usuń zaznaczenie opcji w obszarze **debugowanie** węzła.  
  
2.  Przed kontynuowaniem na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie** do zakończenia wykonywania.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Przy użyciu okno zadań równoległych i widok zadań okna stosów równoległych  
 Zalecane jest wykonanie procedur wcześniejszych przed kontynuowaniem.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Uruchom aplikację do pierwszy punkt przerwania zostaje trafiony  
  
1.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** i poczekaj, aż pierwszy punkt przerwania do trafiony.  
  
2.  Na **debugowania** menu wskaż **Windows** , a następnie kliknij przycisk **wątków**. Dock **wątków** okna w dolnej części programu Visual Studio.  
  
3.  Na **debugowania** menu wskaż **Windows** i kliknij przycisk **stos wywołań**. Dock **stos wywołań** okna w dolnej części programu Visual Studio.  
  
4.  Kliknij dwukrotnie wątek **wątków** okna sprawia, że bieżący. Bieżące wątki ma żółta strzałka. Po zmianie bieżącego wątku innych oknach zostały zaktualizowane. Następnie zostaną omówione zadania.  
  
5.  Na **debugowania** menu wskaż **Windows** , a następnie kliknij przycisk **zadań równoległych**. Na poniższej ilustracji pokazano **zadania** okna.  
  
     ![Cztery uruchomione zadania w oknie zadania](../debugger/media/pdw_walkthrough_6.png "PDW_Walkthrough_6")  
  
     Dla każdego uruchomionego zadania można znaleźć Identyfikatora, który jest zwracany przez właściwość o tej samej nazwie, identyfikator i nazwa wątku, który uruchamia go, jego lokalizacji (kursora myszy nad tym Wyświetla etykietki narzędzia, zawierający stos wywołań całego). Ponadto w obszarze **zadań** kolumny, można wyświetlić metodę, który został przekazany do zadania; innymi słowy, punktu początkowego.  
  
     Można posortować kolumny. Zwróć uwagę, symbolu sortowania, wskazującą kolumna sortowania i kierunku. Można również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo.  
  
     Żółta strzałka wskazuje bieżącego zadania. Można przełączyć zadania, klikając dwukrotnie zadania lub przy użyciu menu skrótów. Po przełączeniu zadania bieżącym staje się podstawowym wątku i innych oknach zostały zaktualizowane.  
  
     Możesz ręcznie przełączać się z jednego zadania, żółta strzałka przenosi, ale białej strzałki nadal zawiera zadania, który spowodował debugera przerwać.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Aby wznowić wykonywanie do drugiego punktu przerwania  
  
1.  Aby wznowić wykonywanie do momentu drugi punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
     Wcześniej **stan** kolumny pokazano wszystkie zadania jako uruchomiona, ale teraz dwa zadania oczekiwania. Zadania mogą zostać zablokowane w wielu różnych powodów. W **stan** kolumny, przesuń kursor myszy zadanie oczekiwania, aby dowiedzieć się, dlaczego jest zablokowany. Na przykład na poniższej ilustracji, zadanie 3 oczekuje na zadanie 4.  
  
     ![Dwa zadania oczekiwania w oknie zadania](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")  
  
     Zadanie 4, z kolei czeka na monitorze należących do wątku przypisane do zadanie 2.  
  
     ![Oczekiwanie na zadanie i etykietek narzędzi w oknie zadania](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")  
  
     Oznacz flagą zadania, klikając flagę w pierwszej kolumnie **zadania** okna.  
  
     Możesz użyć flag śledzenia zadań między różne punkty przerwania w tej samej sesji debugowania lub aby filtrować zadania, których stosy wywołań są wyświetlane w **stosów równoległych** okna.  
  
     Kiedy używać **stosów równoległych** okna wcześniej, można wyświetlić wątki aplikacji. Widok **stosów równoległych** ponownie okno, ale tym razem wyświetlania zadań aplikacji. To zrobić, wybierając **zadania** w polu w lewym górnym rogu. Na poniższej ilustracji przedstawiono widok zadań.  
  
     ![Widok okna stosów równoległych wątków](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")  
  
     Wątków, które nie są obecnie wykonuje zadania nie są wyświetlane w widoku zadań **stosów równoległych** okna. Ponadto dla wątków, które są wykonywane zadania, niektóre ramek stosu, które nie są odpowiednie do zadania są filtrowane z góry i u dołu stosu.  
  
     Widok **zadania** ponownie okno. Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, aby wyświetlić menu skrótów kolumny.  
  
     ![Menu skrótów widoku w oknie zadania](../debugger/media/pdb_walkthrough_8a.png "PDB_Walkthrough_8A")  
  
     Menu skrótów można użyć, aby dodać lub usunąć kolumny. Na przykład nie jest zaznaczone kolumny elementu AppDomain; w związku z tym nie jest wyświetlany na liście. Kliknij przycisk **nadrzędnej**. **Nadrzędnej** kolumny pojawia się bez wartości dla każdego z czterech zadania.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Aby wznowić wykonywanie do momentu trzeci punktu przerwania  
  
1.  Aby wznowić wykonywanie do momentu trzeci punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**.  
  
     Nowe zadanie zadanie 5, jest teraz uruchomiona i obecnie oczekuje zadanie 4. Widać, dlaczego, ustawiając kursor nad zadanie oczekiwania w **stan** okna. W **nadrzędnej** kolumny, powiadomienia, że zadanie 4 jest nadrzędny zadanie 5.  
  
     W celu lepszego wizualizacji relacji nadrzędny podrzędny, kliknij prawym przyciskiem myszy **nadrzędnej** nagłówek kolumny, a następnie kliknij przycisk **widok podrzędny nadrzędnej**. Poniższa ilustracja powinna zostać wyświetlona.  
  
     ![&#45;nadrzędny; Wyświetl w oknie zadania podrzędne](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")  
  
     Należy zauważyć, że zadanie 4 i 5 zadań są uruchomione na tym samym wątku. Te informacje nie są wyświetlane w **wątków** okno; niewidoczny w tym miejscu jest kolejna korzyść związana z **zadania** okna. Aby to potwierdzić, Wyświetl **stosów równoległych** okna. Upewnij się, że **zadania**. Znajdź zadania 4 i 5 przez dwukrotne kliknięcie w **zadania** okna. Powoduje to niebieskie wyróżnienie **stosów równoległych** okna jest aktualizowany. Możesz również znaleźć zadań 4 i 5, skanując etykietki narzędzi na **stosów równoległych** okna.  
  
     ![Widok okna stosów równoległych zadań](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")  
  
     W **stosów równoległych** , kliknij prawym przyciskiem myszy S.P, a następnie kliknij przycisk **przejdź do wątku**. Okno zmienia się do widoku wątków i odpowiednie ramka znajduje się w widoku. Można wyświetlić obu zadań na tym samym wątku.  
  
     ![Wyróżnione wątku w widoku wątków](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")  
  
     Jest to kolejna korzyść związana z widoku zadania w **stosów równoległych** okna w porównaniu do **wątków** okna.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Aby wznowić wykonywanie do momentu czwarty punktu przerwania  
  
1.  Aby wznowić wykonywanie do momentu trzeci punkt przerwania zostaje trafiony, na **debugowania** menu, kliknij przycisk **Kontynuuj**. Kliknij przycisk **identyfikator** nagłówek kolumny, aby posortować według identyfikatora. Poniższa ilustracja powinna zostać wyświetlona.  
  
     ![Cztery zadania stanów w okna stosów równoległych](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")  
  
     Ponieważ zadanie 5 została zakończona, jest już wyświetlany. Zakleszczenia nie będzie wyświetlana, który nie jest uruchomiona na komputerze, krok jeden raz, naciskając klawisz F11.  
  
     Zadanie 3 i 4 zadanie teraz trwa oczekiwanie na każdym z nich i są zakleszczone. Dostępne są także 5 nowe zadania, które są elementami podrzędnymi zadanie 2 i teraz zaplanowane. Zaplanowane zadania są zadania, które zostały rozpoczęte w kodzie, ale nie został jeszcze uruchomiony. W związku z tym ich **lokalizacji** i **wątku przypisania** kolumn są puste.  
  
     Widok **stosów równoległych** ponownie okno. Nagłówek każde pole ma etykietce narzędzia, która zawiera nazwy i identyfikatory wątku. Przełącz do widoku zadania w **stosów równoległych** okna. Umieść kursor nad nagłówka Identyfikatora zadania i nazwy i stan zadania, jak pokazano na poniższej ilustracji.  
  
     ![Nagłówek tooltip okna stosów równoległych](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")  
  
     Zadania można grupować według kolumny. W **zadania** okna, kliknij prawym przyciskiem myszy **stan** nagłówek kolumny, a następnie kliknij przycisk **grupowanie według stanu**. Na poniższej ilustracji pokazano **zadania** okna pogrupowane według stanu.  
  
     ![Grupowania zadań w oknie zadania](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")  
  
     Można także grupować według innej kolumny. Grupowanie zadań można skupić się na podzbiór zadań. Każda grupa zwijanej ma liczbę elementów, które są zgrupowane razem. Wszystkie elementy w grupie można szybko Flaga, klikając **flagi** przycisku z prawej strony **Zwiń** przycisku.  
  
     ![Pogrupowane stosów w okna stosów równoległych](../debugger/media/pdb_walkthrough_12a.png "PDB_Walkthrough_12A")  
  
     Funkcja ostatniego **zadania** okno do sprawdzenia jest wyświetlany po kliknięciu prawym przyciskiem myszy zadanie menu skrótów.  
  
     ![Menu skrótów okna zadań](../debugger/media/pdb_walkthrough_12b.png "PDB_Walkthrough_12B")  
  
     Menu skrótów wyświetlane inne polecenia, w zależności od stanu zadania. Może to **kopii**, **Zaznacz wszystko**, **wyświetlacz**, **przełączyć się do zadań**, **Zablokuj przypisane Wątek**, **Zablokuj wszystkie wątki oprócz to**, i **odblokować wątku przypisanej**, i **flagi**.  
  
     Można zamrozić wątku podstawowe zadania lub zadania lub można zablokować wszystkie wątki oprócz jednego przypisane. Zablokowane wątku jest reprezentowana w **zadania** okna, ponieważ znajduje się w **wątków** okna przez niebieskiego *wstrzymać* ikony.  
  
## <a name="summary"></a>Podsumowanie  
 W tym przewodniku przedstawiono **zadań równoległych** i **stosów równoległych** debugera systemu windows. Użyj tych okien w rzeczywistych projektów wielowątkowe kodu. Można sprawdzić równoległych kod napisany w języku C++, C# lub Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](/dotnet/standard/parallel-programming/index)   
 [Współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime)   
 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)   
 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)