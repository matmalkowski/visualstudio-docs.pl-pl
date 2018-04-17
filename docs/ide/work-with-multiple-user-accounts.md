---
title: Praca z wieloma kontami użytkowników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-acquisition
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b93a57592ae87daa8d60d5a4d5e7166d26cfe61f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="work-with-multiple-user-accounts"></a>Praca z wieloma kontami użytkowników

Jeśli masz wiele kont Microsoft i/lub konta służbowego, można dodać je wszystkie dla programu Visual Studio, dzięki czemu można dostępu do zasobów na dowolne konto bez konieczności oddzielnie Zaloguj się do niego. Udoskonalone środowisko logowania obsługuje obecnie, usług Azure, usługi Application Insights, Team Foundation Server i usługi Office 365. Dodatkowe usługi mogą stać się dostępne, ponieważ czas przechodzi.

Po dodaniu wiele kont na jednej maszynie zestawu kont będzie mobilny Tobie, jeśli logujesz się do programu Visual Studio na innym komputerze. Należy pamiętać, że chociaż nazwy kont są przekazywane, poświadczenia nie jest. W związku z tym pojawi się monit o podanie poświadczeń dla tych kont innych próba użycia zasobów na nowym komputerze po raz pierwszy.

W tym przewodniku pokazano, jak dodać wiele kont dla programu Visual Studio i jak sprawdzić, czy zasoby dostępne z tych kont są uwzględniane w takich jak umieszcza **dodać podłączonej usługi** okna dialogowego, **Eksploratora serwera** , i **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Zaloguj się do programu Visual Studio

- Zaloguj się do programu Visual Studio z konta Microsoft lub konta organizacyjnego. Powinna zostać wyświetlona nazwa użytkownika są wyświetlane w górnym rogu okna, podobnie do poniższego:

     ![Currentlly zalogowanego użytkownika](../ide/media/vs2015_username.png "VS2015_UserName")

### <a name="access-your-azure-account-in-server-explorer"></a>Dostęp do konta platformy Azure w Eksploratorze serwera

Naciśnij klawisz **Ctrl + Alt + S** otworzyć **Eksploratora serwera**. Wybierz pozycję Azure ikony, jak i kiedy rozszerza możesz powinny być widoczne zasoby dostępne w ramach konta Azure, który jest skojarzony z Identyfikatorem, który był używany podczas logowania do programu Visual Studio. Powinna przypominać następujące wyświetlane (z wyjątkiem tego, że zobaczysz własnych zasobów).

![Węzeł narzędzi Azure przedstawiający Eksploratora serwera rozwinięty](../ide/media/vs2015_serverexplorer.png "VS2015_ServerExplorer")

Po raz pierwszy używasz programu Visual Studio na dowolnym określonym urządzeniu okno dialogowe będzie wyświetlana tylko zarejestrowany pod Identyfikatorem zalogowany do środowiska IDE z subskrypcji. Dostęp do zasobów dla każdego konta bezpośrednio z **Eksploratora serwera** prawym przyciskiem myszy węzeł Azure i wybierając pozycję **zarządzanie i subskrypcje filtru** i dodawanie konta z formant wyboru konta. Można wybrać inne konto, w razie potrzeby, klikając strzałkę w dół i wybierając z listy kont. Po wybraniu konta, możesz subskrypcje, które w ramach tego konta, które chcesz wyświetlić w Eksploratorze serwera.

![Okno dialogowe subskrypcji platformy Azure zarządzanie](../ide/media/vs2015_manage_subs.png "vs2015_manage_subs")

Przy następnym otwarciu Eksploratora serwera, wyświetlane są zasoby dla tej subskrypcji.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Dostęp do konta platformy Azure za pomocą okna dialogowego Dodawanie podłączonej usługi

1. Utwórz projekt aplikacji platformy uniwersalnej systemu Windows w języku C#.

1. Wybierz węzeł projektu w Eksploratorze rozwiązań, a następnie wybierz **Dodaj, połączone usługi**. **Dodać podłączonej usługi** kreatora pojawi się i zawiera listę usług konta platformy Azure, która jest skojarzona z identyfikatorem logowania programu Visual Studio Należy pamiętać, że nie trzeba oddzielnie logowanie do platformy Azure. Jednak należy zalogować się do innych kont podczas pierwszej próby dostępu ich zasobów na danym komputerze.

    > [!WARNING]
    > Jeśli po raz pierwszy tworzysz aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio na określonym komputerze, pojawi się monit Aby włączyć, przechodząc do Twojego urządzenia pod kątem trybu programowanie **ustawienia &#124; aktualizacji i zabezpieczeń &#124; dla deweloperów** na komputer. Aby uzyskać więcej informacji, zobacz [Włącz swoje urządzenia na potrzeby programowania](/windows/uwp/get-started/enable-your-device-for-development).

