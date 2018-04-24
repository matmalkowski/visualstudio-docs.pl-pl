---
title: Korzystanie z okna zadań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85319575766ca9ff3ace297bf1e4e577d49ee6d9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="using-the-tasks-window"></a>Korzystanie z okna zadań
**Zadania** podobny okna **wątków** okna, z wyjątkiem, że pokazywane są informacje o <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class), lub [WinJS.Promise ](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) obiektów zamiast każdy wątek. Podobnie jak wątków zadania reprezentują operacje asynchroniczne, które można uruchomić jednocześnie; wiele zadań mogą uruchamiać na tym samym wątku. 
  
 W kodzie zarządzanym, można użyć **zadania** okno podczas pracy z <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów lub **await** i **async** słowa kluczowe (**Await** i **Async** w języka Visual Basic). Aby uzyskać więcej informacji o zadaniach w kodzie zarządzanym, zobacz [programowania równoległego](/dotnet/standard/parallel-programming/index).  
  
 W kodzie natywnym, można użyć **zadania** okno podczas pracy z [zadań grup](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algorytmy równoległe](/cpp/parallel/concrt/parallel-algorithms), [agentów asynchronicznych](/cpp/parallel/concrt/asynchronous-agents), i [zadań lekkich](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Aby uzyskać więcej informacji o zadaniach w kodzie natywnym, zobacz [współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime).  
  
 W języku JavaScript, korzystając z okna zadań podczas pracy z promise `.then` kodu. Zobacz [asynchronicznego programowania w języku JavaScript (aplikacji platformy UWP)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) Aby uzyskać więcej informacji.   
  
 Można użyć **zadania** okna przy każdym przerwanie w debugerze. Można do niego dostęp na **debugowania** menu, klikając **Windows** , a następnie klikając polecenie **zadania**. Na poniższej ilustracji pokazano **zadania** okna w jego domyślny tryb.  
  
 ![Okno zadania](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  W kodzie zarządzanym <xref:System.Threading.Tasks.Task> mający stan <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus>, lub <xref:System.Threading.Tasks.TaskStatus> nie może być wyświetlany w oknie zadania, w przypadku zarządzanych wątków w stan uśpienia lub sprzężenia.  
  
## <a name="tasks-column-information"></a>Informacje o zadaniach w kolumnie  
 Kolumn w **zadania** okna zawierają następujące informacje.  
  
|Nazwa kolumny|Opis|  
|-----------------|-----------------|  
|**Flagi**|Przedstawia zadania, które są oznaczone i umożliwia flaga lub usuwanie oflagowania zadania.|  
|**Ikony**|Żółta strzałka wskazuje bieżącego zadania. Bieżące zadanie jest zadaniem najwyższy w bieżącym wątku.<br /><br /> Białe strzałka oznacza zadanie podziału, czyli jedną, która była bieżąca, gdy debuger został wywołany.<br /><br /> Ikona Wstrzymaj wskazuje zadanie, które zostały zablokowane przez użytkownika. Można blokowanie i odblokowywanie zadania przez kliknięcie prawym przyciskiem myszy na liście.|  
|**ID**|Liczba dostarczane przez system dla zadania. W kodzie natywnym jest to adres zadania.|  
|**Status**|Bieżący stan (zaplanowane, aktywnych, zablokowany, zakleszczenia, oczekiwanie na lub ukończone) zadania. Zaplanowane zadanie to taki, który nie został jeszcze uruchomiony i dlatego nie ma jeszcze stos wywołań, przypisane wątku lub powiązane informacje.<br /><br /> Aktywne zadanie to taki, który został wykonywanie kodu przed przerwaniem w debugerze.<br /><br /> Oczekiwanie na lub zablokowane zadań to taki, który jest zablokowane, ponieważ oczekuje na zdarzenie, aby zostać zgłoszony, zwolnienie blokady lub na zakończenie innego zadania.<br /><br /> Zakleszczenia zadanie jest zadanie oczekiwania wątku, którego jest zakleszczone przez inny wątek.<br /><br /> Umieść kursor nad **stan** komórki do zakleszczenia lub Oczekiwanie na zadanie, aby zobaczyć więcej informacji na temat bloku. **Ostrzeżenie:** **zadania** okna raporty zakleszczenie tylko dla zablokowanych zadania, która używa typu pierwotnego synchronizacji, która jest obsługiwana przez przechodzenie łańcucha oczekiwania (WCT). Na przykład do zakleszczenia <xref:System.Threading.Tasks.Task> obiektu, który używa WCT, raporty debuger **zakleszczone oczekujące**. Zakleszczenia zadania, którymi zarządza współbieżność środowiska wykonawczego, który nie używa WCT, raporty debuger **oczekiwania**. Aby uzyskać więcej informacji na temat WCT, zobacz [oczekiwania przechodzenie łańcucha](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Godzina rozpoczęcia**|Czas, w którym zadanie stał się aktywny.|  
|**Czas trwania**|Liczba sekund, które zadania była aktywna.|  
|**Czas ukończenia**|Czas, jaką zadanie ukończone.|  
|**Lokalizacja**|Bieżąca lokalizacja w stosie wywołań zadania. Umieść kursor nad tej komórki, aby zobaczyć cały stos wywołań dla zadania. Zaplanowane zadania nie mają wartości w tej kolumnie.|  
|**Zadanie**|Metoda początkowej i argumenty, które zostały przekazane do zadania, jeśli został on utworzony.|  
|**AsyncState**|Dla zarządzanego kodu stanu zadania. Domyślnie ta kolumna jest ukryta. Aby wyświetlić tę kolumnę, otwórz menu kontekstowe dla jednego z nagłówków kolumn. Wybierz **kolumn**, **AsyncState**.|  
|**Nadrzędny**|Identyfikator zadania, które tego zadania. Jeśli to pole jest puste, zadanie nie ma nadrzędnego. Dotyczy tylko programów zarządzanych.|  
|**Przypisanie wątku**|Identyfikator i nazwa wątku, w którym zadanie jest uruchomione.|  
|**Domeny aplikacji**|Dla zarządzanego kodu domeny aplikacji, w którym jest wykonywane zadanie.|  
|**task_group**|Dla kodu natywnego adresu [task_group](/cpp/parallel/concrt/reference/task-group-class.mdd) obiekt, który zaplanowane zadanie. Dla agentów asynchronicznych i zadań lekkich w tej kolumnie jest równa 0.|  
|**Proces**|Identyfikator procesu uruchomionego na zadania.|  
  
 Prawym przyciskiem myszy nagłówek kolumny, a następnie wybierając kolumny, które mają można dodać kolumny do widoku. (Usunąć kolumny przez wyczyszczenie zaznaczenia). Można również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo. Na poniższej ilustracji przedstawiono menu skrótów kolumny.  
  
 ![Menu skrótów widoku w oknie zadania](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Sortowanie zadań  
 Aby posortować zadania według kolumny kryteriów, kliknij nagłówek kolumny. Na przykład przez kliknięcie przycisku **identyfikator** nagłówka kolumny można posortować zadania według Identyfikatora zadania: 1,2,3,4,5 i tak dalej. Aby odwrócić porządek sortowania, kliknij nagłówek kolumny ponownie. Bieżącej kolumny i sortowanie kolejność sortowania jest oznaczony za pomocą strzałki w kolumnie.  
  
## <a name="grouping-tasks"></a>Grupowanie zadań  
 Można grupować według dowolnej kolumny w widoku listy zadań. Na przykład przez kliknięcie prawym przyciskiem myszy **stan** nagłówek kolumny, a następnie klikając pozycję **Grupuj według** > **[*stan*]**, możesz Grupa wszystkich zadań, które jest taki sam. Na przykład można szybko Zobacz, oczekiwanie na zadania, dzięki czemu można skupić się na dlaczego są blokowane. Można również Zwiń grupę, która nie jest przydatne podczas sesji debugowania. W ten sam sposób można grupować według innych kolumn. Grupy mogą być (małe) tylko przez kliknięcie przycisku obok nagłówka grupy. Na poniższej ilustracji pokazano **zadania** okna w trybie grupowanych.  
  
 ![Tryb zgrupowane w oknie zadania](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Widok podrzędny nadrzędnego  
 (Ten widok jest dostępny tylko kodu zarządzanego). Klikając prawym przyciskiem myszy **stan** nagłówek kolumny, a następnie klikając pozycję **Grupuj według** > **nadrzędnej**, aby hierarchiczny widok, w którym można zmienić na liście zadań Każde zadanie podrzędne jest podrzędny węzła, który można wyświetlić lub ukryć nadrzędnej. 
  
## <a name="flagging-tasks"></a>Flagowanie zadania  
 Mogą oznaczać wątku zadania, na którym działa zadanie, wybierając zadanie listy element, a następnie wybierając **flagę wątku przypisane** z menu kontekstowego lub po kliknięciu ikony flagi, w pierwszej kolumnie. Jeśli flaga kilka zadań, następnie można sortować kolumny flagi można wyświetlić oflagowanych zadań do góry, dzięki czemu można skupić się tylko na. Można również użyć **stosów równoległych** okna, aby wyświetlić tylko oflagowane zadania. Pozwala to odfiltrowywania zadania, które nie jest konieczne w celu debugowania. Flagi nie są zachowywane między sesji debugowania.  
  
## <a name="freezing-and-thawing-tasks"></a>Zamrażanie i odblokowania zadania  
 Można zamrozić wątku uruchomienie prawym przyciskiem myszy element listy zadań, a następnie klikając pozycję zadania **zamrozić wątku przypisane**. (Jeśli zadanie jest już zablokowany, to polecenie jest **odblokowania przypisane wątku**.) Po zablokowaniu wątku wątek nie zostanie wykonany, gdy krokowo kodu po bieżącym punktu przerwania. **Zablokuj wszystkie wątki, ale ten jeden** polecenie zawiesza się wszystkie wątki oprócz jednego, który jest wykonywany elementu listy zadań.
  
 Na poniższej ilustracji przedstawiono inne elementy menu dla każdego zadania.  
  
 ![Menu skrótów wątku w oknie zadania](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")  

## <a name="switching-the-active-task-or-frame"></a>Przełączanie aktywne zadanie lub ramki

**Przełączyć się do zadań** polecenie sprawia, że bieżące zadanie aktywne zadanie. **Przełącz do ramki** polecenie sprawia, że stosu wybranej ramki ramki stosu active. Zmienia kontekstu debugera do bieżącego zadania lub ramki stosu wybrane.

## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](/dotnet/standard/parallel-programming/index)   
 [Współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime)   
 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)   
 [Wskazówki: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)