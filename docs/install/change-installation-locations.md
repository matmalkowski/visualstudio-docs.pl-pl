---
title: Zmień lokalizację instalacji w programie Visual Studio 2017 r.
description: Dowiedz się, jak ograniczyć wpływ instalacji na dysku systemowym, zmieniając lokalizację pamięci podręcznej pobierania, udostępniane składniki, zestawy SDK i narzędzi na różnych dyskach.
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
ms.openlocfilehash: eef4f8b66da517e471a25bb36e777f6cc343b0a3
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33995783"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Zmień lokalizację instalacji w programie Visual Studio 2017 r.

**Nowość w 15.7**: można ograniczyć wpływ instalacji na dysku systemowym przez przeniesienie pamięć podręczną pobierania, udostępniane składniki, zestawy SDK i narzędzi na różnych dyskach.

Poniżej przedstawiono sposób.

1. Po zainstalowaniu programu Visual Studio wybierz **opcje instalacji** kartę.

  ![Visual Studio 2017 — Zmień lokalizację instalacji](media/installation-options-by-location.png "Zmień lokalizację instalacji")

  > [!IMPORTANT]
  > Jeśli instalacji wstrzymać i wznowić jego, Visual Studio przejmuje miejsca, w którym. Innymi słowy pozostało do pobrania i zainstalowania i nie rozpoczyna się od poprzedniej liczba dotyczy jego postęp instalacji.

2. W **programu Visual Studio IDE** pozycję Zaakceptuj wartość domyślną. Instaluje produkt core i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

 > [!IMPORTANT]
 > Jeśli dysk systemowy jest dysków półprzewodnikowych (SSD), w tym miejscu jego Dlaczego zalecamy zaakceptuj lokalizację domyślną na dysku systemowym: podczas pracy z programem Visual Studio, możesz z do odczytu i zapisu wiele plików, co zwiększa dysku operacje wejścia/wyjścia.  Najlepiej wybrać dysk najszybszy obsłużyć obciążenia.

2. W **pobrać pamięci podręcznej** sekcji, jeśli chcesz zachować pamięć podręczną pobierania, a następnie zaznacz lub usuń zaznaczenie **pamięć podręczną pobierania Zachowaj** odpowiednio. <br><br>Jeśli nie chcesz przechowywać pamięć podręczną pobierania, tylko tymczasowo użyć lokalizacji. Ta akcja nie będzie również wpływać na lub usuwania plików z poprzedniej instalacji. (Aby wyczyścić wszystkie pakiety instalacyjne, należy zmodyfikować poprzedniej instalacji oddzielnie.)

3. W **pobrać pamięci podręcznej** sekcji, określić dysk, na którym chcesz przechowywać pliki instalacyjne i manifestów. <br><br>Na przykład w przypadku wybrania obciążenie "Pulpitu Programowanie w języku C++" tymczasowo wymagany rozmiar jest 1.58 GB na dysku systemowym, który następnie zostanie zwolniona zaraz po zakończeniu instalacji.

 > [!NOTE]
 > Pliki są najpierw pobierany do folderu tymczasowego na dysku systemowym i później usunięta po Visual Studio weryfikuje i przenosi je do folderu pamięci podręcznej pobierania. Jeśli wybierzesz opcję Zachowaj pamięć podręczną pobierania na inny dysk, Visual Studio nadal wymaga miejsca na dysku jest odpowiednikiem rozmiar pamięci podręcznej pobierania na dysku systemowym.
 > [!IMPORTANT]
 > Lokalizacja została skonfigurowana przy instalacji pierwszego i nie można zmienić później z Instalatorem interfejsu użytkownika. Zamiast tego należy [używania parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) można przenieść pamięć podręczną pobierania

4. W **udostępnionych składników, narzędzia i zestawy SDK** sekcji, określić dysk, na którym chcesz przechowywać pliki, które są udostępniane przez side-by-side instalacje programu Visual Studio. Zestawy SDK i narzędzia, które pozwalają Instalator programu Visual Studio można zmienić lokalizacji instalacji również przechowywane w tym katalogu.

 > [!NOTE]
 > Istnieją pewne narzędzia i zestawy SDK, które mają różne zasady na, gdzie mogą być są zainstalowane. Te narzędzia i zestawy SDK będzie nadal można zainstalować na dysku systemowym, nawet jeśli wybierz inną lokalizację.)

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony, aby uzyskać pomoc. Można również skontaktować się nam pomocy instalacji przez [komunikatora](https://www.visualstudio.com/vs/support/#talktous) (tylko angielski); Aby uzyskać więcej informacji, zobacz [programu Visual Studio "Skontaktuj się z nami" strony](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Zainstaluj program Visual Studio 2017 r.](install-visual-studio.md)
* [Update Visual Studio 2017](update-visual-studio.md)
* [Modyfikowanie 2027 usługi Visual Studio](update-visual-studio.md)
* [Odinstaluj program Visual Studio 2017 r.](uninstall-visual-studio.md)
