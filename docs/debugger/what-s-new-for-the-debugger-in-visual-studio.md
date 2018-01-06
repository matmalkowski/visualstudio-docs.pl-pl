---
title: "Nowości w debugerze programu Visual Studio 2017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/07/2016
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
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: "81"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8df1dcde73496f6ec8c25eb33cb4b6986a721f33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Nowości w debugerze programu[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Debuger zawiera następujące nowe funkcje:

- Nowość w 15,5 cala, **debugera migawki** tworzy migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który chcesz. Aby nakazać debugera do tworzenia migawki, należy ustawić snappoints i logpoints w kodzie. Debuger pozwala zobaczyć dokładnie co poszło źle, bez wpływu na ruch aplikacji produkcyjnej. Debuger migawki ułatwiają znacznie skrócić czas potrzebny na rozwiązać problemy występujące w środowisku produkcyjnym.

    Kolekcja migawki jest dostępne dla następujących aplikacji sieci web uruchomionych w usłudze Azure App Service:

    * Aplikacji platformy ASP.NET działających w środowisku .NET Framework 4.6.1 lub nowszej.
    * Aplikacji platformy ASP.NET Core uruchomionych na .NET Core 2.0 lub nowszego systemu Windows.

    Aby uzyskać więcej informacji, zobacz [debugowania na żywo aplikacji ASP.NET, za pomocą debugera migawki](../debugger/debug-live-azure-applications.md).

- Nowość w 15,5 cala w Visual Studio Enterprise, **zwrotnego krok IntelliTrace** automatycznie tworzy migawkę aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawki umożliwiają wróć na poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, ponieważ był w przeszłości. IntelliTrace krok wstecz może zaoszczędzić czas podczas chcesz zobacz poprzedni stan aplikacji, ale nie chcesz uruchomić ponownie debugowania lub Utwórz ponownie stan żądanej aplikacji.

    Można znaleźć i wyświetlić migawki za pomocą **krok do tyłu** i **krok do przodu** przycisków na pasku narzędzi debugowania. Tych przycisków nawigacji zdarzenia, które są widoczne w **zdarzenia** karcie **narzędzia diagnostyczne** okna.

    ![Krok do tyłu i do przodu przyciski](../debugger/media/intellitrace-step-back-icons-description.png  "przyciski krok do tyłu i do przodu")

    Aby uzyskać więcej informacji, zobacz [wyświetlić migawki IntelliTrace krok zwrotnego pomocą](../debugger/how-to-use-intellitrace-step-back.md) strony.

- **Pomocnika wyjątków** zastępuje Asystenta wyjątków i zostanie wyświetlony w oknie dialogowym niemodalne, w którym wystąpił błąd. **Pomocnika wyjątków** zapewnia szybsze uzyskanie dostępu do żadnych wyjątków wewnętrznych, dodatkowe analizy przez debuger (jeśli jest dostępny) i bezpośredniego dostępu do **ustawienia wyjątków** dla wyjątku. Pomocnika wyjątków można również przeciągać przestawne widoku, jeśli blokuje coś, co należy sprawdzić.

    Na przykład **NullReferenceException** pojawi się do zmiennej, która ma wartość null odwołania (dodatkowe informacje).

    ![Pomocnik wyjątków debugera](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Aby uzyskać więcej informacji, zobacz [przy użyciu nowego pomocnika wyjątków w programie Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) wpis w blogu.

- Możesz teraz używać do wiersza kodu podczas wstrzymaniu w debugerze, wybierając **uruchomienia wykonania dotąd** ikona zieloną strzałkę (pojawi się ikona podczas kursora myszy nad wiersz kodu). Eliminuje to potrzebę ustawienia tymczasowych punktów przerwania.

    ![Debuger do uruchomienia kliknij](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- Można ustawić warunki na wyjątki w **ustawienia wyjątków** okno dialogowe (można to zrobić za pomocą **Edytuj warunek** ikonę w oknie dialogowym Ustawienia wyjątków lub za pomocą menu kliknij prawym przyciskiem myszy na wyjątek.) Obecnie obsługiwane warunki obejmować nazwy modułu do dołączania lub wykluczania dla wyjątku.

    ![Warunki po wystąpieniu wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Dołącz do okno dialogowe zawiera nową funkcję wyszukiwania, które mogą ułatwić szybkie identyfikowanie proces, który należy dołączyć do procesu.

    ![Wyszukaj w dołączyć do procesu](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

Aby uzyskać więcej informacji na temat tych nowych funkcji, zobacz [informacje o wersji dla [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)