### <a name="access_azure"></a> Dostęp do usługi Azure Active Directory w projekcie sieci Web

Usługi Azure AD umożliwia obsługę użytkowników końcowych jednej operacji logowania w aplikacji sieci web platformy ASP.NET MVC lub AD uwierzytelniania w usługach interfejsu API sieci Web. Uwierzytelnianie domeny różni się od uwierzytelnienia konta użytkownika; użytkowników, którzy mają dostęp do Twojej domeny usługi Active Directory umożliwia ich istniejących kont usługi Azure AD connect do aplikacji sieci web. Aplikacje pakietu Office 365 można również użyć uwierzytelniania domeny. Aby wyświetlić to działanie, tworzenie aplikacji sieci web (**pliku nowego projektu C#, chmury, aplikacja sieci Web ASP.NET**). W oknie dialogowym Nowy projekt ASP.NET wybierz **Zmień uwierzytelnianie**. Kreator uwierzytelniania zostanie wyświetlona i umożliwia wybranie jakiego rodzaju uwierzytelniania do użycia w aplikacji.

![Zmień dialog uwierzytelniania dla platformy ASP.NET](../ide/media/vs2015_change_authentication.png "VS2015_change_authentication")

Aby uzyskać więcej informacji o różnych rodzajów uwierzytelniania w programie ASP.NET, zobacz [tworzenia projektów sieci Web ASP.NET w programie Visual Studio 2013](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (informacje dotyczące uwierzytelniania jest nadal istotne dla bieżącej wersji programu Visual Studio).

### <a name="access-your-visual-studio-team-services-account"></a>Dostęp do tego konta usługi Visual Studio Team Services

W menu głównym wybierz **zespołu, nawiązywanie połączenia z Team Foundation Server** można wyświetlić **Team Explorer** okna. Polecenie **Wybierz projekty zespołowe**, a następnie w polu listy **wybierz Team Foundation Server**, powinien zostać wyświetlony adres URL konta usługi Visual Studio Team Services. Jeśli wybrany adres URL będziesz się logować bez konieczności ponownego wprowadzania poświadczeń.

## <a name="add-a-second-user-account-to-visual-studio"></a>Dodawanie drugiego konta użytkownika dla programu Visual Studio

Kliknij strzałkę w dół obok swojej nazwy użytkownika w górnym rogu programu Visual Studio. Następnie wybierz pozycję **ustawienia konta** elementu menu. **Menedżerem** okna dialogowego zostanie wyświetlony i podpisany przy użyciu konta. Wybierz **Dodaj konto** łącze w dolnym rogu okna dialogowego, aby dodać nowego konta Microsoft lub nowe konta firmowego lub szkolnego.

![Wybór konta usługi Visual Studio](../ide/media/vs2015_acct_picker.png "VS2015_acct_picker")

Postępuj zgodnie z monitami, aby wprowadź nowe poświadczenia konta. Na poniższej ilustracji przedstawiono Menedżera konta, po użytkownik został dodany swojego konta służbowego Contoso.com.

![Menedżerem](../ide/media/vs2015_accountmanager.gif "VS2015_AccountManager")

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Ponownie Dodaj kreatora podłączonych usług i Eksploratora serwera

Teraz przejdź do **Eksploratora serwera** ponownie, kliknij prawym przyciskiem myszy w węźle Azure i wybierz polecenie **zarządzania i filtr subskrypcji**. Wybierz nowe konto, klikając strzałkę listy rozwijanej obok bieżącego konta, a następnie wybierz pozycję subskrypcje, które chcesz wyświetlić w Eksploratorze serwera. Powinny zostać wyświetlone wszystkie usługi skojarzone z określoną subskrypcję. Mimo że nie aktualnie zalogowano Cię do środowiska IDE programu Visual Studio z drugiego konta, użytkownik jest zalogowany do tego konta usług i zasobów. Dotyczy to także **projektu, dodać podłączonej usługi** i **zespołu, nawiązywanie połączenia z Team Foundation Server**.

## <a name="see-also"></a>Zobacz także

[Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
