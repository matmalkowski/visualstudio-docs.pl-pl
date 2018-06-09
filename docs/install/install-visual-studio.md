---
title: Zainstaluj program Visual Studio 2017 | Dokumentacja firmy Microsoft
description: Dowiedz się, jak zainstalować program Visual Studio, krok po kroku.
ms.custom: ''
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6ebc81e1aed2cd007bf34a5e9145c0b995517fd
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238241"
---
# <a name="install-visual-studio-2017"></a>Zainstaluj program Visual Studio 2017 r.

Nowy sposób, aby zainstalować program Visual Studio — Zapraszamy! W naszym najnowsza wersja ułatwiliśmy ułatwia wybierania i instalowania tylko potrzebnych funkcji, które są potrzebne. Minimalnego miejsca zajmowanego przez program Visual Studio również już zostać zmniejszony, tak aby zainstalował szybciej i z mniejszym wpływem na system niż kiedykolwiek wcześniej.

Chcesz dowiedzieć się więcej na temat innych nowości w tej wersji? Zobacz nasze [informacje o wersji](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Gotowe do zainstalowania? Pomożemy Ci przez niego krok po kroku.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 — Upewnij się, że komputer jest gotowy dla programu Visual Studio

Przed rozpoczęciem instalowania programu Visual Studio:

1. Sprawdź [wymagania systemowe](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Te wymagania ułatwiają wiedzieć, czy komputer obsługuje Visual Studio 2017 r.
2. Zastosuj najnowsze aktualizacje systemu Windows. Te aktualizacje upewnij się, że komputer ma zarówno najnowsze aktualizacje zabezpieczeń i składniki systemowe wymagane dla programu Visual Studio.
3. Ponowne uruchomienie komputera. Ponownego rozruchu gwarantuje, że wszystkie oczekujące instaluje lub aktualizacji nie utrudniać instalację programu Visual Studio.
4. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z sieci % SystemDrive %, na przykład aplikację Oczyszczanie dysku.

Odpowiedzi na pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok siebie z programu Visual Studio 2017, zobacz [szczegóły zgodności programu Visual Studio](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Krok 2 — pobierania programu Visual Studio

Następnie należy pobrać plik inicjujący Instalatora programu Visual Studio. Aby to zrobić, kliknij poniższy przycisk, wybierz wersji programu Visual Studio 2017, żądany, kliknij przycisk **zapisać**, a następnie kliknij przycisk **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio 2017](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) o tym, jak pobrać plik inicjujący Instalatora programu Visual Studio i wybierz wersję programu Visual Studio, które jest odpowiednie dla Ciebie. |

## <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — Instalowanie Instalator programu Visual Studio

Następnie uruchom plik inicjujący tak, aby zainstalować Instalator programu Visual Studio. To nowe lekkie zawiera wszystkie elementy potrzebne do zainstalowania i dostosowywanie programu Visual Studio 2017 r.

1. Z sieci **pobiera** folderu, kliknij dwukrotnie plik inicjujący, który pasuje do lub jest podobny do jednego z następujących plików:

  * **vs_enterprise.exe** dla programu Visual Studio Enterprise
  * **vs_professional.exe** for Visual Studio Professional
  * **vs_community.exe** for Visual Studio Community  <br><br>

  Jeśli zostanie wyświetlone powiadomienie kontroli konta użytkownika, kliknij przycisk **tak**.

2. Poprosimy Cię możesz potwierdzić Microsoft [postanowień licencyjnych](https://www.visualstudio.com/license-terms/) i Microsoft [zasady zachowania poufności informacji](https://go.microsoft.com/fwlink/?LinkID=824704). Kliknij przycisk **Kontynuuj**.  

   ![Licencja warunki i zasady zachowania poufności informacji](media/vs2017-privacy-and-license-terms.PNG "postanowienia licencyjne firmy Microsoft i zasady zachowania poufności informacji")

## <a name="step-4---select-workloads"></a>Krok 4 — Wybierz obciążeń

Po zainstalowaniu Instalator, można go dostosować instalację, wybierając zestawy funkcji — lub obciążeń, który ma. Poniżej przedstawiono sposób.

1. Znajdź obciążenia w **Instalowanie programu Visual Studio** ekranu.

 ![Wybieranie obciążenia w oknie dialogowym Instalator Visual Studio 2017 r.](../install/media/install-visual-studio-community.png)

     Na przykład wybierz obciążenie ".NET development pulpitu". Pochodzi on z domyślnego edytora core, która obejmuje podstawowych czynności edytowania Obsługa ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu kodu i zintegrowane kontroli kodu źródłowego.  

2. Po wybraniu workload(s) ma, kliknij przycisk **zainstalować**.

    Następnie stan pojawią się ekrany pokazujące postęp instalacji programu Visual Studio.

3. Po zainstalowaniu nowego obciążeń i składników, kliknij przycisk **uruchamianie**.  

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążeń lub składniki, które należy wstępnie zainstalować. Jeśli masz program Visual Studio Otwórz, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**  otwierający Instalator programu Visual Studio. Możesz również otworzyć **Instalator programu Visual Studio** z Start menu. Z tego miejsca, możesz wybrać obciążeń lub składniki, które chcesz zainstalować, a następnie kliknij przycisk **Modyfikuj**.  

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) na temat sposobu instalacji Instalator programu Visual Studio, a następnie zainstaluj obciążenia. |

## <a name="step-5---select-individual-components-optional"></a>Krok 5. Wybierz poszczególne składniki (opcjonalnie)

Jeśli nie chcesz dostosować instalację programu Visual Studio za pomocą funkcji obciążeń, możesz to zrobić, instalując zamiast pojedynczych składników. Aby wybrać poszczególne składniki, kliknij przycisk **pojedynczych składników** z Instalator programu Visual Studio, wybierz, co użytkownik ma, a następnie wykonaj monitów.

  ![Visual Studio 2017 r - instalacji poszczególnych składników](media/vs2017-components.PNG "poszczególnych składników instalacji programu Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Ikona aparatu film wideo](media/video-icon.png "obejrzeć film wideo")  |   [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) na temat sposobu instalacji poszczególnych składników za pomocą Instalator programu Visual Studio. |

## <a name="step-6---install-language-packs-optional"></a>Krok 6 — instalowanie pakietów językowych (opcjonalnie)

Domyślnie program Instalator podejmuje próbę język systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio 2017 w języku wybrane, kliknij przycisk **pakiety językowe** opcję Instalator programu Visual Studio i postępuj zgodnie z monitami.

  ![Visual Studio 2017 — instalowanie pakietów językowych](media/vs2017-languages.PNG "pakiety językowe program Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Ikona aparatu film wideo](media/video-icon.png "obejrzeć film wideo")  |   [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) dotyczące instalacji pakietu językowego przy użyciu Instalator programu Visual Studio. |

### <a name="change-the-installer-language-from-the-command-line"></a>Zmień język Instalatora z wiersza polecenia

Inny sposób, że można zmienić domyślny język jest uruchamiając Instalatora z wiersza polecenia. Na przykład możesz wymusić Instalatora, aby uruchomić w języku angielskim, za pomocą następującego polecenia: `vs_installer.exe --locale en-US`. Instalator zapamiętuje to ustawienie po przy następnym uruchomieniu. Instalator obsługuje następujące tokeny języka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Krok 7 — Zmień lokalizację instalacji (opcjonalnie)

**Nowość w 15.7**: teraz można zmniejszyć rozmiaru instalacji programu Visual Studio na dysku systemowym. Istnieje możliwość przenoszenia pamięć podręczną pobierania, udostępniane składniki, zestawy SDK i narzędzi na różnych dyskach, a także zapewnić Visual Studio na dysku, który uruchamia go najszybciej.

  ![Visual Studio 2017 — Zmień lokalizację instalacji](media/installation-options-by-location.png "Zmień lokalizację instalacji")

Aby uzyskać więcej informacji, zobacz [zmienić lokalizację instalacji programu Visual Studio](change-installation-locations.md) strony.

## <a name="step-8---start-developing"></a>Krok 8 — rozpocząć tworzenie

1. Po zakończeniu instalacji programu Visual Studio kliknij **uruchamianie** przycisk, aby [rozpocząć wdrażanie z programem Visual Studio](../ide/get-started-developing-with-visual-studio.md).

2. Kliknij przycisk **pliku**, a następnie kliknij przycisk **nowy projekt**.

3. Wybierz typ projektu. <br><br>
   Na przykład, aby [tworzenie aplikacji C++](../ide/getting-started-with-cpp-in-visual-studio.md), kliknij przycisk **zainstalowana**, rozwiń węzeł **Visual C++**, a następnie wybierz typ projektu C++, który chcesz utworzyć. <br><br>
   Do [kompilowania aplikacji C#](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), kliknij przycisk **zainstalowana**, rozwiń węzeł **Visual C#**, a następnie wybierz typ projektu C#, który chcesz utworzyć.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Update Visual Studio 2017](update-visual-studio.md)
* [Modyfikowanie Visual Studio 2017 r.](modify-visual-studio.md)
* [Odinstaluj program Visual Studio 2017 r.](uninstall-visual-studio.md)
* [Tworzenie w trybie offline instalację programu Visual Studio 2017 r.](create-an-offline-installation-of-visual-studio.md)
* [Przewodnik administratora 2017 r w usłudze Visual Studio](visual-studio-administrator-guide.md)
  * [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017 r.](use-command-line-parameters-to-install-visual-studio.md)
* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
