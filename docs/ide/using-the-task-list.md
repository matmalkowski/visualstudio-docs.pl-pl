---
title: Zapoznaj się z listą zadań
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 4a82663fe397488ee78a82d4fab5d38bfec4ae37
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-the-task-list"></a>Zapoznaj się z listą zadań

Użyj **listy zadań** do śledzenia komentarze w kodzie, takich jak używających tokenów `TODO` i `HACK`, lub tokeny niestandardowe i zarządzać skrótów, które spowoduje przejście bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do lokalizacji w kodzie źródłowym.

## <a name="the-task-list-window"></a>Okno Lista zadań

Gdy **listy zadań** jest otwarty, prawdopodobnie w dolnej części okna aplikacji.

### <a name="open-the-task-list"></a>Otwarcie listy zadań

- Na **widoku** menu, wybierz **listy zadań** (klawiatury: **Ctrl**+**\\**,**T**).

    ![W oknie Lista zadań](../ide/media/vs2015_task_list.png "vs2015_task_list")

### <a name="change-the-sort-order-of-the-list"></a>Zmień kolejność sortowania listy

- Kliknij nagłówek dowolnej kolumny. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i kliknij nagłówek drugiej kolumny.

     Alternatywnie, w menu skrótów wybierz **sortować**i wybierz nagłówek. Aby uściślić wyniki wyszukiwania, naciśnij klawisz **Shift** i wybierz nagłówek drugiego.

### <a name="show-or-hide-columns"></a>Pokazywanie lub ukrywanie kolumn

- W menu skrótów wybierz **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.

### <a name="change-the-order-of-the-columns"></a>Zmień kolejność kolumn

- Przeciągnij dowolny nagłówek kolumny do żądanej lokalizacji.

## <a name="user-tasks"></a>Zadania użytkownika

Funkcja zadań użytkownika została usunięta począwszy od programu Visual Studio 2015. Po otwarciu rozwiązania, które zawiera dane zadanie użytkownika z Visual Studio 2013 i starszych wersji użytkownika zadań danych w sieci *.suo* pliku nie zostaną zmienione, ale użytkownika zadania nie będą wyświetlane na liście zadań.

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

Domyślnie program Visual Studio zawiera następujących tokenów: `HACK`, `TODO`, `UNDONE`, `NOTE`. Nie są z uwzględnieniem wielkości liter.

Można również utworzyć własne niestandardowe tokeny.

#### <a name="create-a-custom-token"></a>Tworzenie tokenu niestandardowego

1. Na **narzędzia** menu, wybierz **opcje**.

2. Otwórz **środowiska** folder, a następnie wybierz **listy zadań**.

     [Strona Opcje listy zadań](../ide/reference/task-list-environment-options-dialog-box.md) jest wyświetlany.

     ![Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")

3. W **tokenów** kategorii w **nazwa** polu tekstowym wprowadź nazwę token, na przykład "USTEREK".

4. W **priorytet** listy rozwijanej wybierz priorytet domyślny nowy token. Wybierz **Dodaj** przycisku.

###  <a name="cppComments"></a> Komentarze C++ TODO

Domyślnie komentarze C++ TODO są wyświetlane w **listy zadań** okna. Aby zmienić to zachowanie.

#### <a name="turn-off-c-todo-comments"></a>Wyłącz komentarze C++ TODO

Na **narzędzia** menu, wybierz **opcje** > **Edytor tekstu** > **C/C++**  >   **Widok** > **wyliczyć komentarz do zadań** i ustaw wartość false.

## <a name="shortcuts"></a>Skróty

A *skrótów* jest zakładek w kodzie, które są śledzone w **listy zadań**; ma inną ikonę niż regularne zakładki. Kliknij dwukrotnie skrót w **listy zadań** można przejść do odpowiedniej lokalizacji w kodzie.

![Ikona skrótu listy zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")

### <a name="create-a-shortcut"></a>Tworzenie skrótu

Aby utworzyć skrót, Wstaw wskaźnik do kodu, w której chcesz umieścić skrót. Wybierz **Edytuj** > **zakładki** > **Dodaj skrót do listy zadań** lub naciśnij klawisz **Ctrl** + **K**, **Ctrl**+**H**.

Do nawigowania skróty w kodzie, wybierz skrót na liście, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz także

- [Lista, środowisko, opcje — Okno dialogowe zadań](../ide/reference/task-list-environment-options-dialog-box.md)