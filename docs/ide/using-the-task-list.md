---
title: Korzystanie z listy zadań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef9b3904ce06c498518d55b0d62b8e9393c75239
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-task-list"></a>Korzystanie z listy zadań

Użyj **listy zadań** do śledzenia komentarze w kodzie, takich jak używających tokenów `TODO` i `HACK`, lub tokeny niestandardowe i zarządzać skrótów, które spowoduje przejście bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do lokalizacji w kodzie źródłowym.

## <a name="the-task-list-window"></a>Okno Lista zadań

Gdy **listy zadań** jest otwarty, prawdopodobnie w dolnej części okna aplikacji.

### <a name="to-open-the-task-list"></a>Aby otworzyć Listę zadań

- Na **widoku** menu, wybierz **listy zadań** (klawiatury: Ctrl +\\, T).

    ![W oknie Lista zadań](../ide/media/vs2015_task_list.png "vs2015_task_list")

### <a name="to-change-the-sort-order-of-the-list"></a>Aby zmienić kolejność sortowania listy

- Kliknij nagłówek dowolnej kolumny. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i kliknij nagłówek drugiej kolumny.

     Alternatywnie, w menu skrótów wybierz **sortować**i wybierz nagłówek. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i wybierz drugi nagłówek.

### <a name="to-show-or-hide-columns"></a>Aby pokazać lub ukryć kolumny

- W menu skrótów wybierz **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.

### <a name="to-change-the-order-of-the-columns"></a>Aby zmienić kolejność kolumn

- Przeciągnij dowolny nagłówek kolumny do żądanej lokalizacji.

## <a name="user-tasks"></a>Zadania użytkownika

Funkcja zadań użytkownika została usunięta począwszy od programu Visual Studio 2015. Po otwarciu rozwiązania, które są dane zadanie użytkownika z Visual Studio 2013 i starszej danych zadań użytkownika w pliku .suo nie zostaną zmienione, ale użytkownika zadania nie będą wyświetlane na liście zadań.

Jeśli chcesz nadal dostępu i zaktualizować swoje dane zadań należy Otwórz projekt w programie Visual Studio 2013 i skopiuj zawartość żadnych zadań użytkownika do narzędzia do zarządzania projektem preferowanych sieci (na przykład Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny i komentarze

Komentarz w kodzie poprzedzone znacznika komentarza i wstępnie zdefiniowanych tokenu są również wyświetlane w **listy zadań** okna. Na przykład, poniższy komentarz C# ma trzy oddzielne części:

- Znacznika komentarza (`//`)

- Token, na przykład (`TODO`)

- Komentarz (reszta tekstu)

```csharp
// TODO: Load state from previously suspended application
```

Ponieważ `TODO` jest wstępnie zdefiniowanej tokenu, ten komentarz jest wyświetlany jako `TODO` zadanie na liście.

###  <a name="customTokens"></a> Tokeny niestandardowe

Domyślnie program Visual Studio zawiera następujących tokenów: HACK, TODO, COFNIĘTO, Uwaga. Nie są z uwzględnieniem wielkości liter.

Można również utworzyć własne niestandardowe tokeny.

#### <a name="to-create-a-custom-token"></a>Aby utworzyć niestandardowy token

1. Na **narzędzia** menu, wybierz **opcje**.

2. Otwórz **środowiska** folder, a następnie wybierz **listy zadań**.

     [Strona Opcje listy zadań](../ide/reference/task-list-environment-options-dialog-box.md) jest wyświetlany.

     ![Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")

3. W **tokenów** kategorii w **nazwa** polu tekstowym wprowadź nazwę token, na przykład "USTEREK".

4. W **priorytet** listy rozwijanej wybierz priorytet domyślny nowy token. Wybierz **Dodaj** przycisku.

###  <a name="cppComments"></a> Komentarze C++ TODO

Domyślnie komentarze C++ TODO są wyświetlane w **listy zadań** okna. Aby zmienić to zachowanie.

#### <a name="to-turn-off-c-todo-comments"></a>Aby wyłączyć komentarze C++ TODO

Na **narzędzia** menu, wybierz **opcje** > **Edytor tekstu** > **C/C++**  >   **Widok** > **wyliczyć komentarz do zadań** i ustaw wartość false.

## <a name="shortcuts"></a>Skróty

A *skrótów* jest zakładek w kodzie, które są śledzone w **listy zadań**; ma inną ikonę niż regularne zakładki. Kliknij dwukrotnie skrót w **listy zadań** można przejść do odpowiedniej lokalizacji w kodzie.

![Ikona skrótu listy zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")

### <a name="to-create-a-shortcut"></a>Aby utworzyć skrót

Aby utworzyć skrót, Wstaw wskaźnik do kodu, w której chcesz umieścić skrót. Wybierz **Edytuj** > **zakładki** > **Dodaj skrót do listy zadań** lub naciśnij klawisz **Ctrl**  +  **K**, **Ctrl** + **H**.

Do nawigowania skróty w kodzie, wybierz skrót na liście, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz także

[Zadanie listy, środowisko, opcje — Okno dialogowe](../ide/reference/task-list-environment-options-dialog-box.md)