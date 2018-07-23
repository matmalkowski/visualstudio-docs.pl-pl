---
title: Praca z wieloma kontami użytkowników
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64e51bd43d278eb681d08b785c2a7d0c9539ee23
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179700"
---
# <a name="work-with-multiple-user-accounts"></a>Praca z wieloma kontami użytkowników

Jeśli masz wiele kont Microsoft i/lub konta służbowego lub szkolnego, można dodać je wszystkie do programu Visual Studio, tak, aby dostęp do zasobów z dowolnego konta bez konieczności logowania się do niego oddzielnie. Obecnie usług platformy Azure, usługa Application Insights, Team Foundation Server i usługi Office 365 obsługują usprawnione środowisko logowania. Dodatkowe usługi może stają się dostępne, gdy czas.

Po dodaniu wielu kont na jednej maszynie, ten zestaw kont "wędrują" z Tobą Jeśli logujesz się do programu Visual Studio na innym komputerze. Należy zauważyć, że chociaż nazwy kont są przekazywane, poświadczenia nie są. W związku z tym można jest monitowany o podanie poświadczeń dla tych innych kont próby użycia zasobów na nowej maszynie po raz pierwszy.

W tym instruktażu przedstawiono sposób dodawania wielu kont w programie Visual Studio, a następnie jak sprawdzić, czy zasoby, które są dostępne z tych kont są odzwierciedlane w umieszcza takich jak **Dodaj podłączoną usługę** okno dialogowe, **Eksploratora serwera** , i **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio

