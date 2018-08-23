---
title: Użyj narzędzia WhiteSource Bolt korzyści | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/11/2017
ms.topic: Get-Started-Article
description: Dowiedz się, jak aktywować subskrypcję WhiteSource Bolt zawartych w ramach subskrypcji programu Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4c1039018eb745c7a04c6269b4b98e737461f7c
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42624142"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>Użyj narzędzia WhiteSource Bolt w subskrypcji programu Visual Studio

Znajdowanie i eliminowanie luk w zabezpieczeniach typu open source oraz generowanie kompleksowych raportów spisu i licencji wszystkich składników typu open source w kompilacji. Niektóre subskrypcje programu Visual Studio obejmują sześć miesięcy bezpłatnego dostępu.

## <a name="activation-steps"></a>Procedurę aktywacji

1.  Aby aktywować swoje korzyści WhiteSource Bolt, zaloguj się do [ https://my.visualstudio.com/benefits ](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) .

2.  Znajdź Kafelek WhiteSource Bolt w sekcji narzędzia, a następnie kliknij **uzyskać kod** link w dolnej części kafelka korzyści.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource korzyści kafelka](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Otrzymasz powiadomienie o wyświetlaniu kodu aktywacji.  **Skopiuj kod do Schowka**, następnie kliknij przycisk **Aktywuj**.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource korzyści kodu ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Na stronie sieci web WhiteSource kliknij **Aktywuj** przycisk lub przewiń w dół do **aktywować konta** części strony.
    > [!div class="mx-imgBorder"]
    > ![Aktywuj korzyść WhiteSource](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  W **aktywować konta** sekcji strony poprowadzą Cię przez cztery kroki:

    - [Zainstaluj](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) rozszerzenia WhiteSource Bolt z programu Microsoft Visual Studio marketplace. Jeśli nie masz uprawnienia do instalowania rozszerzeń, zobacz [zainstalować bezpłatne rozszerzenia usługi VSTS](/vsts/marketplace/install-vsts-extension?view=vsts).

    Kliknij zielony **zainstalować** przycisk, jeśli używasz usługi VSTS, lub **Pobierz** przycisk programu Team Foundation Server.  W tym przykładzie używamy usługi VSTS.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource korzyści instalowanie rozszerzeń](_img\vs-whitesource\vs-whitesource-download-install.png)

    - Następnie wybierz konto usługi VSTS, którego chcesz użyć, a następnie kliknij przycisk **Potwierdź**.  (Jeśli usługi VSTS nie zostały jeszcze skonfigurowany, odwiedź stronę [korzyści](https://my.visualstudio.com/benefits) strony i aktywować swoje korzyści z usługi VSTS.)
    > [!div class="mx-imgBorder"]
    > ![WhiteSource korzyści Potwierdź konto](_img\vs-whitesource\vs-whitesource-confirm-account.png)

    - Otrzymasz potwierdzenie, że rozszerzenie jest zainstalowane i gotowe do użycia.  Kliknij przycisk **wprowadzenie** wróć do strony WhiteSource Bolt i kontynuować.
    > [!div class="mx-imgBorder"]
    > ![Ukończono instalację WhiteSource korzyści](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Otwórz pulpit nawigacyjny projektu programu Visual Studio Team Services (VSTS), kliknij pozycję **kompilowanie i wydawanie** menu i wybrać **WhiteSource Bolt**.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource korzyści Dodaj rozszerzenie](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Wklej kod aktywacji za pomocą kafelka korzyści WhiteSource Bolt, a następnie kliknij przycisk **Aktywuj**. Każdy z kolejnych kodów aktywacji można aktywować tylko jeden projekt.
    > [!div class="mx-imgBorder"]
    > ![Aktywować korzyści WhiteSource](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  Proces aktywacji jest teraz gotowy i będzie mieć 180 dni pozostałych w ramach Twojej subskrypcji.

8.  Należy dodać rozszerzenie WhiteSource Bolt jako jeden z kroków kompilacji.  Film wideo jest dostępna w [strony WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) aby pokazać, jak.

9. Po uruchomieniu kompilacji, następujące kompleksowych raportów i pulpitów nawigacyjnych będą automatycznie generowane:
    - Pulpit nawigacyjny luk w zabezpieczeniach
    - Raport o luk w zabezpieczeniach
    - Przestarzałe biblioteki raportów
    - Pulpit nawigacyjny ryzyka i zgodności licencji
    - Raport o spisie

## <a name="eligibility"></a>Uprawnienie

| Poziom subskrypcji                                                 |     Kanały                                            | Korzyść                                                          | Podlega odnowieniu?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Program Visual Studio Enterprise (standardowy, roczna w chmurze)   | Licencjonowania zbiorowego, Azure, w sprzedaży detalicznej, wybrane NFR<sup>1</sup> | 6 miesięcy       |  Tak          |
| Program Visual Studio Professional (standardowy, roczna w chmurze) | VL, Azure, Retail                                       | Nie jest dostępna                                                           |NAZWA         |
| Visual Studio Test Professional (standardowa)                         | Licencjonowania zbiorowego, handlu detalicznego                                              | Niedostępne                                             |  NAZWA         |
| Platformy MSDN (standardowa)                                          | Licencjonowania zbiorowego, handlu detalicznego                                              | Niedostępne                                              | NAZWA         |
| Visual Studio Dev Essentials | NAZWA  | Niedostępne |NAZWA |
| Program Visual Studio Enterprise, Visual Studio Professional (miesięcznych w chmurze) | Azure                                       | Niedostępne                                                           |NAZWA|

<sup>1</sup>*obejmuje: sieci Microsoft Partner Network (przedsiębiorstwo).    Nie obejmuje: Inne Not for Resale (NFR), Visual Studio Industry Partner (VSIP), ekwiwalentu pełnego wymiaru czasu, MCT Software & deweloperów usług, BizSpark, Imagine, cenionym partnera firmy Microsoft (MVP), dyrektor Region (usług pulpitu zdalnego), MCT Software & Services, Microsoft Partner Network () Professional).*

Nie masz pewności której subskrypcji używasz?  Połączyć się z [ https://my.visualstudio.com/subscriptions ](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) Aby wyświetlić wszystkie subskrypcje, które są przypisane do Twojego adresu e-mail. Jeśli nie widzisz wszystkie swoje subskrypcje, mogą mieć co najmniej jeden przypisany do innego adresu e-mail.  Musisz zalogować się przy użyciu tego adresu e-mail, aby wyświetlić te subskrypcje.

## <a name="support-resources"></a>Zasoby pomocy technicznej

-  Potrzebujesz pomocy dotyczącej WhiteSource Bolt?  Porozmawiaj z przedstawicielem WhiteSource Bolt na żywo w https://www.whitesourcesoftware.com/vse_whitesource_bolt/
-  Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, skontaktuj się z pomocą programu Visual Studio [pomoc techniczna dla subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/).
-  Masz pytanie dotyczące środowiska IDE programu Visual Studio, Visual Studio Team Services lub innych produktów Visual Studio lub usług?  Odwiedź stronę [pomoc techniczna dla programu Visual Studio](https://visualstudio.microsoft.com/support/).