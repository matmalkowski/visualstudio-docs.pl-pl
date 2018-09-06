---
title: Zmiana lokalizacji instalacji programu Visual Studio 2017
description: Dowiedz się, jak zmniejszyć rozmiar instalacji na dysku systemowym, zmieniając lokalizację pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8b3ce1b0b0bc646f6a4d28031be51920da776cd
ms.sourcegitcommit: 9ea4b62163ad6be556e088da1e2a355f31366f39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43995910"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Zmiana lokalizacji instalacji programu Visual Studio 2017

**Nowość w wersji 15.7**: może zmniejszyć miejsca zajmowanego przez instalację na dysku systemowym przez przeniesienie pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach.

Poniżej przedstawiono sposób.

1. Po zainstalowaniu programu Visual Studio, wybierz **opcje instalacji** kartę.

  ![Program Visual Studio 2017 — zmiana lokalizacji instalacji](media/installation-options-by-location.png "zmiana lokalizacji instalacji")

  > [!IMPORTANT]
  > Jeśli wstrzymać instalację, a później je wznowić, Visual Studio przejmuje tam, gdzie ją przerwaliśmy. Oznacza to co pozostało do pobrania i zainstalowania, a nie rozpoczyna się od poprzedniego dotyczy jego postęp instalacji.

2. W **środowiska IDE programu Visual Studio** sekcji, zaakceptuj wartość domyślną. Instaluje produkt core i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

 > [!IMPORTANT]
 > Jeśli dysk systemowy jest dysków półprzewodnikowych (SSD), w tym miejscu firmy Dlaczego firma Microsoft zaleca zaakceptuj lokalizację domyślną na dysku systemowym: podczas tworzenia za pomocą programu Visual Studio możesz z do odczytu i zapisu wiele plików, co zwiększa dysku, operacje wejścia / wyjścia.  Najlepiej wybrać dysk najszybszy do obsługi obciążenia.

2. W **pamięć podręczna pobierania** sekcji, zdecyduj, czy chcesz zachować pamięci podręcznej pobierania, a następnie zaznacz lub wyczyść **pamięci podręcznej pobierania Zachowaj** odpowiednio. <br><br>Jeśli nie chcesz przechowywać w pamięci podręcznej pobierania, ta lokalizacja będzie używana tylko tymczasowo. Ta akcja nie będzie także mają wpływ na lub usuwania plików z poprzedniej instalacji. (Aby wyczyścić wszystkie pakiety instalacyjne, należy zmodyfikować poprzedniej instalacji oddzielnie.)

3. W **pamięć podręczna pobierania** sekcji, określ dysk, na którym chcesz przechowywać pliki instalacyjne i manifesty. <br><br>Na przykład jeśli wybierzesz obciążenie "Programowanie aplikacji klasycznych w języku C++", tymczasowo wymagany rozmiar jest 1.58 GB na dysku systemowym, który następnie zostanie zwolniony, zaraz po zakończeniu instalacji.

 > [!NOTE]
 > Pliki są najpierw pobrany do folderu tymczasowego na dysku systemowym i później usunięta po programu Visual Studio sprawdza i przenosi je do folderu pamięci podręcznej pobierania. Jeśli wybrano opcję zachowania pamięci podręcznej pobierania na inny dysk, program Visual Studio nadal wymaga miejsca na dysku, który jest odpowiednikiem rozmiar pamięci podręcznej pobierania na dysku systemowym.
 > [!IMPORTANT]
 > Lokalizacja została ustawiona za pomocą przez pierwszą instalację i nie można zmienić później z poziomu interfejsu użytkownika Instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) przenieść pamięci podręcznej pobierania

4. W **udostępnione składniki, narzędzia i zestawy SDK** sekcji, określ dysk, na którym chcesz przechowywać pliki, które są współużytkowane przez instalacje programu Visual Studio side-by-side. Zestawy SDK i narzędzia umożliwiające Instalatora programu Visual Studio należy zmienić jego lokalizację instalacji, również są przechowywane w tym katalogu.

 > [!NOTE]
 > Istnieją pewne narzędzia i zestawy SDK, które mają różne reguły na, gdzie mogą być są zainstalowane. Te narzędzia i zestawy SDK pozostaną zainstalowane na dysku systemowym, nawet jeśli wybierz inną lokalizację.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio 2017](install-visual-studio.md)
* [Update Visual Studio 2017](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio 2017](update-visual-studio.md)
* [Odinstaluj program Visual Studio 2017](uninstall-visual-studio.md)
