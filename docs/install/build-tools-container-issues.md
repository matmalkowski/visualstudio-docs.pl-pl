---
title: Znane problemy dotyczące kontenerów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c433716b0a5623fa9b4f098952b4c951d8b52e12
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="known-issues-for-containers"></a>Znane problemy dotyczące kontenerów

Istnieje kilka problemów podczas instalowania programu Visual Studio w kontenerze Docker.

## <a name="windows-container"></a>Kontener systemu Windows

Następujące znane problemy występować po zainstalowaniu programu Visual Studio kompilacji 2017 narzędzia do kontenera systemu Windows.

* Nie można zainstalować programu Visual Studio do kontenera oparte na microsoft/windowsservercore:10.0.14393.1593 obrazu. Obrazy z systemu Windows w wersji starszej lub nowszej powinna działać.
* Nie można zainstalować zestaw Windows SDK w wersji wcześniejszej niż 10.0.14393. Niektóre pakiety nie można zainstalować i obciążeń, które są zależne od tych pakietów nie będzie działać.
* Należy podać `-m 2GB` (lub więcej) podczas tworzenia obrazu. Niektóre obciążenia wymagają więcej pamięci niż domyślna 1 GB, podczas instalacji.
* Należy skonfigurować Docker do dysków o większych niż domyślne 20 GB.
* Należy podać `--norestart` w wierszu polecenia. Zgodnie z tym próba ponownego uruchomienia kontenera systemu Windows z poziomu kontenera zwraca `ERROR_TOO_MANY_OPEN_FILES` do hosta.

## <a name="build-tools-container"></a>Kontener narzędzia kompilacji

Następujące znane problemy mogą wystąpić, jeśli używasz kontenera Build Tools. Zobacz, czy zostały rozwiązane problemy lub jeśli istnieją inne znanych problemów, odwiedź witrynę https://developercommunity.visualstudio.com.

* Funkcja IntelliTrace nie może działać w [Niektóre scenariusze](https://github.com/Microsoft/vstest/issues/940) w kontenerze.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Visual Studio kompilacji narzędzia 2017 obciążenia i składnik identyfikatorów](workload-component-id-vs-build-tools.md)
