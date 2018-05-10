---
title: Konfigurowanie repozytorium Podwersją
description: Przy użyciu usługi Git i Podwersją w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: f21106ea020118eb1facef9f7ac64a080015d621
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="setting-up-a-subversion-repository"></a>Konfigurowanie repozytorium Podwersją

Podwersją jest system kontroli wersji scentralizowane. Oznacza to, że ma pojedynczego serwera, który zawiera wszystkie pliki i wersje, z których użytkownicy można wyewidencjonować dowolna wersja dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium Podwersją, użytkownik otrzyma migawkę repozytorium w danym momencie.

Przed rozpoczęciem pracy z Podwersją, narzędzi wiersza polecenia Xcode musi być zainstalowany jako obejmują one poprawne svn pakietów. Możesz sprawdzić, czy SVN został zainstalowany w terminalu przy użyciu następującego polecenia:

`svn h`

1. Utwórz bezpłatne repozytorium SVN w trybie online. Na przykład [Assembla](https://app.assembla.com/) została użyta. Po utworzeniu, należy podać adres URL, który będzie używany do nawiązania połączenia repozytorium: 

    ![Uzyskaj adres URL SVN i skopiuj go](media/version-control-subversion1-sml.png)

2. Otwórz lub Utwórz dla komputerów Mac projektu programu Visual Studio.

3. Kliknij prawym przyciskiem myszy projekt i wybierz **kontrolą wersji > Publikuj w kontroli wersji...** : 

    ![Rozpocząć publikowanie projektu](media/version-control-subversion2.png)

4. W **Połącz z repozytorium** wybierz opcję **Podwersją** z najwyższym listy rozwijanej.

5. Wprowadź adres URL z kroku 1. Powinno to spowodować wypełnienie innych pól domyślnie: 

    ![Wybierz repozytorium i wprowadź szczegóły okna dialogowego](media/version-control-subversion3.png)

7. Kliknij przycisk **OK** , a następnie potwierdź naciskając **publikowania**.

7. Użytkownik może zostać poproszony o podanie poświadczeń dla lokacji, w której jest tworzony repozytorium. Wprowadź te, jak przedstawiono poniżej:

    ![](media/version-control-subversion5.png)

8.  Wszystkie polecenia kontroli wersji dostępna teraz powinny być widoczne w menu kontroli wersji.