- Zaloguj się do programu Visual Studio za pomocą konta Microsoft lub kontem organizacyjnym. Powinny zostać wyświetlone swoją nazwę użytkownika, które pojawiają się w prawym górnym rogu okna, podobny do następującego:

     ![Currentlly zalogowanego użytkownika](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Dostęp do konta platformy Azure w Eksploratorze serwera

Naciśnij klawisz **Ctrl**+**Alt**+**S** otworzyć **Eksploratora serwera**. Wybierz **Azure** ikonę i po użytkownik rozszerza powinien zostać wyświetlony zasobów dostępnych na koncie platformy Azure, która jest skojarzona z Identyfikatorem, którego użyto do zalogowania się do programu Visual Studio. Będzie widoczny podobny do poniższego (z tą różnicą, że zobaczysz własne zasoby).

![Rozwinięty węzeł narzędzi Azure przedstawiający Eksploratora serwera](../ide/media/vs2015_serverexplorer.png)

Po raz pierwszy używasz programu Visual Studio na dowolnym urządzeniu określonego okna dialogowego zostaną wyświetlone tylko subskrypcje zarejestrowany w identyfikatorze, którego zalogowano się do środowiska IDE, za pomocą. Dostęp do zasobów dla każdego z innych kont, bezpośrednio z **Eksploratora serwera** przez kliknięcie prawym przyciskiem myszy **Azure** węzła i wybierając pozycję **zarządzanie i filtr subskrypcji**i dodawanie kont z formant selektora konta. Następnie możesz wybrać inne konto, jeśli to konieczne, klikając strzałkę w dół, a następnie wybierając z listy kont. Po wybraniu konta, możesz wybrać subskrypcje, które w ramach tego konta, które mają być wyświetlane w **Eksploratora serwera**.

![Zarządzanie subskrypcjami platformy Azure w oknie dialogowym](../ide/media/vs2015_manage_subs.png)

Gdy następnym razem otworzysz **Eksploratora serwera**, wyświetlane są zasoby dla tej subskrypcji.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Dostęp do konta platformy Azure za pomocą okna dialogowego Dodawanie podłączonej usługi

1. Tworzenie projektu aplikacji platformy uniwersalnej systemu Windows w języku C#.

1. Wybierz węzeł projektu w **Eksploratora rozwiązań** , a następnie wybierz **Dodaj** > **podłączoną usługę**. **Dodaj podłączoną usługę** kreatora pojawia się i zostanie wyświetlony na liście usług na koncie platformy Azure, który jest skojarzony z identyfikatora logowania programu Visual Studio Należy pamiętać, że nie trzeba osobno logowanie do platformy Azure. Jednakże należy zalogować się do innych kont spróbujesz uzyskać dostęp do zasobów z danego komputera po raz pierwszy.

    > [!WARNING]
    > Jeśli po raz pierwszy tworzysz aplikację platformy UWP w programie Visual Studio na określonym komputerze, zostanie wyświetlony monit Włącz urządzenie w trybie projektowania, przechodząc do **ustawienia** > **aktualizacje i zabezpieczenia**  >  **Dla deweloperów** na tym komputerze. Aby uzyskać więcej informacji, zobacz [włączyć urządzenia na potrzeby programowania](/windows/uwp/get-started/enable-your-device-for-development).

### <a name="access_azure"></a> Dostęp do usługi Azure Active Directory w projekcie sieci Web

Usługa Azure AD umożliwia obsługę użytkownika końcowego logowania jednokrotnego w aplikacjach sieci web platformy ASP.NET MVC lub uwierzytelniania AD w usługach interfejsu API sieci web. Uwierzytelnianie domeny różni się od uwierzytelniania konta użytkownika; Użytkownicy, którzy mają dostęp do domeny usługi Active Directory można użyć istniejących kont usługi Azure AD, połączyć się z aplikacji sieci web. Aplikacje usługi Office 365 można również użyć uwierzytelniania przez domenę. Aby to zobaczyć w działaniu, tworzenie aplikacji sieci web (**pliku** > **nowy projekt** > **C#** > **chmury**  >  **Aplikacji sieci Web ASP.NET**). W **nowy projekt ASP.NET** okno dialogowe, wybierz **Zmień uwierzytelnianie**. Kreatora uwierzytelniania pojawia się i pozwala wybrać rodzaj uwierzytelniania do użycia w aplikacji.

![Okna dialogowego uwierzytelnienia zmiany dla platformy ASP.NET](../ide/media/vs2015_change_authentication.png)

Aby uzyskać więcej informacji na temat różnych rodzajów uwierzytelniania w programie ASP.NET: zobacz [projekty sieci web ASP.NET tworzenie w programie Visual Studio 2013](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (informacje o uwierzytelnianiu jest nadal istotne dla bieżącej wersji programu Visual Studio).

### <a name="access-your-visual-studio-team-services-account"></a>Dostęp do konta programu Visual Studio Team Services

W menu głównym wybierz **zespołu** > **nawiązywanie połączenia z Team Foundation Server** aby przywołać **Team Explorer** okna. Kliknij pozycję **Wybierz projekty zespołowe**, a następnie w polu listy **wybierz Team Foundation Server**, powinien zostać wyświetlony adres URL dla konta usługi Visual Studio Team Services. Po wybraniu adresu URL możesz będą rejestrowane w bez konieczności ponownego wprowadzania poświadczeń.

## <a name="add-a-second-user-account-to-visual-studio"></a>Dodawanie drugiego konta użytkownika w programie Visual Studio

Kliknij strzałkę w dół obok swojej nazwy użytkownika w prawym górnym rogu programu Visual Studio. Następnie wybierz **ustawienia konta** elementu menu. **Menedżerem** okno dialogowe pojawia się i wyświetla konta podczas logowania. Wybierz **Dodaj konto** łącze w dolnym rogu okna dialogowego, aby dodać nowe konto Microsoft lub nowej pracy lub konta służbowego.

![Selektor konta usługi Visual Studio](../ide/media/vs2015_acct_picker.png)

Postępuj zgodnie z monitami, aby wprowadzić nowe poświadczenia konta. Poniższa ilustracja przedstawia **menedżerem** po użytkownik został dodany jego *Contoso.com* konto służbowe.

![Menedżer kont](../ide/media/vs2015_accountmanager.gif)

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Kontroluj, Kreator dodawania usługi połączone i Eksploratora serwera

Teraz przejdź do **Eksploratora serwera** ponownie, kliknij prawym przyciskiem myszy **Azure** węzeł i wybierz polecenie **zarządzanie i Filtruj subskrypcje**. Wybierz nowe konto, klikając strzałkę listy rozwijanej obok bieżącego konta, a następnie wybierz subskrypcje, które mają być wyświetlane w **Eksploratora serwera**. Powinny być widoczne wszystkie usługi, które są skojarzone z określonej subskrypcji. Mimo że nie aktualnie zalogowano Cię do środowiska IDE Visual Studio przy użyciu drugiego konta, zalogowano Cię do tego konta usług i zasobów. Dotyczy to także **projektu** > **Dodaj podłączoną usługę** i **zespołu** > **nawiązywanie połączenia z Team Foundation Server**.

## <a name="see-also"></a>Zobacz także

- [Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
