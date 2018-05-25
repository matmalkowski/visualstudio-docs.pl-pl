---
title: Logowanie do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas aliasy użycia | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: Get-Started-Article
description: Logowanie może zakończyć się niepowodzeniem, jeśli są używane aliasy nazwami lub przyjaznymi
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 765862efcd3b83be2d52767dbc81570da2e8f9d6
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Logowanie do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas aliasy użycia

W zależności od typu konta używane do logowania, dostępnych subskrypcji mogą nie być poprawnie wyświetlane po zalogowaniu się do [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Jeden potencjalną przyczyną jest użycie "aliasów" lub "przyjazne nazwy" zamiast tożsamości logowania przypisaniu subskrypcji. Jest to "aliasów". 

## <a name="what-is-aliasing"></a>Co to jest aliasów?

Termin "aliasów" odnosi się do użytkowników o różnych tożsamości, aby zalogować się do systemu Windows (lub usługi Active Directory) i dostęp do poczty e-mail.

Wygładzanie może wystąpić, gdy firma ma usługi Online firmy Microsoft dla swojego katalogu logowania, takie jak JohnD@contoso.com, ale użytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak John.Doe@contoso.com.  Dla wielu klientów, którzy zarządzają subskrypcji, za pośrednictwem wolumin licencjonowania Service Center (VLSC), może to skutkować niepowodzeniem logowania jako adresu e-mail pod warunkiem (John.Doe@contoso.com) jest niezgodna z adresem katalogu (JohnD@contoso.com) wymagany w przypadku pomyślnego uwierzytelnienia za pomocą opcji "Pracy lub konto służbowe".

## <a name="as-an-administrator-what-options-do-i-have"></a>Jako administrator jakie opcje są dostępne?

Jako administrator, dostępne są dwie opcje, aby zapewnić subskrybenci pomyślnego logowania na [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs). 
- Pierwsza opcja (zalecane), ma korzystać z konta katalogu jako przypisanego adresu w wolumin licencjonowania Service Center (VLSC). Zapoznaj się [przypisywanie subskrybentów z kontem katalogu](#assigning-subscribers-to-a-directory-account) w tym artykule, aby uzyskać więcej informacji.
- Druga opcja (mniej bezpieczna opcja), jest umożliwienie subskrybenci skojarzyć swój adres e-mail "Pracy lub szkoły" kontu "Osobiste" () Konta Microsoft lub zarządzanych kont usług). Zapoznaj się [określenie konta firmowego lub szkolnego jako konto osobiste ](#defining-a-work-or-school-account-as-a-personal-account ) w tym artykule, aby uzyskać więcej informacji.

> [!NOTE]
> Po migracji do nowej subskrypcji programu Visual Studio firmy [portalu zarządzania](https://manage.visualstudio.com), będzie można korzystać z nowych czynności administracyjnych, dzięki czemu zarówno katalogu i adresami poczty e-mail mają być dostarczone jako część Profil abonenta.  Dowiedz się więcej o [migracji](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Jako subskrybent jakie opcje są dostępne?

Z punktu widzenia subskrybenta ważne jest pierwszym pracować z administratorem, aby zrozumieć konfigurację tożsamość firmy.  Jeśli to konieczne, administrator może trzeba zaktualizować ustawienia konta z ich portalu administracyjnego lub może być konieczne utworzenie Microsoft konta (MSA) przy użyciu adresu e-mail firmy.  Przed wykonaniem czynności, aby utworzyć konto, skontaktuj się z odpowiednim administratorem w sprawie żadnych zasad lub problemy z wykonaniem tej akcji.  Zapoznaj się [określenie konta firmowego lub szkolnego jako konto osobiste ](#defining-a-work-or-school-account-as-a-personal-account ) w tym artykule, aby uzyskać więcej informacji.  

## <a name="assigning-subscribers-to-a-directory-account"></a>Przypisywanie subskrybentów z kontem katalogu 

We wszystkich przypadkach Menedżer subskrypcji w ramach wolumin licencjonowania Service Center (VLSC) należy użyć adresu katalogu dla nowych subskrybentów lub zaktualizować adres e-mail dla subskrybentów "istniejące".  Należy pamiętać, że przy użyciu adresu katalogu oznacza żadnych nowych subskrybentów nie otrzyma powitalnej wiadomości E-mail, a Administrator będzie musiał powiadomić subskrybenta, które subskrypcji przypisano do nich.  Po wykonaniu następujące czynności, również, Wyślij wiadomość e-mail korzystać [szablonu](#notifying-your-subscribers-with-directory-addresses) subskrybenci, i pomóc w procesie logowania.

### <a name="adding-new-subscribers"></a>Dodawanie nowych subskrybentów
Wykonaj następujące kroki, aby dodać nowy subskrybenta z kontem katalogu.

1. Odwiedź stronę [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (firmy Microsoft VLSC) i zaloguj się.
2. Ze strony administratora VLSC kliknij **subskrypcje** , a następnie **Visual Studio subskrypcje**.

    <img alt="Subscriptions menu" src="_img//vlsc/vlsc-subscriptions.png" style="border: 1px solid #CCCCCC" />

3. Kliknij przycisk **numer umowy** skojarzone z subskrypcją programu Visual Studio.

    <img alt="Select agreement" src="_img/vlsc/vlsc-agreement.png" style="border: 1px solid #CCCCCC" />

4. Kliknij przycisk **przypisać subskrypcji**.

    <img alt="Assign subscription" src="_img/vlsc/vlsc-assign.png" style="border: 1px solid #CCCCCC" />


5. Wybierz żądaną **poziom subskrypcji**.

    <img alt="Subscription level" src="_img/vlsc/vlsc-subscription-level.png" style="border: 1px solid #CCCCCC" /> 

6. Sprawdź poprawność posiadania subskrypcji można przypisać i kliknij **dalej**.
7.  Wprowadź szczegóły subskrybenta i katalogu adres w polu Adres E-mail, a następnie kliknij przycisk **dalej**.

    <img alt="Email address" src="_img/vlsc/vlsc-email-address.png" style="border: 1px solid #CCCCCC" /> 
        
8. Sprawdzanie poprawności informacji dotyczących subskrybenta, a następnie kliknij przycisk **Zakończ**.

9. Powiadom subskrybenta, że zainicjowano swoją subskrypcją przy użyciu poniżej [szablonu](#notifying-your-subscribers-with-directory-addresses).

### <a name="updating-an-existing-subscriber"></a>Aktualizowanie istniejącego abonenta
Wykonaj następujące czynności, aby zaktualizować istniejącego abonenta z kontem katalogu.

1. Odwiedź stronę [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (firmy Microsoft VLSC) i zaloguj się.

2. Ze strony administratora VLSC kliknij **subskrypcji** , a następnie **programu Visual Studio subskrypcji**.

3. Kliknij przycisk **numer umowy** skojarzone z subskrypcją programu Visual Studio.

4. Kliknij przycisk **Strzałka w dół** na pasku wyszukiwania.

5. Wyszukaj za pomocą pola "Adres E-mail".

6. Na liście wyników kliknij **nazwisko** subskrybenta.

7. Kliknij przycisk **Edytuj**.

8. Zmień wartość pola Adres E-mail na adres żądanego katalogu, a następnie kliknij przycisk **zapisać**.

9. Powiadom subskrybenta, że zainicjowano swoją subskrypcją przy użyciu poniżej szablon wiadomości e-mail.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Powiadamianie subskrybenci z adresami katalogu
Ponieważ powitalnej wiadomości E-mail nie zostanie pomyślnie osiągnąć Twojej subskrybenta, skopiuj i Wklej poniżej wiadomości do poczty e-mail i Wyślij z subskrybentem. Zastąp WORD % odpowiednich informacji dotyczących poszczególnych subskrybentów.

---Kopiowania poniżej (Ctrl + C)---

Witaj % SUBSKRYBENTA NAME %

Przypisane subskrypcji programu Visual Studio.  Odwiedź stronę https://my.visualstudio.comi zaloguj się przy użyciu adresu % adres katalogu % aktywować i dostępu do Twojej subskrypcji. 

Jeśli masz problemy, skontaktuj się z zespołem pomocy technicznej (https://www.visualstudio.com/subscriptions/support/).

W dolnej części strony wybierz jedną z poniższych:
   - Konta, subskrypcje i obsługę rozliczeń
   - Problem Wybierz subskrypcję, zaloguj się w pomocy technicznej
   - Wybierz odpowiedni kraj
   - Wybierz odpowiednią opcję asystowaną pomocą techniczną

---Koniec kopiowania---



## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Określenie konta firmowego lub szkolnego jako konta osobistego 
Należy korzystać z instrukcji przedstawionych w temacie [przypisywanie subskrybentów z kontem katalogu](#assigning-subscribers-to-a-directory-account) sekcji, aby dodać nowego użytkownika lub zaktualizować adres e-mail użytkownika w ramach wolumin licencjonowania Service Center (VLSC).  W przypadku których adres e-mail nie został rozpoznany przez katalog użytkownik będzie musiał kroków procesu, aby utworzyć nowe konto, aby zdefiniować adres e-mail jako konta osobistego.  Dla krótkoterminowej zespołu Visual Studio subskrypcji ma zabezpieczone wyjątek od zasad tożsamości określonych poniżej, ale możemy inwestują w możliwości należy usunąć te zasady.

> [!WARNING]
> Firma Microsoft zaleca łączenie tożsamości "Pracy lub szkoły" z "Osobiste" tożsamości.  Ta akcja powoduje utraty własności i kontroli konta organizacji, a pracownik mogą w dalszym ciągu dostęp do określonych produktów lub usług, nawet po opuszczających firmę.  Odwołaj to [wpis w blogu](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/), od zespołu Microsoft Identity, aby uzyskać dodatkowe informacje.

### <a name="defining-an-email-address-as-a-personal-account"></a>Określenie adresu e-mail jako konta osobistego
Po przypisaniu subskrypcji z subskrybentem, otrzymają wiadomość e-mail z prośbą ich do https://my.visualstudio.com Aby skorzystać z zalet ich subskrypcji.  Podczas próby logowania, logowanie subskrypcja programu Visual Studio zakończy się niepowodzeniem z o błędzie informujący, że konto nie został rozpoznany.  Przed logowanie do https://my.visualstudio.com występują, poproś subskrybentom wykonaj te instrukcje.  Jeśli to konieczne, możesz użyć tej funkcji [szablonu](#notifying-your-subscribers-using-personal-accounts) do powiadamiania Twojego subskrybenta po przypisaniu subskrypcji.

1. Przejdź do https://my.visualstudio.comi kliknij przycisk **Utwórz nowe konto Microsoft**.

2. Wypełnij pola:
    - Wprowadź adres e-mail, która odebrała powitalnej wiadomości E-mail w Someone@example.com pole
    - Można utworzyć hasło
    - Wybierz ustawienia promocyjna
    - Kliknij przycisk **dalej**

3. Wykonaj kroki weryfikacji, a następnie kliknij przycisk **dalej**.

4. Nowych użytkowników może być konieczne przeprowadzenie profilu programu Visual Studio.

5. Teraz powinny być widoczne w subskrypcji i korzyści.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Subskrybenci przy użyciu kont osobistych powiadamiania

W powyższym scenariuszu sieci subskrybenta będą otrzymywać "powitalnej wiadomości E-mail", ale z powodu aliasów mogą znaleźć się, że nie mogą logować się.  Można użyć poniżej tekst do powiadamiania Twojego subskrybenta powyższych kroków i zalecane opcje pomocy technicznej, jeśli jest to wymagane.  Zastąp WORD % odpowiednich informacji dotyczących poszczególnych subskrybentów.

---Kopiowania poniżej (Ctrl + C)---

Witaj % SUBSKRYBENTA NAME %

Przypisano subskrypcji programu Visual Studio i może przekierowanie do zalogowania się do https://my.visualstudio.com oparte na powitalną.  Jest to poprawny witryny sieci Web służący do konsumowania korzyści, naszej organizacji wymaga podjęcia odpowiednich jest kilka dodatkowych czynności w celu uzyskania dostępu do witryny.  Wykonaj poniżej informacje ułatwiające tworzenie "Account Microsoft", który jest powiązany z naszych adres firmowej poczty e-mail.  Po wykonaniu tych kroków użyje adresu e-mail można korzystać z zalet subskrypcji.
1. Odwiedź stronę https://my.visualstudio.com

2. Kliknij przycisk Utwórz nowe Account Microsoft po prawej stronie

3. Wypełnij formularz: 
    - Użyj adresu firmowej poczty e-mail w someone@example.com pole
    - Wprowadź hasło
    - Wybierz preferencje promocyjna
    - Kliknij przycisk Dalej

4. Wykonaj kroki weryfikacji konta

5. W razie potrzeby wypełnij profil Visual Studio

6. Powinien zostać wyświetlony swoje korzyści

Uwaga: Podczas odwiedzania https://my.visualstudio.com w przyszłości może pojawić się prośba wybierz konto, które chcesz użyć (np. "Konto służbowe" lub "Osobiste konto").  Po wykonaniu powyższych czynności, należy skorzystać z opcji "Osobiste konto".

Jeśli masz problemy, skontaktuj się z zespołem pomocy technicznej (https://www.visualstudio.com/subscriptions/support/).

W dolnej części strony wybierz jedną z poniższych:
   - Konta, subskrypcje i obsługę rozliczeń
   - Problem Wybierz subskrypcję, zaloguj się w pomocy technicznej
   - Wybierz odpowiedni kraj
   - Wybierz odpowiednią opcję asystowaną pomocą techniczną

---Koniec kopiowania---