---
title: 'Porady: odpowiadanie na debugera Just In Time | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cec8887ddf2023a8abd08f409b93f47efdc7001
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155571"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Porady: odpowiadanie na debugera Just In Time

Działania należy podjąć, gdy pojawi się Just-in-Time okno dialogowe debuger zależą od tego, co chcesz zrobić:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Jeśli chcesz naprawić lub debugowania błędu (użytkowników programu Visual Studio)

- Konieczne jest posiadanie [zainstalowanego programu Visual Studio](http://visualstudio.microsoft.com) Aby wyświetlić szczegółowe informacje o błędzie i spróbuj go debugować. Aby uzyskać więcej informacji, zobacz [debugowania za pomocą debugera just in Time](../debugger/debug-using-the-just-in-time-debugger.md). Jeśli nie można naprawić błąd i napraw aplikację, skontaktuj się z właścicielem aplikacji, aby rozwiązać problem.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Jeśli chcesz zapobiec pojawianiu się okno dialogowe debuger just in Time

Możesz wykonać kroki, aby zapobiec Just-in-Time okno dialogowe debuger pojawianiu się. Jeśli aplikacja obsłuży błąd, możesz uruchomić tę aplikację normalnie.

1. (Aplikacje sieci web) Jeśli próbujesz uruchomić aplikację sieci web, można wyłączyć debugowanie skryptu.

    Dla programu Internet Explorer lub Microsoft Edge Wyłącz debugowanie skryptu w oknie dialogowym Opcje internetowe. Możesz uzyskać dostęp tych ustawień w **Panelu sterowania** > **sieć i Internet** > **Opcje internetowe** (konkretne kroki zależą od użytkownika wersja systemu Windows i przeglądarki).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Następnie ponownie otworzyć stronę sieci web, gdzie znaleźć błąd. Jeśli zmiana tego ustawienia nie rozwiąże problemu, skontaktuj się z właścicielem aplikacji sieci web, aby rozwiązać ten problem.

3. (Użytkownicy programu visual Studio) Jeśli masz zainstalowany program Visual Studio (lub jeśli był zainstalowany wcześniej i usunął ją), [Wyłącz Just-in-Time debugging](../debugger/debug-using-the-just-in-time-debugger.md) , a następnie spróbuj ponownie uruchomić aplikację.

    > [!IMPORTANT]
    > Jeśli wyłączysz Just-in-Time debugowania i aplikacja napotkał nieobsługiwany wyjątek (błąd), zostanie wyświetlona okno dialogowe błędu standardowego zamiast tego lub aplikacji spowoduje awarię lub zawieszenie. Aplikacja nie będzie działać normalnie do czasu naprawienia błędu (przez użytkownika lub właściciela aplikacji).

2. (ASP.NET i IIS) Jeśli hostujesz aplikację sieci Web platformy ASP.NET w usługach IIS, należy wyłączyć debugowanie po stronie serwera.

    W Menedżerze usług IIS, kliknij prawym przyciskiem myszy węzeł serwera i wybierz polecenie **Przełącz do widoku funkcji**. W sekcji platformy ASP.NET, wybierz **kompilacja platformy .NET** i upewnij się, możesz wybrać **False** jako zachowanie debugowania (kroki różnią się w starszych wersjach usług IIS).

## <a name="see-also"></a>Zobacz też
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
