---
title: Tożsamości dla subskrybentów programu Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Tożsamości dla subskrybentów programu Visual Studio

Podczas aktywowania subskrypcji programu Visual Studio, możemy link tożsamości (lub logowania) używanego podczas aktywacji za pomocą subskrypcji programu Visual Studio. Dzięki temu firma Microsoft może Cię rozpoznać na [portal subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), VSTS i na platformie Azure.

W VSTS możemy Sprawdź stan subskrypcji programu Visual Studio możesz zalogować się w każdym i poproś o udzielenie funkcji automatycznie w ramach każdego konta, w którym użytkownik jest członkiem. Ponieważ te funkcje są dołączone jako korzyści subskrybenta, jest także dodać jako element członkowski dowolnego konta usługi VSTS przy użyciu tożsamości, który jest połączony z subskrypcją programu Visual Studio.

Na platformie Azure możemy Sprawdź stan subskrypcji programu Visual Studio podczas aktywowania Twojego [miesięczne środki Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) czyli korzyści subskrybenta.

W ramach [portal subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), można dodać **alternatywny tożsamości**— oprócz tożsamości używanej podczas aktywacji. Dzisiaj mamy umożliwiają dodać tożsamość alternatywnego, jeśli używasz konta Microsoft, aby aktywować subskrypcję. Ten sposób można także dodać służbowego lub konto służbowe (który jest używany podczas logowania do programu Visual Studio, usługi Office 365 lub sieci firmowej firmy lub szkoły), co umożliwia dostęp do programu VSTS, używając konta osobistego i konta firmowego lub szkolnego.

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Jak dodać alternatywne tożsamości do subskrypcji programu Visual Studio

1. Zaloguj się do [portal subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

  > Jeśli użytkownik jest proszony o wybierz "Konto osobiste" lub "konto służbowe", "Konto osobiste" (konta Microsoft).
  >
  > Czasami trzeba wybrać, ponieważ konto Microsoft i konto służbowe udostępnianie tego samego adresu e-mail. Mimo że oba tożsamości używają tego samego adresu e-mail, są one nadal oddzielne tożsamości z różnych profilów, ustawienia zabezpieczeń i uprawnienia.
  >
  > Uruchamianie 30 marca 2018 nie można utworzyć konto Microsoft, za pomocą poczty e-mail, który używa domeny, która jest zarządzana w usłudze Azure Active Directory. Możesz nadal logować się za pomocą tej wiadomości e-mail jako konta służbowego.

2. Przejdź do **subskrypcje** kartę.

  ![Wybierz subskrypcje](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. W obszarze **łączy pokrewnych**, przejdź do **Dodawanie alternatywnego konta**.

  ![W obszarze łączy pokrewnych przejdź do Dodawanie alternatywnego konta](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. Wprowadź konto służbowe i wybierz **Dodaj**.

  ![Wprowadź konto służbowe](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Użyj konta firmowego lub szkolnego logować się do swojego konta usługi VSTS (```https://{youraccount}.visualstudio.com```). Może to być niewielkie opóźnienie informacji propagację, więc spróbuj ponownie 15 minut. 

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>Pytanie: Dlaczego nie VSTS rozpoznaje mnie jako subskrybent Visual Studio?
A: VSTS powinien automatycznie rozpoznać subskrypcji podczas logowania przy użyciu tożsamości głównego lub alternatywnego. Jeśli nie, możesz spróbować kilka rzeczy:

* Sprawdź, czy masz aktywnych subskrypcji programu Visual Studio który [obejmuje VSTS jako świadczenie](vs-vsts.md).

* Upewnij się, że używasz logowania/tożsamości, która jest albo tożsamości głównego lub alternatywnego dla Twojej subskrypcji programu Visual Studio.

* Odwiedź stronę [portal subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) co najmniej raz przed logowania do usługi VSTS.

Jeśli nadal VSTS nie rozpoznaje subskrypcji, [się z pomocą techniczną](https://www.visualstudio.com/team-services/support/)

