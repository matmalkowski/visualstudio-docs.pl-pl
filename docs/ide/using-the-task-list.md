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
ms.openlocfilehash: 46a156e7f016c0966321240f5ae2362f2bc161e7
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336074"
---
# <a name="use-the-task-list"></a>Zapoznaj się z listą zadań

Użyj **listy zadań** do śledzenia komentarze w kodzie, takich jak używających tokenów `TODO` i `HACK`, lub tokeny niestandardowe i zarządzać skróty klawiaturowe przejście bezpośrednio do wstępnie zdefiniowaną lokalizację w kodzie. Kliknij element na liście, aby przejść do lokalizacji w kodzie źródłowym.

## <a name="the-task-list-window"></a>Okno Lista zadań

Gdy **listy zadań** jest otwarty, prawdopodobnie w dolnej części okna aplikacji.

Aby otworzyć **listy zadań**, wybierz pozycję **widoku** > **listy zadań**, lub naciśnij klawisz klawiatury **Ctrl** + **\\**,**T**.

![okno listy zadań](../ide/media/vs2015_task_list.png)

Aby zmienić kolejność sortowania listy, wybierz nagłówka kolumny. Aby uściślić wyniki wyszukiwania, naciśnij klawisz **Shift** i kliknij pozycję drugiego nagłówka kolumny. Alternatywnie, w menu skrótów wybierz **sortować**, a następnie wybierz pozycję nagłówka. Aby uściślić wyniki wyszukiwania, naciśnij klawisz **Shift** i wybierz nagłówek drugiego.

Aby wyświetlić lub ukryć kolumny, w menu skrótów wybierz **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.

Aby zmienić kolejność kolumn, przeciągnij nagłówek dowolnej kolumny do dowolnej lokalizacji.

## <a name="user-tasks"></a>Zadania użytkownika

Funkcja zadań użytkownika został usunięty w programie Visual Studio 2015. Po otwarciu rozwiązania, które ma dane zadanie użytkownika z Visual Studio 2013 i starszych wersji użytkownika zadań danych w sieci *.suo* nie wpływa na plik, ale zadania użytkownika nie są wyświetlane na liście zadań.

Jeśli chcesz nadal dostępu i zaktualizować swoje dane zadanie, otwórz projekt w programie Visual Studio 2013 i skopiuj zawartość żadnych zadań użytkownika do narzędzia do zarządzania projektem preferowanych sieci (na przykład Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny i komentarze

Komentarz w kodzie poprzedzone znacznika komentarza i wstępnie zdefiniowanych token jest także wyświetlany w **listy zadań**. Na przykład, poniższy komentarz C# ma trzy oddzielne części:

- Znacznika komentarza (`//`)

- Token, na przykład (`TODO`)

- Komentarz (reszta tekstu)

```csharp
// TODO: Load state from previously suspended application
```

Ponieważ `TODO` jest wstępnie zdefiniowanej tokenu, ten komentarz jest wyświetlany jako `TODO` zadanie na liście.

### <a name="custom-tokens"></a>Tokeny niestandardowe

Domyślnie program Visual Studio zawiera następujących tokenów: `HACK`, `TODO`, `UNDONE`, i `NOTE`. Nie są one z uwzględnieniem wielkości liter.

Można również utworzyć własne niestandardowe tokeny. Aby utworzyć niestandardowy token:

1. Na **narzędzia** menu, wybierz **opcje**.

2. Otwórz **środowiska** folder, a następnie wybierz **listy zadań**.

   [Strona Opcje listy zadań](../ide/reference/task-list-environment-options-dialog-box.md) jest wyświetlany.

   ![Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_options.png)

3. W **tokenów** kategorii w **nazwa** tekst na przykład wprowadź nazwę token **USTERKI**.

4. W **priorytet** listy rozwijanej wybierz priorytet domyślny nowy token. Wybierz **Dodaj** przycisku.

### <a name="c-todo-comments"></a>Komentarze C++ TODO

Domyślnie komentarze C++ TODO są wyświetlane w **listy zadań**.

Aby wyłączyć komentarze C++ TODO na **narzędzia** menu, wybierz **opcje** > **Edytor tekstu** > **C/C++**  >  **Widoku** > **wyliczyć komentarz do zadań**i ustaw wartość **false**.

## <a name="shortcuts"></a>Skróty

A *skrótów* jest zakładek w kodzie, które są śledzone w **listy zadań**. Ma inną ikonę niż regularne zakładki. Kliknij dwukrotnie skrót w **listy zadań** można przejść do odpowiedniej lokalizacji w kodzie.

![Ikona skrótu listy zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Tworzenie skrótu

Aby utworzyć skrót, Wstaw wskaźnik do kodu, w której chcesz umieścić skrót. Wybierz **Edytuj** > **zakładki** > **Dodaj skrót do listy zadań** lub naciśnij klawisz **Ctrl** + **K**, **Ctrl**+**H**.

Do nawigowania skróty w kodzie, wybierz skrót na liście, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz także

- [Lista, środowisko, opcje — Okno dialogowe zadań](../ide/reference/task-list-environment-options-dialog-box.md)