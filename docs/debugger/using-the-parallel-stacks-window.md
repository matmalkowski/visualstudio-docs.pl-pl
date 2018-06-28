---
title: Wyświetlanie przy użyciu okna stosów równoległych wątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bc66f2017b243f94ae0012b354230aae66c76fd
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058740"
---
# <a name="view-threads-and-tasks-using-the-parallel-stacks-window"></a>Widok wątków i zadań za pomocą okna stosów równoległych
**Stosów równoległych** okno jest przydatne podczas debugowania aplikacji wielowątkowych. Jego **Widok wątków** pokazuje informacje stosu wywołań dla wszystkich wątków w aplikacji. Umożliwia nawigowanie między wątków i ramek stosu na tych wątków. W kodzie zarządzanym **widoku zadania** stosy wywołań pokazuje <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów. W kodzie natywnym **widoku zadania** stosy wywołań pokazuje [zadań grup](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algorytmy równoległe](/cpp/parallel/concrt/parallel-algorithms), [agentów asynchronicznych](/cpp/parallel/concrt/asynchronous-agents)i [zadań lekkich](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
## <a name="threads-view"></a>Widok wątków  
 Na poniższej ilustracji przedstawiono jeden wątek, który zakończył się z głównym a na B, a następnie do zewnętrznego kodu. Dwa inne wątki rozpoczynający się od zewnętrznego kodu, a następnie próby A, ale jeden z wątków nadal b, a następnie do zewnętrznego kodu i innych wątków nadal C, a następnie niektóre AnonymousMethod.  
  
 ![Widok okna stosów równoległych wątków](../debugger/media/parallel_stacksthread.png "Parallel_StacksThread")  
  
 Na ilustracji ścieżka wywołania bieżącego wątku jest zaznaczone na niebiesko i bieżącej lokalizacji (ramki stosu active) wątku jest oznaczona żółta strzałka. Bieżącej ramki stosu można zmienić, wybierając inną metodę w **stosów równoległych** okna. Może to spowodować również przełączania bieżącego wątku, w zależności od tego, czy wybrana metoda jest częścią bieżącego wątku już lub inny wątek. W poniższej tabeli opisano główne funkcje **stosów równoległych** okna, jak pokazano na rysunku.  
  
|Objaśnienie list|Nazwa elementu|Opis|  
|-|-|-|  
|ELEMENT|Segment stosu wywołań lub węzeł|Zawiera szereg metod dla co najmniej jeden wątek. Jeśli węzeł nie ma wierszy strzałkę dołączone do niego, jego reprezentuje ścieżkę całego wywołania dla wątkiem(mi).|  
|B|Niebieskie wyróżnienie|Określa ścieżkę wywołania bieżącego wątku.|  
|C|Linie strzałek|Łączenie węzłów do tworzą wywołania całą ścieżkę wątkiem(mi).|  
|D|Etykietka narzędzia węzła nagłówka|Zawiera identyfikator i nazwę użytkownika każdy wątek, których ścieżką wywołania współużytkują ten węzeł.|  
|E|Metoda|Reprezentuje jedną lub więcej ramek stosu w tej samej metody.|  
|F|Etykietka narzędzia na — metoda|W widoku wątków pokazuje wszystkie wątki w tabeli podobny do **wątków** okna. W widoku zadań pokazuje wszystkie zadania w tabeli podobny do **zadania** okna.|  
  
 Ponadto zawiera okna stosów równoległych **widok** ikonę w okienku głównym, gdy wykres jest za duży dla do okna. Możesz kliknąć ikonę, aby zobaczyć cały wykres w oknie.  
  
## <a name="stack-frame-icons"></a>Ikony ramki stosu  
 W poniższej tabeli opisano ikony, które zawierają informacje na temat ramek stosu aktywne i bieżący:  
  
|Ikona|Opis|  
|-|-|  
|![Równoległych stosów żółta strzałka](../debugger/media/icon_parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Wskazuje, że metoda zawiera bieżącą lokalizację bieżącego wątku (ramki stosu active).|  
|![Równoległych stosów ikona wątków](../debugger/media/icon_parallelthreads.gif "Icon_ParallelThreads")|Wskazuje, że metoda zawiera bieżącą lokalizację (ramki stosu active) z systemem innym niż bieżący wątek.|  
|![Równoległych stosów zieloną strzałkę](../debugger/media/icon_parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Wskazuje, że metoda zawiera bieżącą ramkę stosu (bieżącego kontekstu debugera). Podana nazwa metody jest pogrubioną we wszystkich węzłach, w których występuje.|  
  
## <a name="toolbar-controls"></a>Formanty paska narzędzi  
 Poniższe ilustracja i tabela opisano formantów, które są dostępne na pasku narzędzi stosów równoległych.  
  
 ![Pasek narzędzi okna stosów równoległych](../debugger/media/parallel_stackstoolbar.png "Parallel_StacksToolbar")  
  
|Objaśnienie list|Formant|Opis|  
|-|-|-|  
|ELEMENT|Pole kombi wątki/zadania|Przełączniki widok między stosy wątków wywołań i stosy zadań wywołań. Aby uzyskać więcej informacji zobacz widok zadań i wątków.|  
|B|Pokaż tylko oflagowane|Stosy wywołań pokazuje tylko dla wątków, które są oznaczone w innych oknach debugowania, takich jak **wątki GPU** okna i **czujki równoległej** okna.|  
|C|Przełącz widok — metoda|Przełącza między widokiem stosu i metody. Aby uzyskać więcej informacji zobacz widoku metody.|  
|D|Automatycznie przewiń do bieżącej ramki stosu|Autoscrolls diagramu, dzięki czemu ramki stosu bieżącego jest w widoku. Ta funkcja jest przydatna, gdy zmieniasz bieżącej ramki stosu w innych oknach, lub gdy są naciśnięcie nowego punktu przerwania w dużych diagramów.|  
|E|Formant powiększania przełączania|Pokazuje lub ukrywa formantu powiększenia. Można również powiększenie naciskając klawisz CTRL i kółka myszy, niezależnie od tego, widoczność formantu powiększenia, włączając lub przy użyciu klawiszy CTRL + SHIFT + '+', aby powiększyć lub CTRL + SHIFT + "-" Aby pomniejszyć. Naciśnięcie klawiszy CTRL + F8 będzie widok do rozmiaru ekranu.|  
  
### <a name="context-menu-items"></a>Elementy Menu kontekstowego  
 Poniższe ilustracja i tabela opisano elementy menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy metodę, w widoku wątków lub zadania. Ostatnich sześciu elementy są pobierają bezpośrednio z okna stosu wywołań i powodować nie nowe zachowanie.  
  
 ![Menu skrótów okna stosów równoległych](../debugger/media/parallel_contmenu.png "Parallel_ContMenu")  
  
|Element menu|Opis|  
|-|-|  
|Flaga|Flagi wybranego elementu.|  
|Usuwanie oflagowania|Unflags wybranego elementu.|  
|Blokowanie|Zawiesza się wybrany element.|  
|Odblokowania|Thaws wybranego elementu.|  
|Przejdź do zadania (wątek)|Pełni taką samą funkcję jak pole kombi na pasku narzędzi, ale zachowuje tej samej ramki stosu wyróżnione.|  
|Przejdź do kodu źródłowego|Powoduje przejście do lokalizacji w kodzie źródłowym, umożliwiająca ramki stosu, który użytkownik kliknął prawym przyciskiem myszy.|  
|Przełącz do ramki|Taka sama jak odpowiedniego polecenia menu w oknie stosu wywołań. Jednak z stosów równoległych wiele ramek mogą odpowiadać jednej metody. Dlatego element menu ma podmenu, z których każdy reprezentuje ramka stosu określone. Jeśli jeden z ramki stosu w bieżącym wątku, jest wybierana menu, która odnosi się do tej ramki stosu.|  
|Przejdź do dezasemblacji|Powoduje przejście do lokalizacji w oknie dezasemblacji umożliwiająca ramki stosu, który użytkownik kliknął prawym przyciskiem myszy.|  
|Pokaż kodu zewnętrznego|Pokazuje lub ukrywa kod zewnętrzny.|  
|Wyświetlacz|Przełącza między wyświetlania dziesiętną, a szesnastkową.|  
|Informacje dotyczące załadowania symboli|Wyświetla okno dialogowe odpowiednie.|  
|Ustawienia symboli|Wyświetla okno dialogowe odpowiednie.|  
  
## <a name="tasks-view"></a>Zadania widoku  
 Jeśli aplikacja korzysta <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów (zarządzany kod) lub `task_handle` obiektów (kod natywny) Express równoległości służy pole kombi na pasku narzędzi okna stosów równoległych Aby przełączyć się do *widoku zadania*. Zadania widoku są wyświetlane stosy wywołań zadań zamiast wątków. Zadania widoku różni się od widoku wątków w następujący sposób:  
  
-   Stosy wywołań wątków, które nie są uruchomione zadania nie są wyświetlane.  
  
-   Stosy wywołań wątków, które są uruchomione zadania wizualne są usuwane u góry i u dołu, aby wyświetlić najbardziej odpowiednie ramek, które odnoszą się do zadań.  
  
-   W przypadku wielu zadań w jednym wątku, stosy wywołań tych zadań są dzielone na osobne węzły.  
  
 Na poniższej ilustracji przedstawiono widoku zadania stosów równoległych po prawej stronie i odpowiedni widok wątki po lewej stronie.  
  
 ![Zadania widoku w okna stosów równoległych](../debugger/media/parallel_tasksview.png "Parallel_TasksView")  
  
 Aby wyświetlić cały stos wywołań, przełącz się do widoku wątków prawym przyciskiem myszy ramka stosu, a następnie klikając polecenie **przejdź do wątku**.  
  
 Zgodnie z opisem w tabeli wcześniej, ustawiając kursor nad metodą, znajdują się dodatkowe informacje. Na poniższej ilustracji przedstawiono informacji w etykietce narzędzia dla widoku wątków i widok zadań.  
  
 ![Etykietki narzędzi w okna stosów równoległych](../debugger/media/parallel_stack_tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Widok — metoda  
 Z wątków widoku lub widok zadań klikając ikonę widoku metody, na pasku narzędzi można przestawiać wykres w bieżącej metodzie. Widoku metody zawiera krótki przegląd wszystkie metody wszystkie wątki, które wywołania lub są wywoływane przy bieżącej metody. Na poniższej ilustracji przedstawiono widok wątków, a także wygląd tych samych informacji w widoku metody.  
  
 ![Metoda widok okna stosów równoległych](../debugger/media/parallel_methodview.png "Parallel_MethodView")  
  
 Przełączając nowej ramki stosu, można spowodować metoda bieżącej metody i do wyświetlenia wszystkich obiektów wywołujących i callees dla nowej metody w oknie. Może to spowodować, że niektóre wątki są wyświetlane lub usuwane z widoku, w zależności od tego, czy metoda jest wyświetlane na ich stosy wywołań. Aby powrócić do widoku stosu, kliknij ponownie przycisk paska narzędzi widoku metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Wskazówki: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](/dotnet/standard/parallel-programming/index)   
 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)   
 [Task — klasa](../extensibility/debugger/task-class-internal-members.md)
