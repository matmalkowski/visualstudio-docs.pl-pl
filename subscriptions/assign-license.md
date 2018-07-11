---
title: Przypisywanie licencji do subskrypcji programu Visual Studio | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do subskrybentów
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: d0dbd509d60ed3528186e41c98f374ab6db60fa3
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "36327027"
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Przypisywanie licencji w portalu administratora subskrypcji programu Visual Studio

Jako administratora subskrypcji programu Visual Studio z portalu administratora subskrypcji programu Visual Studio służy do przypisywania subskrypcji do poszczególnych użytkowników.  
Możesz przypisać pojedynczo lub użyj funkcji "Dodaj zbiorczo", aby przekazać listę subskrybentów z informacjami o subskrypcji, szybkie i łatwe. 

## <a name="assigning-a-single-user"></a>Przypisywanie pojedynczego użytkownika
Jeśli masz dostępnych licencji dla subskrypcji programu Visual Studio, możesz przypisać licencje do nowych użytkowników do nich uzyskiwać dostęp do swoich korzyści z subskrypcji. 
1.  Zaloguj się do [portal administratora](https://manage.visualstudio.com)

2.  Aby przypisać pojedynczego subskrybenta programu Visual Studio, w górnej części tej tabeli, kliknij przycisk **Dodaj**.
   
3.  Wprowadź informacje w polach formularza dla nowych subskrybentów. Jeśli Twoja organizacja używa usługi Azure Active Directory, w tym polu działa jako funkcja wyszukiwania można znaleźć osób w bieżącym katalogu, dzięki czemu można wybrać właściwy użytkownik z wyników wyszukiwania. Po wybraniu tej osobie, ich nazwy, zaloguj się poczty e-mail i powiadomienie e-mail zostaną wypełnione automatycznie jak widać poniżej. 

    Jeśli Twoja organizacja nie korzysta z usługi Azure Active Directory (Azure AD), ale ma inny adres e-mail do odbierania wiadomości e-mail niż ten, który ma być używany do logowania, istnieje możliwość wprowadzania go tutaj. Wybierz hiperłącze etykietą "Dodaj inny adres e-mail do odbierania komunikacji". 

    **Dostęp do plików do pobrania:**  
    Jeśli chcesz, aby mieć dostępu do plików do pobrania oprogramowania, po zalogowaniu się do tego subskrybenta [portalu subskrypcji programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), upewnij się, że pozostawisz przełącznik pliki do pobrania, włączone. Jeśli chcesz wyłączyć pliki do pobrania, użytkownik nie ma dostępu do plików do pobrania oprogramowania, ale będą nadal mieć dostęp do wszystkich innych korzyści objętych subskrypcją. 
    
    Po zakończeniu wybierania opcji dla tego subskrybenta, kliknij przycisk **Dodaj**.

    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-1.png" style="border: 1px solid #CCCCCC" />
    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-2.png" style="border: 1px solid #CCCCCC" />

4.  Po dodaniu subskrybenta, wiadomość e-mail dotycząca przypisania będzie automatycznie przesyłane nowy abonent z dalszymi instrukcjami. Możesz wysłać wiadomość e-mail dotycząca przypisania w dowolnym momencie ponownie, wybierając subskrybenta i klikając **Wyślij ponownie** przycisku w menu u góry.


## <a name="bulk-assignments"></a>Zbiorcze przypisania
1.  Aby dodać jednocześnie wielu subskrybentów, przejdź do **Zarządzanie subskrybentów** kartę. Na Wstążce u góry kliknij **zbiorcze Dodawanie**. 

2. Przypisz zbiorczo używa szablonu programu Microsoft Excel, można przekazać subskrybentów. W oknie dialogowym Przekaż wielu subskrybentów kliknij **Pobierz** pobrać szablon. Zawsze należy pobrać najnowszą wersję tego szablonu. Jeśli używasz starszej wersji, przekazywanie zbiorcze może zakończyć się niepowodzeniem.

3.  W arkuszu kalkulacyjnym programu Excel Wypełnij pola informacjami dla użytkowników indywidualnych, którą chcesz przypisać subskrypcje. Odwołanie pole jest opcjonalne. Jeśli wypełnienie dowolnej części szablonu niepoprawnie, powinien zobaczysz komunikat o błędzie opisujący problem. Zapisz plik lokalnie po zakończeniu.
**Aby zapewnić bezproblemowe przekazywania, należy stosować poniższe najlepsze rozwiązania:**
    - Upewnij się, że żadne pole formularza będzie zawierać przecinków.
    - Usuwaj odstępy przed i po nim pola formularza, takie jak nazwy użytkowników.
    - Upewnij się, nazwy użytkowników nie zawierają dodatkowe spacje między nazwami legalną dwuczęściową pierwszy lub ostatni (np. imię legalną dwuczęściową, takie jak "Może być użytkownikami są Maggie" powinna nie wpisać jako "Może być użytkownikami są Maggie", ponieważ system nie będzie ograniczać dodatkowe miejsce.)

4.  Wróć do portalu administratora subskrypcji programu Visual Studio i w oknie dialogowym Przekaż wielu subskrybentów, kliknij przycisk **Przeglądaj**. Przejdź do pliku programu Excel został zapisany, a następnie kliknij przycisk **OK**. Postęp przekazywania zobaczą na ekranie. 

    <img alt="Bulk add upload" src="_img\assign-license-add\bulk-assign-upload-2.png" style="border: 1px solid #CCCCCC" />

Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem i zostaną wyświetlone błędy można więc Popraw szablon i przekazywania masowego próbę.
    <img alt="Upload fail" src="_img\assign-license-add\bulk-assign-upload-fail.png" style="border: 1px solid #CCCCCC" />

Jeśli przekazywanie zakończy się pomyślnie, zobaczysz listę subskrybentów i komunikat z potwierdzeniem.

