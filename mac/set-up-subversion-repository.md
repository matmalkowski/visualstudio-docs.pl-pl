---
title: Konfigurowanie repozytorium Podwersją
description: Przy użyciu Podwersją w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: e5f395511ad3b2b3cc4568a4d701ca5dbcc02736
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "34000260"
---
# <a name="setting-up-a-subversion-repository"></a>Konfigurowanie repozytorium Podwersją

Podwersją jest scentralizowanego _system kontroli wersji_, co oznacza, że istnieje pojedynczego serwera, który zawiera wszystkie pliki i wersje, z których użytkownicy można wyewidencjonować dowolna wersja dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium Podwersją, użytkownik pobiera migawkę repozytorium w danym momencie.

Aby użyć Podwersją kontroli wersji, musi ona zainstalowana na tym komputerze. Aby sprawdzić, czy Podwersją jest zainstalowany ten komputer, użyj następującego polecenia w terminalu:

```bash
svn --version
```

To polecenie zwraca numer wersji.

Jeśli Podwersją nie jest już zainstalowany, najprościej przygotować jest instalując _narzędzi wiersza polecenia Xcode_. Użyj poniższego polecenia do zainstalowania narzędzia wiersza polecenia Xcode i Podwersją.

```bash
xcode-select --install
```

Po Podwersją jest zainstalowany na tym komputerze, wykonaj następujące kroki, aby opublikować projekt w SVN.

1. Utwórz bezpłatne repozytorium SVN w trybie online. Na przykład [Assembla](https://app.assembla.com/) została użyta. Po utworzeniu, należy podać adres URL, który będzie używany do nawiązania połączenia repozytorium: 

    ![Skopiuj adres URL SVN](media/version-control-subversion1-sml.png)

2. Otwórz lub Utwórz dla komputerów Mac projektu programu Visual Studio.

3. Kliknij prawym przyciskiem myszy projekt i wybierz **kontrolą wersji > Publikuj w kontroli wersji...** : 

    ![Rozpocząć publikowanie projektu](media/version-control-subversion2.png)

4. W **Połącz z repozytorium** wybierz opcję **Podwersją** od góry listy rozwijanej.

5. Wprowadź adres URL z kroku 1. Po wprowadzeniu adresu URL, pozostałe pola są wypełniane domyślnie: 

    ![Wybierz repozytorium i wprowadź szczegóły okna dialogowego](media/version-control-subversion3.png)

7. Kliknij przycisk **OK** , a następnie potwierdź naciskając **publikowania**.

7. Jeśli zostanie wyświetlony monit, wprowadź swoje poświadczenia dla lokacji, w której jest tworzony repozytorium, jak przedstawiono poniżej:

    ![Wprowadzanie poświadczeń podwersją repozytorium](media/version-control-subversion5.png)

8.  Wszystkie polecenia kontroli wersji dostępna teraz powinny być widoczne w menu kontroli wersji.

