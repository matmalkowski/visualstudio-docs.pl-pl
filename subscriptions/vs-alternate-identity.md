---
title: Tożsamości dla subskrybentów programu Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Jak dodać alternatywne tożsamości dla Twojej subskrypcji programu Visual Studio dla programu VSTS i na platformie Azure
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 9a83f78f35b9533c554c81cecd181c00eca05568
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Tożsamości dla subskrybentów programu Visual Studio

Podczas aktywowania subskrypcji programu Visual Studio, możemy link tożsamości (lub logowania) używanego podczas aktywacji za pomocą subskrypcji programu Visual Studio. Dzięki temu firma Microsoft może Cię rozpoznać na [portal subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)w Visual Studio Team Services (VSTS) i na platformie Azure.

W VSTS możemy Sprawdź stan subskrypcji programu Visual Studio możesz zalogować się w każdym i poproś o udzielenie funkcji automatycznie w ramach każdego konta, w którym użytkownik jest członkiem.
Ponieważ te funkcje są dołączone jako korzyści subskrybenta, jest także dodać jako element członkowski dowolnego konta usługi VSTS przy użyciu tożsamości, który jest połączony z subskrypcją programu Visual Studio.

Na platformie Azure możemy Sprawdź stan subskrypcji programu Visual Studio podczas aktywowania Twojego [miesięczne środki Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) czyli korzyści subskrybenta.

W ramach [portal subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), można dodać **alternatywny tożsamości** — oprócz tożsamości używanej podczas aktywacji. Obecnie możemy umożliwiają dodać tożsamość alternatywnego, jeśli używasz konta Microsoft, aby aktywować subskrypcję. Ten sposób można także dodać służbowego lub konto służbowe (który jest używany podczas logowania do programu Visual Studio, usługi Office 365 lub sieci firmowej firmy lub szkoły), co umożliwia dostęp do programu VSTS, używając konta osobistego i konta firmowego lub szkolnego.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Dodawanie alternatywnego konta do subskrypcji programu Visual Studio

Dodawanie alternatywnego konta do subskrypcji programu Visual Studio pozwala korzystać z zalet subskrypcji, takich jak Visual Studio Team Services (VSTS) i Azure, z inną tożsamość niż ta, która subskrypcja jest przypisana do. W przeszłości ta funkcja była dostępna, tylko wtedy, gdy subskrypcji Visual Studio (VS) została przypisana do konta Microsoft (MSA). Firma Microsoft rozszerzony tę funkcję dla kont służbowych w usłudze Azure Active Directory (Azure AD).

To nie zapewnia kopii subskrypcji na inne konto; tylko zapewnia możliwość dostępu dwie korzyści z konta alternatywne.

Dla wszystkich subskrypcji można dodać "konto służbowe", dzięki czemu można użyć tego konta z swoje korzyści, które wymagają logowania (IDE w VS VSTS i Azure).

### <a name="prerequisites"></a>Wymagania wstępne

* [VSTS projektu administratora kolekcji lub uprawnienia właściciela konta](https://docs.microsoft.com/en-us/vsts/accounts/faq-add-delete-users#find-owner).

* Aby użyć alternatywnego konta, musi zawierać subskrypcji skojarzonych z Twoim kontem, Visual Studio Team Services lub Microsoft Azure.

> [!Note]
> Możesz użyć korzyści z subskrypcji z Identyfikatorem alternatywny jednak Twoja subskrypcja jest nadal skojarzona z Twoim kontem oryginalnego.

### <a name="add-the-alternate-account"></a>Dodawanie alternatywnego konta

1. Zaloguj się do programu Visual Studio przy użyciu konta Microsoft (https://{youraccount}.visualstudio.com).

2. Przejdź do **subskrypcje**.

  ![Dodawanie alternatywnego konta — Przejdź do subskrypcji w wersji programu VS](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Wybierz **Dodawanie alternatywnego konta**.

  ![Wybierz pozycję Dodaj konto alternatywnej ](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Dodaj konto służbowe.

  ![Dodaj konto służbowe](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Logować się do programu Visual Studio (https://{youraccount}.visualstudio.com), należy użyć konta firmowego lub szkolnego.

  ![Użyj konta służbowego](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

  Twoje alternatywne konto jest dodawane do subskrypcji programu Visual Studio, dzięki czemu zarówno tożsamości mogą korzystać z zalet subskrypcji wymagające Zaloguj się przy użyciu alternatywnego konta (IDE programu VSTS i Azure).

Aby uzyskać więcej informacji dotyczących dodawania konta alternatywne, zobacz [Moje Visual Studio — często zadawane pytania](https://www.visualstudio.com/my/myvsfaq#alternate) strony.

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>Pytanie: Dlaczego nie VSTS rozpoznaje mnie jako subskrybent Visual Studio?
A: VSTS powinien automatycznie rozpoznać subskrypcji podczas logowania przy użyciu tożsamości głównego lub alternatywnego. Jeśli nie, możesz spróbować kilka rzeczy:

* Sprawdź, czy masz aktywnych subskrypcji programu Visual Studio który [obejmuje VSTS jako świadczenie](vs-vsts.md).

* Upewnij się, że używasz logowania/tożsamości, która jest albo tożsamości głównego lub alternatywnego dla Twojej subskrypcji programu Visual Studio.

* Odwiedź stronę [portal subskrybenta programu Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) co najmniej raz przed logowania do usługi VSTS.

Jeśli nadal VSTS nie rozpoznaje subskrypcji, [się z pomocą techniczną](https://www.visualstudio.com/team-services/support/)
