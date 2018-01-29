---
Title: Assign licenses to Visual Studio Subscriptions | Microsoft Docs
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how administrators can assign licenses to subscribers
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: b82f02b968398d0a8d1ce4872ce00e8447a2ae4d
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Przypisywanie licencji w portalu administratora subskrypcji programu Visual Studio

## <a name="assigning-a-single-user"></a>Przypisywanie jednego użytkownika
Jeśli masz dostępnych licencji dla subskrypcji programu Visual Studio, można przypisać do nowych użytkowników na ich ich zalety subskrypcji dostęp do tych licencji. 
1.  Aby przypisać jeden subskrybent Visual Studio, w górnej części tabeli, kliknij przycisk **Dodaj**.

    ![Dodaj subskrybenta](_img\assign-license-add\assign-license-add.png)

2.  Wprowadź informacje do pól formularza dla nowych subskrybentów. Jeśli organizacja korzysta z usługi Azure Active Directory, w tym polu działa jako funkcja wyszukiwania: wyszukiwanie osób w bieżącym katalogu, można wybrać użytkownika w wynikach wyszukiwania. Po wybraniu tej osoby ich nazw, logowania poczty e-mail i powiadomienie e-mail zostaną wypełnione automatycznie zgodnie z poniższą. 

Jeśli Twoja organizacja ma inny adres e-mail do odbierania wiadomości e-mail niż używanego do logowania, istnieje możliwość wprowadzania go tutaj. Wybierz hiperłącze, które wskazuje "Inny adres e-mail dla komunikacji niż logowania?". 

Jeśli chcesz, aby ten subskrybent ma nieprawidłowy plików do pobrania oprogramowania podczas logowania się do [Portal subskrypcji w usłudze Visual Studio](https:/my.visualstudio.com?wt.mc_id=o~msft~docs), upewnij się, że jest zaznaczone pole pliki do pobrania. Jeśli wybierzesz zaznaczenie tego pola wyboru, użytkownik nie ma dostępu do plików do pobrania oprogramowania, ale nadal będzie miał dostęp do wszystkich innych korzyści zawarte w subskrypcji. Gdy wszystko będzie gotowe, kliknij przycisk **Dodaj**.

   ![Wprowadź informacje abonenta](_img\assign-license-add\add-subscriber-1.png)

   ![Wprowadź informacje abonenta](_img\assign-license-add\add-subscriber-2.png)

3.  Po dodaniu subskrybenta, wiadomości E-mail przypisania będą automatycznie wysyłane do nowych subskrybentów z dalszymi instrukcjami. Możesz wysłać wiadomości E-mail przypisania w dowolnym momencie ponownie zaznaczając subskrybenta i klikając przycisk **Wyślij ponownie** przycisk w menu u góry.

    ![Subskrybent dodane](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Przydziały zbiorcze
1.  Aby dodać jednocześnie wiele subskrybentów, przejdź do karty subskrybentów. Na Wstążce u góry kliknij **Dodawanie zbiorcze**. 

    ![Dodawanie zbiorcze](_img\assign-license-add\bulk-assign-add.png)

2. Przypisz masowo używa szablonu programu Microsoft Excel można przekazać subskrybentów. W oknie dialogowym przekazać wielu subskrybentów, kliknij przycisk **Pobierz** można pobrać szablonu. Zawsze należy pobrać najnowszą wersję tego szablonu. Jeśli używasz starszej wersji zbiorczego przekazania może zakończyć się niepowodzeniem.

    ![Przekaż wielu subskrybentów](_img\assign-license-add\bulk-assign-upload.png)

3.  W arkuszu kalkulacyjnym programu Excel Wypełnij pola o informacje dla użytkowników indywidualnych, które chcesz przypisać subskrypcje. Odwołanie pole jest opcjonalne. Jeśli wypełniony dowolnej części szablonu nieprawidłowo, powinien zostać wyświetlony komunikat o błędzie opisujący problem. Zapisz plik na dysku twardym, jeśli zostaną wykonane.
**W celu zapewnienia sprawnego przekazywania, należy stosować poniższe najlepsze rozwiązania:**
    - Upewnij się, że żadne z pól formularza zawierać przecinków.
    - Usuwaj odstępy przed i po pól formularza, takich jak nazwy użytkowników.
    - Upewnij się, że nie zawierają dodatkowe spacje między nazwami pierwszego lub ostatniego dwuczęściowej nazwy użytkowników (np. dwuczęściową imię, takie jak "Może Maggie" należy nie wpisać jako "Może Maggie", ponieważ system nie będzie ograniczać dodatkowe miejsce)

   ![Zbiorcze Dodawanie szablonu](_img\assign-license-add\bulk-template.png)

4.  Powrócić do portalu Visual Studio subskrypcje administracyjnej i w oknie dialogowym przekazać wielu subskrybentów, kliknij przycisk **Przeglądaj**. Przejdź do pliku programu Excel został zapisany i kliknij **OK**. Na ekranie pojawi się postępu przekazywania. 

    ![Dodawanie zbiorcze przekazywania](_img\assign-license-add\bulk-assign-upload-2.png)

Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem i zostaną wyświetlone błędy można więc Popraw szablon i próbę przekazania zbiorczego.

   ![Przekazywanie błędów](_img\assign-license-add\bulk-assign-upload-fail.png)

Po pomyślnym zakończeniu operacji przekazywania, zobaczysz listę subskrybentów i komunikat potwierdzenia.

   ![Przesyłanie zakończone](_img\assign-license-add\bulk-assign-upload-complete.png)