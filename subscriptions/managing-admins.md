---
title: "Zarządzanie prawami administratora w portalu administratora subskrypcji programu Visual Studio"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/19/2018
Ms.topic: Get-Started-Article
Description: Learn how manage admins & super admins in the Visual Studio Subscriptions Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 83bf27d5aaa99c2095ad8a1fafd7541df90f316b
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="managing-administrator-rights-in-the-visual-studio-subscriptions-administrator-portal"></a>Zarządzanie prawami administratora w portalu administratora subskrypcji programu Visual Studio

## <a name="overview"></a>Omówienie 
W programie Visual Studio subskrypcje administratora portalu (https://manage.visualstudio.com) istnieją dwie role związane z zarządzaniem:

**Administratorzy super:** po skonfigurowaniu organizacji, podstawowej lub skontaktuj się z powiadomienia staje się administratorem super domyślnie. Skontaktuj się z podstawowej lub powiadomienia można przypisać dodatkowych administratorów super lub Administratorzy. Oprócz Zarządzanie subskrypcjami dla poszczególnych subskrybentów, Administratorzy super można dodawać i usuwać innych administratorów i administratorów super. Jeśli istnieje więcej niż dwóch Administratorzy super w systemie, superadministrator umożliwia usunięcie wszystkich ostatnie dwa zabezpieczeń. 

**Administratorzy:** może zarządzać administrator subskrybentów w umowach, które super Administrator przypisuje do nich.  Ich przypisać subskrypcji do osób, Edytuj subskrypcji i ponownie przypisać albo usuń je.   (Administratorzy są wyznaczone przez administratorów Super).  

## <a name="adding-an-administrator-with-super-admin-rights"></a>Dodawanie administratora **z** Superadministrator prawa:

1. Zaloguj się do subskrypcji programu Visual Studio [portalu administratora](https://manage.visualstudio.com) przy użyciu konta, które już ma prawa administratora super.

2. Polecenie **administratorom zarządzanie** kartę w górnej części strony. (Tylko Super Administratorzy mają dostęp do tej karty.  Administratorzy bez użycia prawa superadministrator **Zarządzanie subskrybentów** kartę do obsługi poszczególnych subskrybentów.)

3. Kliknij przycisk **Dodaj** do utworzenia nowego administratora. 

4. Wypełnij wszystkie żądane szczegóły w oknie podręcznym Dodawanie administratora.
  - Jeśli Twoja organizacja ma już zarejestrowany w usłudze Azure Active Directory (AAD), rozpocznij wpisywanie nazwy w **nazwa** pola, a następnie zaznacz odpowiedni element na liście rozwijanej. Dodanie nowych użytkowników, wpisz pełną nazwę i Ignoruj *Brak znaleziono tożsamości* powiadomień.
  - Po zidentyfikowaniu odpowiednich użytkowników pole logowania adres E-mail zostanie wypełnione automatycznie. Wpisz adres e-mail administratora nowe, jeżeli nie został dostarczony.

5. Wybierz **PCN** chcesz nowy administrator, aby zarządzać, klikając na liście rozwijanej w obszarze **umowy**. Jeśli PCN są dołączania ma więcej niż jedną umowę na jego podstawie, musisz podać administrator z dostępem do dowolnego lub wszystkich umów. 

**Więcej informacji na temat umów:** funkcji listy rozwijanej w obszarze umów jest wyłączona, gdy tylko jedna umowa jest dostępna.  Po udzieleniu uprawnień administratora Super użytkownika, którego jest konfigurowana automatycznie sprawdzane są wszystkie umowy.

6. Kliknij przycisk **Super Admin** pole, aby włączyć prawa superadministrator tego administratora.  

7. Aby zakończyć dodawanie tego administratora, kliknij przycisk **Dodaj**.

**Potencjalny błąd podczas dodawania administratorów:** niektórych użytkowników może zostać wyświetlony komunikat o błędzie podczas próby dodania administrator. To może nastąpić, jeśli adres e-mail administratora super, który jest dodawany nie znajduje się w usłudze AAD firmy. Aby zakończyć dodawanie nowego administratora, po prostu zignorować błąd i kliknij przycisk **Dodaj** ponownie. 

8. Po utworzeniu superadministrator będą widoczne na liście Administratorzy i swojego konta, które będą oznaczone znakiem zielony znacznik wyboru, aby wskazać ich stan superadministrator. 

### <a name="optional--add-a-different-notification-email"></a>Opcjonalnie: Dodaj wiadomość e-mail z powiadomieniem inny.
Jeśli Twoja organizacja ma inny adres / konta do odbierania wiadomości e-mail, masz teraz opcję, aby wprowadzić adres "Komunikacji". Wybierz **Dodaj wiadomość e-mail z powiadomieniem różnych do odbierania komunikacji**. 

*Przykład:* używa Rene rene@contoso.com , gdy osoba zaloguje się przy użyciu swoich poświadczeń firmowych.  Jednak w Rene firmy tylko używa tego adresu do zarządzania dostęp do katalogu.  Podczas wysyłania i odbierania wiadomości e-mail, używa Rene rene.collado@contoso.com, więc jego Superadministrator przeszedł drugi adres, aby upewnić się, otrzyma powitalnej wiadomości.  Jeśli firma nie jest skonfigurowany w taki sposób, po prostu wprowadzania adresu E-mail logowania powinno wystarczyć.

## <a name="adding-an-administrator-without-super-admin-rights"></a>Dodawanie administratora **bez** Superadministrator prawa:

Ten sam proces zgodnie z powyższym opisem, należy wykonać w celu dodania administratorów bez uprawnień administratora Super, ale biorąc pod uwagę następujące aspekty:
-  Podczas dodawania administratorów bez uprawnień administratora Super, nie jest konieczne w adresie e-mail dodatkowych ma zostać dodana, a pole wyboru Superadministrator pozostanie puste.
-  Użytkownicy bez uprawnień administratora Super nie mają ikonę Sprawdź zielony w jej profilu wpis konfiguracyjny w obszarze "Zarządzaj Administratorzy".
