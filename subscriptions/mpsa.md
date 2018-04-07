---
title: Subskrypcji programu Visual Studio w produktach firmy Microsoft i umowy o świadczenie usług (MPSA) | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: Get-Started-Article
description: Subskrypcji programu Visual Studio w produktach firmy Microsoft i umowy o świadczenie usług (MPSA)
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a18565a97c0cd85ce42109961592a57c490d92a1
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Visual Studio subskrypcje w Microsoft Products i umowy usług (MPSA)

Jeśli program Visual Studio subskrypcje zostały zakupione w ramach programu MPSA, istnieje kilka rzeczy, aby zwrócić uwagę przed może stać się administratorem subskrypcji programu Visual Studio i przypisać do użytkowników subskrypcji. Jeśli użytkownik ma już został skonfigurowany jako administrator, a następnie można przejść bezpośrednio do subskrypcji programu Visual Studio [portalu administracyjnego](https://manage.visualstudio.com/). 

Jako klient MPSA zostaną wprowadzone do portalu, w którym można zarządzać zakupionymi za pośrednictwem MPSA zasobów. Ten nowy portal jest nazywany [Centrum biznesowych](https://businessaccount.microsoft.com/), który obsługuje niektóre z tych samych i nowe funkcje podobnie jak usługi licencjonowania zbiorowego Center (VLSC). Należą do przeglądania sieci podsumowanie licencji, pliki do pobrania, klucze, użytkowników, itp. Jednak subskrypcji programu Visual Studio w MPSA zachowują się podobnie jak usługi w chmurze. Centrum biznesowych również używa konta służbowego do logowania zamiast Accounts firmy Microsoft. Jeśli Twoja organizacja korzysta z usługi w chmurze, takich jak usługi Office 365 lub Azure Active Directory, a Twój adres e-mail jest częścią żadnego z tych dwóch usług następnie jest już konto służbowe. Pozwoli to można zarejestrować się w Centrum biznesowych przy użyciu istniejącego hasła, który organizacji wyznaczonych do Ciebie. Jeśli organizacja nie korzysta z usługi w chmurze, poczty e-mail nie jest konto służbowe w ogóle nie martw się jako może być ona wykorzystana do zarejestrowania do Centrum biznesowych.

Ponadto subskrypcji programu Visual Studio [portalu administracyjnego](https://manage.visualstudio.com/) jest, gdzie subskrypcji zostanie przypisana do subskrybentów po staje się administratorem programu Visual Studio. W MPSA subskrypcji programu Visual Studio musi być przygotowana do jego portalu zarządzania odpowiednich, czyli portalu administracyjnego subskrypcji programu Visual Studio. W tym celu należy skojarzyć konto zakupu do dzierżawy (np. contoso.onmicrosoft.com). 

Należy pamiętać, że istnieją dwa typy dzierżaw (zarządzanego dzierżawcy i niezarządzanej dzierżawy). Zarządzanego dzierżawcy odwołuje się do dzierżawy, który jest już zarządzany przez administratorów w organizacji. 

Niezarządzanej dzierżawy jest dzierżawy bez żadnych uprawnień administratorów i nie jest używany w usługach Online, takich jak Office 365. Niezarządzane dzierżaw są również tworzone podczas rejestrowania do Centrum firm za pomocą wiadomości e-mail, który nie jest konto służbowe. Jeśli zostały pytanie, aby utworzyć hasło podczas rejestrowania do centrum danych biznesowych, następnie oznacza to, że Twój adres e-mail nie jest konto służbowe i utworzony niezarządzanej dzierżawy.

Przed Kończenie skojarzenie dzierżawcy poniżej przedstawiono kilka wymagań/czynności, aby stać się administratorem subskrypcji usługi Visual Studio.

## <a name="pre-tenant-association-managed-tenant"></a>Skojarzenie wstępne dzierżawy (zarządzanego dzierżawcy)
-   Musi być zarejestrowany użytkownik do Centrum biznesowych.
-   W ramach dzierżawy, które są częścią musi być użytkownika administratora (minimum) lub administratora globalnego. (Dotyczy to jeśli firma korzysta już z usługi w chmurze). Każda rola jest wymagana do administratora subskrypcji programu Visual Studio.
-   Musi być administratorem globalnym w dzierżawie, które są częścią aby można było skojarzyć konto zakupów dla Twojej dzierżawy.
-   Musisz być administratorem konta lub menedżerem w Centrum biznesowych.
-   "Kraju lub regionie" pola w profilu użytkownika (i innych użytkowników) w [Azure](https://portal.azure.com/) musi być wypełnione odpowiednio w zależności od regionu (tj. USA urzędu certyfikacji, itp.). 

> [!NOTE]
> Użytkownicy, którzy mają być Administratorzy subskrypcji programu Visual Studio nie są wymagane do użytkowników w centrum danych biznesowych, potrzebują do spełniania w kroku 2 i 5.

Gdy spełniono kryteria w powyższych krokach 5 można przejść do skojarzenia konta zakupu dzierżawcy poniższe kroki.
1.  Zaloguj się do [Centrum biznesowych](https://businessaccount.microsoft.com/).
2.  Polecenie **konta** kartę i wybierz polecenie **kojarzenie domen**.
3.  Wybierz użytkownika **zakupu konta** (Jeśli masz więcej niż jeden).
4.  Wybierz użytkownika **dzierżawy** (np. contoso.onmicrosoft.com).
5.  Kliknij przycisk **skojarzenia domeny**.

Po dokonaniu skojarzenia wszystkich użytkowników, które spełniają kryteria wymagane będzie zazwyczaj ustanowić jako administratorzy subskrypcji programu Visual Studio w ciągu minut. Jednak czasami może potrwać do 24 godzin. Po udostępnieniem można uzyskać dostępu do portalu administracyjnego subskrypcji programu Visual Studio. Jeśli to trwa dłużej niż 24 godziny, skontaktuj się z pomocą techniczną MPSA.

> [!NOTE]
> W przypadku nowych użytkowników, które spełniają kryteria w kroku 2 i 5 (po skojarzeniu) musi się z pomocą techniczną MPSA. Obsługa MPSA będzie zapewniać pomoc do obsługi administracyjnej nowych administratorów subskrypcji usługi Visual Studio.

## <a name="tenant-association-unmanaged"></a>Skojarzenie dzierżawcy (niezarządzany)

Jeśli został zarejestrowany do Centrum firm za pomocą wiadomości e-mail, który nie był konta służbowego (nie zarejestrowano w usłudze Azure Active Directory "Azure AD"), jak wyjaśniono w akapitu powyższych pięciu skojarzenie dzierżawcy mogą być nieco inne. Należy wykonać, co jest określana mianem "przejęcia domeny". W trakcie tego procesu można utworzyć samodzielnie Administrator globalny, co spowoduje zmianę dzierżawy z niezarządzanych w zarządzanych.

Aby uzyskać bardziej szczegółowy opis dla tego procesu, można użyć [Szybki Start prowadzi](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Pobierz Podręcznik o nazwie *"Instalatora i użyj Your usług Online"* który poprowadzi Cię przez przejęcia domeny. Po zakończeniu zakupu konta zostanie również skojarzony z dzierżawą.

> [!NOTE]
> Po zakończeniu procesu przejęcia domeny trzeba spełnić kryteria z pięciu czynności opisane w sekcji dla wstępnie skojarzenia dzierżawy (zarządzany). Po spełnieniu kryteriów tylko należy się z pomocą techniczną MPSA do udostępnienia dodatkowych administratorów subskrypcji programu Visual Studio.

Jeśli wymagają pomocy lub masz pytania, mogą się z pomocą techniczną za pośrednictwem telefonu lub poczty e-mail.

Obsługa MPSA: **1-866-200-9611**, dostępne poniedziałek — piątek 5:30:00 do 5:30 będzie czas pacyficzny

Adres e-mail: ngvlsup@microsoft.com
