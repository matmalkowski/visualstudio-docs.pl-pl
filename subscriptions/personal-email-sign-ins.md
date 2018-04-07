---
title: Osobiste wiadomości E-mail wyświetlany w centrum VLSC
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: Get-Started-Article
description: Subskrypcji programu Visual Studio — dlaczego widzę Hotmail lub adresy usługi Gmail dla moich subskrybentów?
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: cfe035d82976e3df683f4e3a35bd9d7f3c8cf9e2
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Subskrypcji programu Visual Studio — dlaczego widzę Hotmail lub Gmail adresów dla moich subskrybentów? 

Jak firm migracji z wolumin licencjonowania Service Center (VLSC) do nowego programu Visual Studio [portalu administracyjnego subskrypcje](https://manage.visualstudio.com), Administratorzy mogą być zaskoczeniem się okazać, że "Logowania adres E-mail" dla niektórych subskrybentów Pokazuje 3rd strony adres e-mail, takich jak Hotmail, Gmail lub Yahoo.

## <a name="cause"></a>Przyczyna

W tym scenariuszu występuje z powodu procesów logowania, które zostały skojarzone z msDN starszej wersji środowiska subskrybenta. Użytkownicy zostały poddane migracji z centrum VLSC do nowego portalu bez modyfikacji. W przypadku niektórych administratorów mogła zostać wie, że użytkownicy ma zostały Otwieranie za pomocą konta osobiste ich zalety subskrypcji. Przed migracje subskrybent Visual Studio, które zostały ukończone w 2016 r., wystąpiły dwie akcje wymagane, aby pomyślnie korzystać z subskrypcji programu Visual Studio:
1. Administrator "przypisane" subskrypcji do poszczególnych subskrybentów, przy użyciu ich pracy lub nauki adres e-mail.
2. Subskrybent "aktywować" subskrypcji.

W procesie aktywacji subskrybenta: A konta Microsoft (msA) było wymagane do logowania. Jeśli subskrybenta nie nawiązania swoje konto służbowe (np. John@contoso.com) jako zarządzanych kont usług, ich można utworzyć nowego zarządzanych kont usług lub korzystać z jednego z istniejących. Wynikiem "Logowania adresu E-mail" jest inna niż "Przypisana do adresu E-mail".

> [!NOTE] 
> Nowe środowisko subskrybenta na [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) obsługuje zarówno pracy/szkoły, jak i typów tożsamości Account Microsoft (msA).

Na koniec od czasu migracji administrator trwa danych z centrum VLSC dotyczących subskrybenta "logowania adres E-mail" do wypełnienia nową funkcjonalność zarządzania subskrybenta, ostatnio migrowanych Administratorzy mogą Zobacz te wcześniej niezauważalnie konta osobiste, ze względu na zmiany do interfejsu użytkownika, które wyświetlić te informacje.

## <a name="solution"></a>Rozwiązanie

Aby rozwiązać ten problem, należy edytować subskrybenta informacje do zaktualizowania ich adresów e-mail logowania.  Mogą być wprowadzone dla poszczególnych subskrybentów lub grupowo. Aby uzyskać pełne informacje, odwiedź stronę [edytować subskrypcję](/visualstudio/subscriptions/edit-license).  

Po zaktualizowaniu subscriber(s) adresy e-mail można powiadamiać użytkowników, zmienił ich informacji logowania.  