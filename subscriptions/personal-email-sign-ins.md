---
title: "Osobiste wiadomości E-mail wyświetlany w centrum VLSC"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: "Visual Studio Subscriptions – Why Am I Seeing Hotmail or Gmail Addresses for My Subscribers?"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 2bfe2f39d432be5fc6ff7b24be2a218d02fce961
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Subskrypcji programu Visual Studio — dlaczego widzę Hotmail lub adresy usługi Gmail dla moich subskrybentów? 

Jak firm migracji z wolumin licencjonowania Service Center (VLSC) do nowego programu Visual Studio [portalu administracyjnego subskrypcje](https://manage.visualstudio.com), Administratorzy mogą być zaskoczeniem się okazać, że "Logowania adres E-mail" dla niektórych subskrybentów Pokazuje 3rd strony adres e-mail, takich jak Hotmail, Gmail lub Yahoo.

## <a name="cause"></a>Przyczyna

W tym scenariuszu występuje z powodu procesów logowania, które zostały skojarzone z starszy interfejs subskrybenta MSDN. Użytkownicy zostały poddane migracji z centrum VLSC do nowego portalu bez modyfikacji. W przypadku niektórych administratorów mogła zostać wie, że użytkownicy ma zostały Otwieranie za pomocą konta osobiste ich zalety subskrypcji. Przed migracje subskrybent Visual Studio, które zostały ukończone w 2016 r., wystąpiły dwie akcje wymagane, aby pomyślnie korzystać z subskrypcji programu Visual Studio:
1. Administrator "przypisane" subskrypcji do poszczególnych subskrybentów, przy użyciu ich pracy lub nauki adres e-mail.
2. Subskrybent "aktywować" subskrypcji.

W procesie aktywacji subskrybenta:
1. Konto Microsoft (MSA) było wymagane do logowania.
2. Jeśli subskrybenta nie nawiązania swoje konto służbowe (np. John@contoso.com) jako zarządzanych kont usług, ich można utworzyć nowego zarządzanych kont usług lub korzystać z jednego z istniejących.
3. Wynikiem "Logowania adresu E-mail" jest inna niż "Przypisana do adresu E-mail".

> [!NOTE] 
> Nowe środowisko subskrybenta na [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) obsługuje zarówno pracy/szkoły, jak i konto Microsoft (MSA) typów tożsamości.

Na koniec od czasu migracji administrator trwa danych z centrum VLSC dotyczących subskrybenta "logowania adres E-mail" do wypełnienia nową funkcjonalność zarządzania subskrybenta, ostatnio migrowanych Administratorzy mogą Zobacz te wcześniej niezauważalnie konta osobiste, ze względu na zmiany do interfejsu użytkownika, które wyświetlić te informacje.

## <a name="solution"></a>Rozwiązanie

Aby rozwiązać ten problem, należy edytować subskrybenta informacje do zaktualizowania ich adresów e-mail logowania.  Mogą być wprowadzone dla poszczególnych subskrybentów lub grupowo. Aby uzyskać pełne informacje, odwiedź stronę [edytować subskrypcję](/visualstudio/subscriptions/edit-license).  

Po zaktualizowaniu subscriber(s) adresy e-mail można powiadamiać użytkowników, zmienił ich informacji logowania.  