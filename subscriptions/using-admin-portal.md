---
title: Korzystanie z portalu administratora | Visual Studio Marketplace
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
mescription: Learn how to manage your organization's Visual Studio subscriptions with the Administrator Portal.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 22351b94923777d5eb1fe40cd2e43e9dc20f2449
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
#  <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Korzystanie z portalu administratora subskrypcji programu Visual Studio

Pamiętać to korzystając z portalu administracyjnego subskrypcji programu Visual Studio:
 
- **Visual Studio subskrypcje są licencjonowane na użytkownika.** Każdy subskrybent móc korzystać z oprogramowania na komputerach odpowiednio do projektowania i testowania. 
- **Przypisanie poziomu tylko jedna subskrypcja dla każdego subskrybenta**, odpowiadające subskrypcji programu Visual Studio zakupionych w Twojej organizacji. Jeśli masz subskrybentów z więcej niż jednego poziomu subskrypcji do nich przypisane edycji ustawień, aby tylko jeden. 
- **Poziom subskrypcji subskrybenta będą muszą zostać zaktualizowane** po uaktualnieniu (po zakupu licencję "wzrostu") lub odnowiony na niższym poziomie subskrypcji. 
- **Nie udostępniaj subskrypcje między subskrybentów.** Subskrypcję należy przypisać do wszystkich użytkowników lub jej część korzyści subskrypcji (oprogramowanie do projektowania i testowania, Microsoft Azure e-learning itp.). 

## <a name="adminstrator-roles"></a>Role administratora

Istnieją dwa różne role, które istnieją w nowej Visual Studio subskrypcje portalu administracyjnego dla klientów usługi licencjonowania zbiorowego. Te role są obecnie jak rola skontaktuj się z podstawowej/powiadomienia i roli menedżera subskrypcje w centrum VLSC. 

**Super Administratorzy:** po skonfigurowaniu organizacji, podstawowej lub skontaktuj się z powiadomienia staje się administratorem super domyślnie. Skontaktuj się z podstawowej lub powiadomienia można przypisać dodatkowych administratorów super lub Administratorzy. Superadministrator można dodawać i usuwać innych administratorów, a także subskrybentów. Jeśli istnieje więcej niż dwóch Administratorzy super w systemie, superadministrator umożliwia usunięcie wszystkich ostatnie dwa zabezpieczeń. 

**Administratorzy:** administrator można skonfigurować tylko przez administratora. Administrator może zarządzać subskrybentów w umowach, które super Administrator przypisuje do nich. 

## <a name="getting-started"></a>Wprowadzenie

Aby można było używać portalu administratora, aby zarządzać subskrypcjami w organizacji, należy najpierw dołączyć organizacji do portalu.  Po zakończeniu dołączania, należy zapoznać się z strony subskrybentów i uzyskać szczegółowe informacje, jak te są znajdziesz narzędzi i informacje potrzebne do wykonywania zadań zarządzania Twojej subskrypcji.  

### <a name="onboarding"></a>Dołączania

Jeśli Twoja organizacja jest gotowy do można dołączać do portalu administracyjnego subskrypcji programu Visual Studio zostanie wysłana wiadomość e-mail do serwera podstawowego i kontakty powiadomienia, zwracając do ukończenia procesu dołączania. Poniżej szczegóły przedstawiono kroki, które należy podjąć dołączyć do nowego portalu. Jeśli chcesz wskazówki procesu wyewidencjonować to [dołączania administratora wideo](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) lub to [artykuł pomocy technicznej](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "programu Visual Studio subskrypcje administratora migracji procesu").   
1.  **Lokalizowanie PCN Twojego i logowania:**
    - W wiadomości e-mail serwer podstawowy i kontakty powiadomienia są dostarczane z łączem unikatowy i ostatnich trzech cyfr z ich publicznego klienta numer (PCN). * 
    - Uzyskanie całego PCN, należy zalogować się w centrum VLSC w głównej osoby kontaktowej (można znaleźć instrukcje dotyczące lokalizacji PCN). 
    - Po uzyskaniu NKP, ich musisz wybierz ich unikatowy łącze, która wyświetli monit o ich do logowania. Będą oni mogli zalogowanie się przy użyciu konta Microsoft (MSA) albo konto robocze/służbowe (Jeśli Twoja organizacja jest w usłudze AAD), jeśli Twoja organizacja nie znajduje się w usłudze AAD. 
    - Następnie muszą wprowadzić NKP. 
2.  **Konfigurowanie Administratorzy w Twojej organizacji.** Po wprowadzeniu NKP, zostanie zarejestrowany jako superadministrator w nowym systemie i będzie można dodać inne super Administratorzy i Administratorzy (wcześniej znane jako menedżerów subskrypcji). Aby zapobiec utracie dostępu, to należy wykonać przed datą migracji w organizacji. 
3.  **Uzyskiwanie dostępu do portalu zarządzania subskrypcji.**  Po migracji organizacji wiadomości e-mail będą wysyłane do nowo dodanego super Administratorzy i Administratorzy, zwracając dostęp do nowego portalu i rozpocząć zarządzanie subskrypcjami.  

> [!NOTE]
> Jeśli serwer podstawowy bądź powiadomienia kontaktów odbierają więcej niż jeden adres e-mail, oznacza to, że PCN więcej niż jeden. Należy ukończyć proces przy użyciu łącza unikatowy dla PCN występujący w odwołaniu w każdym email.*

Jeśli nie masz pewności, kto jest kontakt podstawowy/powiadomienia mają zostać dodane do nowego programu Visual Studio subskrypcje portalu administracyjnego, te informacje po zalogowaniu się można znaleźć [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx). Spójrz na [Znajdź swój głównej osoby kontaktowej](/find-primary-contact/) tematu kroki, aby znaleźć kontakt podstawowy/powiadomienia w w centrum VLSC.
Jeśli użytkownik ma już został skonfigurowany jako administrator, a następnie można przejść bezpośrednio do [portalu administracyjnego subskrypcji programu Visual Studio](https://manage.visualstudio.com).

### <a name="understanding-the-subscribers-page"></a>Opis strony subskrybentów
Po przypisane subskrypcje, na karcie subskrybentów udostępnia szczegółowe informacje na temat subskrybentów, w tym:
- Imię i nazwisko każdy subskrybent.
- Adres e-mail dla tego użytkownika.
- Poziom subskrypcji, który przypisano do nich.
- Data swoją subskrypcję przypisano do nich. 
- Data wygaśnięcia swoją subskrypcję.
- Opcjonalny opis.
- Włączono lub wyłączono wskazaniem, czy do pobrania dla subskrybenta. 
- Kraju, w którym się znajdują.
- Ich preferencje językowe dla przypisania e-mail komunikacji z portalu administracyjnego.
- Pole opcjonalne dla innego adresu e-mail używane do komunikacji niż logowania. 

W lewej części strony można wyświetlić dodatkowe informacje o liczbie zakupionych, przypisane i nadal dostępne w Twojej organizacji, dla każdej umowy licencji subskrypcji.

   ![Strona Subscibers portalu administratora subskrypcji programu Visual Studio](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>Opis strony szczegółów
Aby uzyskać więcej informacji o umowie, że jest wyświetlana wybierz kartę szczegółów. Widoczny jest stan umowy, zakupu konta, szczegóły organizacji, kontaktów podstawowych (VLSC), Administratorzy super (jeśli jest dostępny) i inne istotne informacje.

   ![Strona szczegółów portalu administratora subskrypcji programu Visual Studio](_img/using-admin-portal/details-page.png)

