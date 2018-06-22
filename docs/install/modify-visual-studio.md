---
title: Modyfikowanie Visual Studio 2017 | Dokumentacja firmy Microsoft
description: Dowiedz się, jak zmodyfikuj program Visual Studio, krok po kroku.
ms.custom: H1Hack27Feb2017
ms.date: 06/12/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e63a21a6090f4d3c7b1a371fc667325eed9ba65
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36296359"
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Modyfikowanie Visual Studio 2017 przez dodanie lub usunięcie obciążeń i składniki

Nie tylko ma wprowadziliśmy łatwiej można spersonalizować Visual Studio, aby dopasować zadań, należy wykonać, wprowadziliśmy również go łatwiej zbyt Dostosowywanie programu Visual Studio. Aby to zrobić, Uruchom nowe Instalator programu Visual Studio i wprowadź żądane zmiany.

Poniżej przedstawiono sposób.

## <a name="modify-workloads"></a>Modyfikowanie obciążeń

 Obciążeń zawiera funkcje, które należy do programowania języka lub platformy, którego używasz. Zmodyfikować Visual Studio, dzięki czemu obsługuje pracę, którą chcesz wykonać, jeśli chcesz to zrobić za pomocą obciążeń.

>[!IMPORTANT]
>Aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i programu Visual Studio](../ide/user-permissions-and-visual-studio.md).

1. Instalator programu Visual Studio odnaleźć na tym komputerze.

     Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do literę **V**, w którym znajduje się w **Instalator programu Visual Studio**.

     ![Instalator programu Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "zlokalizować Instalator programu Microsoft Visual Studio")

     >[!NOTE]
     >Na niektórych komputerach, Instalator programu Visual Studio może być wyświetlany poniżej literę **"M"** jako **Microsoft Visual Studio Instalatora**.<br/><br/> Alternatywnie Instalator programu Visual Studio można znaleźć w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2. Kliknij lub naciśnij, aby uruchomić Instalatora, a następnie wybierz pozycję **Modyfikuj**.

     ![Uruchom lub zmodyfikuj program Visual Studio](media/modify-visual-studio.png "zmodyfikować 2017 Visual Studio")

     Jeśli masz oczekujących aktualizacji przycisk Modyfikuj jest w innym miejscu. Dzięki temu można zmodyfikować Visual Studio bez aktualizacji, należy wybrać w tym celu. Kliknij przycisk **więcej**, a następnie wybierz pozycję **Modyfikuj**.

     ![Zaktualizuj lub zmodyfikuj program Visual Studio](media/modify-or-update-visual-studio.png "aktualizacji lub zmodyfikować Visual Studio 2017 r.")

3. Z **obciążeń** ekranu, zaznacz lub odznacz obciążeń, które chcesz zainstalować lub odinstalować.

    ![Okno dialogowe programu Visual Studio 2017 ustawienia](media/vs2017-modify-workloads.PNG "wybierz obciążenie w Visual Studio 2017 r.")

4. Wybierz **Modyfikuj** ponownie.

5. Po zainstalowaniu nowego obciążeń i składników, wybierz **uruchamianie**.

## <a name="modify-individual-components"></a>Zmodyfikować poszczególne składniki

Jeśli nie chcesz dostosować instalację programu Visual Studio, wybierz za pomocą funkcji przydatną obciążeń **pojedynczych składników** z Instalator programu Visual Studio, wybierz, jakie mają i postępuj monitów.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony, aby uzyskać pomoc. Można również skontaktować się nam pomocy instalacji przez [komunikatora](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko angielski); Aby uzyskać więcej informacji, zobacz [programu Visual Studio "Skontaktuj się z nami" strony](https://visualstudio.microsoft.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Zainstaluj program Visual Studio 2017 r.](install-visual-studio.md)
* [Update Visual Studio 2017](update-visual-studio.md)
* [Odinstaluj program Visual Studio 2017 r.](uninstall-visual-studio.md)
