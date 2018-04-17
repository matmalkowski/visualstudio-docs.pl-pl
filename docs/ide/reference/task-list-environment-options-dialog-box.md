---
title: Lista zadań, środowisko, opcje ― Okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31aa18a219d49f3f18e8b98fbe010141cf5e69c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="task-list-environment-options-dialog-box"></a>Lista zadań, środowisko, opcje — Okno dialogowe
Ta strona Opcje umożliwia dodawanie, usuwanie i zmienić tokenów komentarzy, które generują **listy zadań** przypomnienia. Aby wyświetlić te ustawienia, wybierz **opcje** z **narzędzia** menu, rozwiń węzeł **środowiska** folderu i wybierz polecenie **listy zadań**.  
  
## <a name="task-list-options"></a>Opcje listy zadań  
 Potwierdź usunięcie zadań  
 Po wybraniu okno komunikatu jest wyświetlane zawsze, gdy zadanie użytkownika są usuwane z **listy zadań**, co umożliwia potwierdzenie usunięcia. Ta opcja jest domyślnie wybrana.  
  
> [!NOTE]
>  Aby usunąć komentarz zadań, użyj łącza, aby znaleźć komentarz, a następnie usuń go z kodu.  
  
 Wyświetl tylko nazwy pliku  
 Po wybraniu **pliku** kolumny **listy zadań** wyświetla tylko nazwy plików można edytowane, nie ich pełnej ścieżki.  
  
## <a name="tokens"></a>Tokeny  
 Gdy Wstaw komentarz do kodu, w których tekst rozpoczyna się od tokenu z **lista tokenów**, **listy zadań** Wyświetla komentarz jako nowy wpis w każdym przypadku, gdy plik jest otwarty do edycji. Kliknij ten przycisk **listy zadań** wpis, aby przejść bezpośrednio do wiersza komentarz w kodzie. Aby uzyskać więcej informacji, zobacz [korzystanie z listy zadań](../../ide/using-the-task-list.md).  
  
 lista tokenów  
 Wyświetla listę tokenów i umożliwia dodawanie lub usuwanie tokeny niestandardowe. Tokeny komentarza to rozróżnianiem wielkości liter w języku C# i Visual C++, ale nie w języku Visual Basic.  
  
> [!NOTE]
>  Jeśli nie wpiszesz żądanego tokenu dokładnie w brzmieniu podanym w **lista tokenów**, komentarza zadania nie będą wyświetlane w **listy zadań**.  
  
 Priorytet  
 Ustawia priorytet zadania korzystające z wybranych tokenu. Komentarze zadań, które zaczynają się od tokenu są automatycznie przypisywane wyznaczonych priorytet w **listy zadań**.  
  
 Nazwa  
 Wprowadź ciąg tokena. Dzięki temu **Dodaj** przycisku. Na **Dodaj**, ten ciąg jest uwzględniona w **lista tokenów**, i komentarze zaczynające się ta nazwa będzie wyświetlana w **listy zadań**.  
  
 Dodaj  
 Włączone po wprowadzeniu nowego **nazwa**. Kliknij, aby dodać nowy ciąg tokenu przy użyciu wartości wprowadzone w **nazwa** i **priorytet** pola.  
  
 Usuwanie  
 Kliknij, aby usunąć wybrany token z **lista tokenów**. Nie można usunąć domyślnego tokenu komentarza.  
  
 Zmiana  
 Kliknij, aby wprowadzić zmiany w istniejących tokenu przy użyciu wartości wprowadzone w **nazwa** i **priorytet** pola.  
  
> [!NOTE]
>  Nie można zmienić ani usunąć domyślny token komentarza, ale można zmienić jego poziom priorytetu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z listy zadań](../../ide/using-the-task-list.md)   
 [Ustawianie zakładek w kodzie](../../ide/setting-bookmarks-in-code.md)   
 [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)