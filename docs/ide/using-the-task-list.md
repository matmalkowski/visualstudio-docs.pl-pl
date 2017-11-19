---
title: "Korzystanie z listy zadań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a380d0e1503a0a0a0683d6088a1ca2f9c085184d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-task-list"></a>Korzystanie z listy zadań
Użyj **listy zadań** do śledzenia komentarze w kodzie, takich jak używających tokenów `TODO` i `HACK`, lub tokeny niestandardowe i zarządzać skrótów, które spowoduje przejście bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do lokalizacji w kodzie źródłowym.  
  
 W tym temacie:  
  
-   [W oknie Lista zadań](../ide/using-the-task-list.md#taskListWindow)  
  
-   [Zadania użytkownika](../ide/using-the-task-list.md#userTasks)  
  
-   [Tokeny i komentarze](../ide/using-the-task-list.md#tokensComments)  
  
-   [Tokeny niestandardowe](../ide/using-the-task-list.md#customTokens)  
  
-   [Komentarze C++ TODO](../ide/using-the-task-list.md#cppComments)  
  
-   [Skróty](../ide/using-the-task-list.md#shortcuts)  
  
##  <a name="taskListWindow"></a>W oknie Lista zadań  
 Gdy **listy zadań** jest otwarty, prawdopodobnie w dolnej części okna aplikacji.  
  
#### <a name="to-open-the-task-list"></a>Aby otworzyć Listę zadań  
  
-   Na **widoku** menu, wybierz **listy zadań** (klawiatury: Ctrl +\\, T).  
  
     ![W oknie Lista zadań](../ide/media/vs2015_task_list.png "vs2015_task_list")  
  
#### <a name="to-change-the-sort-order-of-the-list"></a>Aby zmienić kolejność sortowania listy  
  
-   Kliknij nagłówek dowolnej kolumny. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i kliknij nagłówek drugiej kolumny.  
  
     Alternatywnie, w menu skrótów wybierz **sortować**i wybierz nagłówek. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i wybierz drugi nagłówek.  
  
#### <a name="to-show-or-hide-columns"></a>Aby pokazać lub ukryć kolumny  
  
-   W menu skrótów wybierz **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.  
  
#### <a name="to-change-the-order-of-the-columns"></a>Aby zmienić kolejność kolumn  
  
-   Przeciągnij dowolny nagłówek kolumny do żądanej lokalizacji.  
  
##  <a name="userTasks"></a>Zadania użytkownika  
 Funkcja zadań użytkownika została usunięta w programie Visual Studio 2015. Po otwarciu rozwiązania, które są dane zadanie użytkownika z Visual Studio 2013 i wcześniej w programie Visual Studio 2015, dane zadanie użytkownika w pliku .suo nie zostaną zmienione, ale użytkownika zadania nie będą wyświetlane na liście zadań.  
  
 Jeśli chcesz nadal dostępu i zaktualizować swoje dane zadań należy Otwórz projekt w programie Visual Studio 2013 i skopiuj zawartość żadnych zadań użytkownika do narzędzia do zarządzania projektem preferowanych sieci (na przykład Team Foundation Server).  
  
##  <a name="tokensComments"></a>Tokeny i komentarze  
 Komentarz w kodzie poprzedzone znacznika komentarza i wstępnie zdefiniowanych tokenu są również wyświetlane w **listy zadań** okna. Na przykład, poniższy komentarz C# ma trzy oddzielne części:  
  
-   Znacznika komentarza (`//`)  
  
-   Token, na przykład (`TODO`)  
  
-   Komentarz (reszta tekstu)  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 Ponieważ `TODO` jest wstępnie zdefiniowanej tokenu, ten komentarz jest wyświetlany jako `TODO` zadanie na liście.  
  
###  <a name="customTokens"></a>Tokeny niestandardowe  
 Domyślnie program Visual Studio zawiera następujących tokenów: HACK, TODO, COFNIĘTO, Uwaga. Nie są z uwzględnieniem wielkości liter.  
  
 Można również utworzyć własne niestandardowe tokeny.  
  
##### <a name="to-create-a-custom-token"></a>Aby utworzyć niestandardowy token  
  
1.  Na **narzędzia** menu, wybierz **opcje**.  
  
2.  Otwórz **środowiska** folder, a następnie wybierz **listy zadań**.  
  
     [Listy zadań, środowisko, opcje — Okno dialogowe](../ide/reference/task-list-environment-options-dialog-box.md) jest wyświetlany.  
  
     ![Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")  
  
3.  W **tokenów** kategorii w **nazwa** polu tekstowym wprowadź nazwę token, na przykład "USTEREK".  
  
4.  W **priorytet** listy rozwijanej wybierz priorytet domyślny nowy token. Wybierz **Dodaj** przycisku.  
  
###  <a name="cppComments"></a>Komentarze C++ TODO  
 Domyślnie komentarze C++ TODO są wyświetlane w **listy zadań** okna. Aby zmienić to zachowanie.  
  
##### <a name="to-turn-off-c-todo-comments"></a>Aby wyłączyć komentarze C++ TODO  
  
1.  Na **narzędzia** menu, przejdź do **Opcje &#124; Edytor tekstu &#124; C/C++ &#124; Wyświetl &#124; Wyliczanie zadań w komentarzach** i ustaw wartość false.  
  
2.  W **opcje** po otwarciu okna dialogowego **Edytor tekstu**.  
  
3.  W obszarze **C/C++**, wybierz **widoku**, a następnie ustaw **wyliczyć komentarz do zadań** do **False**.  
  
##  <a name="shortcuts"></a>Skróty  
 A *skrótów* jest zakładek w kodzie, które są śledzone w **listy zadań**; ma inną ikonę niż regularne zakładki. Kliknij dwukrotnie skrót w **listy zadań** można przejść do odpowiedniej lokalizacji w kodzie.  
  
 ![Ikona skrótu listy zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")  
  
#### <a name="to-create-a-shortcut"></a>Aby utworzyć skrót  
  
-   Wstaw wskaźnik do kodu, w którym chcesz umieścić skrót. Wybierz **Edytuj &#124; Zakładki &#124; Dodaj skrót do listy zadań** lub naciśnij klawisz (klawiatury: Ctrl + K, Ctrl + H).  
  
     Do nawigowania skróty w kodzie, wybierz skrót na liście, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadanie listy, środowisko, opcje — Okno dialogowe](../ide/reference/task-list-environment-options-dialog-box.md)