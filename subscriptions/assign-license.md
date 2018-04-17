---
title: Przypisywanie licencji do subskrypcji usługi Visual Studio | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do subskrybentów
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 62336656e551a085c6c8753e6baea06730f49510
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Przypisywanie licencji w portalu administratora subskrypcji programu Visual Studio

Jako administrator subskrypcji programu Visual Studio można użyć portalu administratora programu Visual Studio subskrypcji można przypisać subskrypcji dla poszczególnych użytkowników.  
Można przypisać pojedynczo lub użyj funkcji "Dodaj zbiorczo", aby przekazać listy subskrybentów z informacjami o swoich subskrypcji, szybkie i łatwe. 

## <a name="assigning-a-single-user"></a>Przypisywanie jednego użytkownika
Jeśli masz dostępnych licencji dla subskrypcji programu Visual Studio, można przypisać do nowych użytkowników na ich ich zalety subskrypcji dostęp do tych licencji. 
1.  Zaloguj się do [portal administratora](https://manage.visualstudio.com)

2.  Aby przypisać jeden subskrybent Visual Studio, w górnej części tabeli, kliknij przycisk **Dodaj**.

    ![Dodaj subskrybenta](_img\assign-license-add\assign-license-add.png)

3.  Wprowadź informacje do pól formularza dla nowych subskrybentów. Jeśli organizacja korzysta z usługi Azure Active Directory, w tym polu działa jako funkcja wyszukiwania: wyszukiwanie osób w bieżącym katalogu, można wybrać użytkownika w wynikach wyszukiwania. Po wybraniu tej osoby ich nazw, logowania poczty e-mail i powiadomienie e-mail zostaną wypełnione automatycznie zgodnie z poniższą. 

    Jeśli Twoja organizacja ma inny adres e-mail do odbierania wiadomości e-mail niż używanego do logowania, istnieje możliwość wprowadzania go tutaj. Wybierz hiperłącze, które wskazuje "Inny adres e-mail dla komunikacji niż logowania?". 

    **Dostęp do plików do pobrania:**  
    Jeśli chcesz, aby ten subskrybent ma nieprawidłowy plików do pobrania oprogramowania podczas logowania się do [Portal subskrypcji w usłudze Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), upewnij się, że jest zaznaczone pole pliki do pobrania. Jeśli wybierzesz zaznaczenie tego pola wyboru, użytkownik nie ma dostępu do plików do pobrania oprogramowania, ale nadal będzie miał dostęp do wszystkich innych korzyści zawarte w subskrypcji. 
    
    Po zakończeniu wybierania opcji dla tego subskrybenta, kliknij przycisk **Dodaj**.

    ![Wprowadź informacje abonenta](_img\assign-license-add\add-subscriber-1.png)
    ![wprowadź informacje abonenta](_img\assign-license-add\add-subscriber-2.png)

4.  Po dodaniu subskrybenta, wiadomości E-mail przypisania będą automatycznie wysyłane do nowych subskrybentów z dalszymi instrukcjami. Możesz wysłać wiadomości E-mail przypisania w dowolnym momencie ponownie zaznaczając subskrybenta i klikając przycisk **Wyślij ponownie** przycisk w menu u góry.

    ![Subskrybent dodane](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Przydziały zbiorcze
1.  Aby dodać jednocześnie wiele subskrybentów, przejdź do **subskrybentów** kartę. Na Wstążce u góry kliknij **Dodawanie zbiorcze**. 

    ![Dodawanie zbiorcze](_img\assign-license-add\bulk-assign-add.png)

2. Przypisz masowo używa szablonu programu Microsoft Excel można przekazać subskrybentów. W oknie dialogowym przekazać wielu subskrybentów, kliknij przycisk **Pobierz** można pobrać szablonu. Zawsze należy pobrać najnowszą wersję tego szablonu. Jeśli używasz starszej wersji zbiorczego przekazania może zakończyć się niepowodzeniem.

    ![Przekaż wielu subskrybentów](_img\assign-license-add\bulk-assign-upload.png)

3.  W arkuszu kalkulacyjnym programu Excel Wypełnij pola o informacje dla użytkowników indywidualnych, które chcesz przypisać subskrypcje. Odwołanie pole jest opcjonalne. Jeśli wypełniony dowolnej części szablonu nieprawidłowo, powinien zostać wyświetlony komunikat o błędzie opisujący problem. Zapisz plik na dysku twardym, jeśli zostaną wykonane.
**W celu zapewnienia sprawnego przekazywania, należy stosować poniższe najlepsze rozwiązania:**
    - Upewnij się, że żadne z pól formularza zawierać przecinków.
    - Usuwaj odstępy przed i po pól formularza, takich jak nazwy użytkowników.
    - Upewnij się, że nie zawierają dodatkowe spacje między nazwami pierwszego lub ostatniego dwuczęściowej nazwy użytkowników (np. dwuczęściową imię, takie jak "Może Maggie" należy nie wpisać jako "Może Maggie", ponieważ system nie będzie ograniczać dodatkowe miejsce) ![zbiorcze Dodawanie szablonu](_img\assign-license-add\bulk-template.png)

4.  Powrócić do portalu Visual Studio subskrypcje administracyjnej i w oknie dialogowym przekazać wielu subskrybentów, kliknij przycisk **Przeglądaj**. Przejdź do pliku programu Excel został zapisany i kliknij **OK**. Na ekranie pojawi się postępu przekazywania. 

    ![Dodawanie zbiorcze przekazywania](_img\assign-license-add\bulk-assign-upload-2.png)

Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem i zostaną wyświetlone błędy można więc Popraw szablon i próbę przekazania zbiorczego.

   ![Przekazywanie błędów](_img\assign-license-add\bulk-assign-upload-fail.png)

Po pomyślnym zakończeniu operacji przekazywania, zobaczysz listę subskrybentów i komunikat potwierdzenia.

   ![Przesyłanie zakończone](_img\assign-license-add\bulk-assign-upload-complete.png)