---
title: 'Porady: odpowiadanie na debuger Just In Time | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c506e12fc8e6637e2b53852587e6a37c57cbf5ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Porady: odpowiadanie na debuger Just In Time

Działania należy podjąć po wyświetleniu Just in Time okno dialogowe debugera zależą od tego, co chcesz zrobić:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Jeśli chcesz naprawić lub Debugowanie błędów (użytkowników programu Visual Studio)

- Musi mieć [zainstalowanego programu Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48146) wyświetlić szczegółowe informacje o błędzie i spróbuj on debugowania. Aby uzyskać więcej informacji, zobacz [debugowania za pomocą debugera just in Time](../debugger/debug-using-the-just-in-time-debugger.md). Jeśli nie można usunąć błąd i napraw aplikację, skontaktuj się z właścicielem aplikacji, aby usunąć błąd.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Jeśli chcesz zapobiec wyświetlaniu okna dialogowego debuger just in Time

Możesz wykonać czynności, aby zapobiec Just in Time wyświetlaniu — okno dialogowe debugera. Jeśli aplikacja obsługuje błąd, aplikację można uruchomić normalnie.

1. (Aplikacje sieci web) Jeśli próbujesz uruchomić aplikacji sieci web, możesz wyłączyć debugowanie skryptu.

    Dla programu Internet Explorer lub Microsoft Edge Wyłącz debugowanie skryptu w oknie dialogowym Opcje internetowe. Można uzyskać dostępu do tych ustawień od **Panelu sterowania** > **sieć i Internet** > **Opcje internetowe** (kroki szczegółowe zależą od użytkownika wersja systemu Windows i przeglądarka).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Następnie ponownie otwórz stronę sieci web, gdzie znaleziono błąd. Jeśli zmiana tego ustawienia nie rozwiąże problemu, skontaktuj się z właścicielem aplikacji sieci web, aby rozwiązać ten problem.

3. (Użytkowników programu visual Studio) Jeśli masz zainstalowanego programu Visual Studio (lub jeśli były zainstalowane wcześniej i usunięto go), [debugowania Just in Time Wyłącz](../debugger/debug-using-the-just-in-time-debugger.md) i spróbuj ponownie uruchomić aplikację.

    > [!IMPORTANT]
    > Jeśli wyłączysz Just in Time debugowania i aplikacja napotka nieobsługiwany wyjątek (błąd), albo zostanie wyświetlone okno dialogowe błędu standardowego zamiast tego lub aplikacji spowoduje awarię lub Rozłącz. Aplikacja nie będzie działać normalnie, dopóki nie zostanie rozwiązany błędu (przez użytkownika lub właściciela aplikacji).

2. (Platformy ASP.NET i IIS) Jeśli przechowujesz aplikacji sieci Web ASP.NET w usługach IIS należy wyłączyć debugowanie po stronie serwera.

    W Menedżerze usług IIS kliknij prawym przyciskiem myszy węzeł serwera i wybierz polecenie **Przełącz do widoku funkcji**. W sekcji platformy ASP.NET, wybierz **kompilacja platformy .NET** i upewnij się, możesz wybrać **False** jako zachowanie debugowania (kroki są różne w starszych wersjach usług IIS).
  
## <a name="see-also"></a>Zobacz też    
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
