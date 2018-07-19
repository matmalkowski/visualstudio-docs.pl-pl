---
title: Przypisywanie licencji do subskrypcji programu Visual Studio | Dokumentacja firmy Microsoft
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 07/16/2018
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do subskrybentów
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e43e9050e2b021025ed4ae104f4345bce6e8eee3
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131934"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Przypisz licencje w portal administratora subskrypcji programu Visual Studio

Jako administratora subskrypcji programu Visual Studio z portalu administratora służy do przypisywania subskrypcji do poszczególnych użytkowników i grup użytkowników.

Dla grup użytkowników, można przypisać subskrypcji do nich jedną w czasie, lub użyj **zbiorcze Dodawanie** funkcję, aby przekazać listę subskrybentów z informacjami o subskrypcji, szybkie i łatwe. 

## <a name="individual-assignments"></a>Poszczególne przypisania

Poniżej przedstawiono sposób przypisać licencję subskrypcji programu Visual Studio, aby do nowego użytkownika, dzięki czemu mogą uzyskiwać dostęp do korzyści z subskrypcji.

1. Zaloguj się do [portal administratora](https://manage.visualstudio.com).

2. Aby przypisać licencję do pojedynczego subskrybenta programu Visual Studio, w górnej części tej tabeli, wybierz pozycję **Dodaj**.

   ![Dodaj pojedynczego subskrybenta](media\add-single-subscriber.png)

3. Wprowadź informacje w polach formularza dla nowych subskrybentów. Jeśli Twoja organizacja używa usługi Azure Active Directory, w tym polu działa jako funkcja wyszukiwania można znaleźć osób w bieżącym katalogu, dzięki czemu można wybrać właściwy użytkownik z wyników wyszukiwania. Po wybraniu tej osobie, ich nazwy, zaloguj się poczty e-mail i powiadomienie e-mail zostaną wypełnione automatycznie. 

   ![Dodaj nowy adres e-mail powiadamiania](media\add-new-subscriber-notification-email.png)

   Jeśli chcesz, aby mieć dostęp do plików do pobrania oprogramowania, po zalogowaniu się do tego subskrybenta [portalu subskrypcji programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), upewnij się, że pozostawisz przełącznik pliki do pobrania, włączone w **ustawienia pobierania** sekcja. Jeśli chcesz wyłączyć pliki do pobrania, użytkownik nie ma dostępu do plików do pobrania oprogramowania, ale będą nadal mieć dostęp do wszystkich innych korzyści objętych subskrypcją.

   ![Dostęp do plików do pobrania](media\access-to-downloads.png)

   Jeśli chcesz zmienić język, w którym subskrybent otrzymuje informacje, możesz zrobić to w **preferencje dotyczące komunikacji** sekcji.

   ![Zmień język do użycia podczas wysyłania wiadomości e-mail z powiadomieniem](media\change-subscriber-communication-preference.png)

   Jeśli chcesz dodać notatki odwołania do subskrypcji, możesz zrobić to w **Dodaj odwołanie do** sekcji.

   ![Dodaj notatki odwołania do każdej subskrypcji](media\add-subscriber-reference-notes.png) 

    Gdy ukończysz pracę wybierając opcje i wprowadzania danych dla subskrybenta, wybierz **Dodaj** w dolnej części **Dodaj subskrybenta** staną się.

   ![Kliknij przycisk Dodaj](media\add-button.png)

4. Po dodaniu subskrybenta, wiadomość e-mail dotycząca przypisania będzie automatycznie wysyłane do nowych subskrybentów z dalszymi instrukcjami. Możesz wysłać wiadomość e-mail dotycząca przypisania w dowolnym momencie ponownie, wybierając subskrybenta i klikając **Wyślij ponownie** przycisku w menu u góry.

   ![Wyślij ponownie wiadomość e-mail dotyczącą aktywacji do żadnego użytkownika lub wielu użytkowników zawsze wtedy, gdy chcesz](media\resend-subscriber-activation-emails.png) 

## <a name="bulk-assignments"></a>Zbiorcze przypisania

1. Aby dodać wielu subskrybentów w tym samym czasie, przejdź do **Zarządzanie subskrybentów** kartę. Na Wstążce u góry kliknij **zbiorcze Dodawanie**.

  ![Dodaj wielu subskrybentów](media\add-multiple-subscribers.png)

1. Przypisz zbiorczo używa szablonu programu Microsoft Excel, można przekazać subskrybentów. W oknie dialogowym Przekaż wielu subskrybentów kliknij **Pobierz** pobrać szablon.

  ![Pobierz szablon programu Excel, aby przesłać wielu subskrybentów](media\download-template-upload-subscribers.png)

  >! [UWAGA] Zawsze należy pobrać najnowszą wersję tego szablonu. Jeśli używasz starszej wersji, przekazywanie zbiorcze może zakończyć się niepowodzeniem.

1. W arkuszu kalkulacyjnym programu Excel Wypełnij pola informacjami dla użytkowników indywidualnych, które chcesz przypisać subskrypcje. (*Odwołania* pole jest opcjonalne.) Zapisz plik lokalnie w przypadku, gdy wszystko będzie gotowe.

  Aby zapewnić bezproblemowe przekazywania, należy stosować poniższe najlepsze rozwiązania:

    - Upewnij się, że żadne pole formularza będzie zawierać przecinków.
    - Usuwaj odstępy przed i po nim pola formularza.
    - Upewnij się, nazwy użytkownika nie zawierają dodatkowe spacje między nazwami legalną dwuczęściową pierwszy lub ostatni (na przykład, jeśli osoba ma dwuczęściowej nazwy pierwszej, takie jak "Może być użytkownikami są Maggie", jego należy wpisać jako "MaggieMay", ponieważ system nie będzie trim dodatkowe miejsce.)

1. Wróć do portalu administratora subskrypcji programu Visual Studio. W **Przekaż wielu subskrybentów** okno dialogowe, kliknij przycisk **Przeglądaj**.

  ![Przejdź do zapisany szablon, aby Przekaż wielu subskrybentów](media\bulk-add-browse-saved-template.png)

1. Przejdź do pliku programu Excel, który został zapisany, a następnie kliknij przycisk **OK**.

  ![Przekaż szablon programu Excel, aby przesłać wielu subskrybentów](media\bulk-upload-subscribers.png)

  Pojawi się okno dialogowe postępu przekazywania.

  Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem, a zostaną wyświetlone błędy, aby użytkownik może poprawić szablonu i ponów próbę przekazywania masowego.

  ![Komunikat o błędzie w przypadku niepowodzenia przekazywania wielu subskrybentów](media\bulk-add-template-failed.png)

  Jeśli przekazywanie zakończy się pomyślnie, zobaczysz listę subskrybentów i komunikat z potwierdzeniem.

  ![Komunikat z potwierdzeniem Jeśli przekazywanie wielu subskrybentów zakończy się powodzeniem.](media\bulk-add-template-success.png)