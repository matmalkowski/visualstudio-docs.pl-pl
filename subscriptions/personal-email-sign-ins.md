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
ms.openlocfilehash: a9b0e02acd0c362759997938cec91983a5d48547
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335723"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio subskrypcje w — dlaczego widzę Hotmail lub Gmail adresów dla moich subskrybentów? 

Jak firm migracji z wolumin licencjonowania Service Center (VLSC) do nowego programu Visual Studio [portalu administracyjnego subskrypcje](https://manage.visualstudio.com), Administratorzy mogą być zaskoczeniem się okazać, że "Logowania adres E-mail" dla niektórych subskrybentów Pokazuje 3rd strony adres e-mail, takich jak Hotmail, Gmail lub Yahoo.  Aby uzyskać więcej informacji, zapoznaj się z [ten film](https://www.youtube.com/watch?v=1op-i1zEMfY&t=0s&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=6).

## <a name="cause"></a>Przyczyna

W tym scenariuszu występuje z powodu procesów logowania, które zostały skojarzone z starszy interfejs subskrybenta MSDN. Użytkownicy, zostały poddane migracji z woluminu licencji usługi Center (VLSC) do nowego portalu bez modyfikacji. Administratorzy mogą nie zostać pamiętać, że użytkownicy ma zostały Otwieranie za pomocą konta osobiste ich zalety subskrypcji. Przed migracje subskrybent Visual Studio, które zostały ukończone w 2016 r., wystąpiły dwie akcje wymagane, aby pomyślnie korzystać z subskrypcji programu Visual Studio:
1. Administrator "przypisane" subskrypcji do poszczególnych subskrybentów, przy użyciu ich pracy lub nauki adres e-mail.
2. Subskrybent "aktywować" subskrypcji.

W procesie aktywacji subskrybenta: wymagany do logowania konta Microsoft A (MSA). Jeśli subskrybenta nie nawiązania swoje konto służbowe (np. tasha@contoso.com) jako zarządzanych kont usług, ich można utworzyć nowego zarządzanych kont usług lub korzystać z jednego z istniejących. Wynikiem "Logowania adresu E-mail" jest inna niż "Przypisana do adresu E-mail".

> [!NOTE] 
> Nowe środowisko subskrybenta na [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) obsługuje zarówno pracy/szkoły, jak i konto Microsoft (MAA) typów tożsamości.

Na koniec od czasu migracji administrator trwa danych z centrum VLSC dotyczących subskrybenta "logowania adres E-mail" do wypełnienia nową funkcjonalność zarządzania subskrybenta, ostatnio migrowanych Administratorzy mogą Zobacz te wcześniej niezauważalnie konta osobiste, ze względu na zmiany interfejsu użytkownika, które wyświetlić te informacje.

## <a name="solution"></a>Rozwiązanie

Aby rozwiązać ten problem, należy edytować subskrybenta informacje do zaktualizowania ich adresów e-mail logowania.  Mogą być wprowadzone dla poszczególnych subskrybentów lub grupowo. Aby uzyskać pełne informacje, odwiedź stronę [edytować subskrypcję](edit-license.md).  

Po zaktualizowaniu subscriber(s) adresy e-mail można powiadamiać użytkowników, zmienił ich informacji logowania.  Również otrzymają wiadomość e-mail z zaktualizowane informacje.   