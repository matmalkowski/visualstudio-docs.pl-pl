---
title: Przykłady parametru wiersza polecenia do instalacji programu Visual Studio
description: Dostosowywanie tych przykładach, można utworzyć wiersza polecenia instalacji programu Visual Studio.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 829a7892b1d35df2fe5cd2a42dcc431f5ccbb7dc
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36279954"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Przykłady parametru wiersza polecenia do instalacji programu Visual Studio 2017 r.

Aby zilustrować jak [używania parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md), poniżej przedstawiono kilka przykładów, które można dostosować w celu dostosowania potrzeb.

W każdym przykładzie `vs_enterprise.exe`, `vs_professional.exe` i `vs_community.exe` reprezentują odpowiedniej wersji programu inicjującego Visual Studio, czyli pliku małych (około 1 MB), który inicjuje proces pobierania. Jeśli używasz innej wersji, należy zastąpić nazwę odpowiedniego programu inicjującego.

> [!NOTE]
> Wszystkie polecenia wymaga podniesienia uprawnień administracyjnych i kontrola konta użytkownika, jeśli proces nie została uruchomiona z podniesionego wiersza zostanie wyświetlony monit.
>
> [!NOTE]
>  Można użyć `^` znak na końcu wiersza polecenia do łączenia wielu wierszy do jednego polecenia. Alternatywnie można po prostu umieścić te wiersze razem na jeden wiersz. W programie PowerShell odpowiednikiem jest backtick (`` ` ``) znaków.

## <a name="using---installpath"></a>Przy użyciu--installPath

* Zainstaluj minimalnego wystąpienie programu Visual Studio z nie interakcyjne monitów, ale wyświetlany postęp:

 ```cmd
 vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
 ```

* Aktualizacja wystąpienia programu Visual Studio przy użyciu wiersza polecenia nie interakcyjne monitów, ale wyświetlany postęp:

 ```cmd
 vs_enterprise.exe --update --quiet --wait
 vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
 ```

 > [!NOTE]
 > Oba polecenia są wymagane. Pierwsze polecenie aktualizacji, Instalator programu Visual Studio. Drugie polecenie aktualizuje wystąpienie programu Visual Studio. Aby uniknąć okno dialogowe kontroli konta użytkownika, należy uruchomić wiersz polecenia jako Administrator.

* Zainstalować pulpitu wystąpienie programu Visual Studio w trybie dyskretnym, przy użyciu pakietu języka francuskiego, zwracanie tylko wtedy, gdy jest zainstalowany produkt.

 ```cmd
 vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
 ```

 > [!NOTE]
 > `--wait` Parametr jest przeznaczony do użytku w pliku wsadowym. W pliku wsadowym wykonanie następnego polecenia nie będzie kontynuowane dopiero po ukończeniu instalacji. `%ERRORLEVEL%` Zmienna środowiskowa będzie zawierał wartość zwracaną polecenie, zgodnie z opisem w [używania parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

## <a name="using---layout"></a>Przy użyciu — układ

* Pobierz edytorze podstawowych programu Visual Studio (najbardziej minimalnej konfiguracji programu Visual Studio). Uwzględnij tylko pakiet języka angielskiego:

 ```cmd
 vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
 ```

* Pobierz pulpitu .NET i .NET obciążenia sieci web oraz wszystkie zalecane składniki i rozszerzenie GitHub. Uwzględnij tylko pakiet języka angielskiego:

 ```cmd
 vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
 ```

## <a name="using---includerecommended"></a>Przy użyciu--includeRecommended

* Uruchom instalacji interakcyjnej wszystkich obciążeń i składników, które są dostępne w wersji Visual Studio 2017 Enterprise:

 ```cmd
 vs_enterprise.exe --all --includeRecommended --includeOptional
 ```

* Drugi nazwane wystąpienie programu Visual Studio 2017 Professional zostaną zainstalowane na komputerze z zainstalowanym, obsługę programowania Node.js w wersji Visual Studio 2017 Community:

 ```cmd
 vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
 ```

## <a name="using---remove"></a>Przy użyciu — Usuń

* Usuń składnik narzędzi profilowania z domyślnego zainstalowane wystąpienie programu Visual Studio:

 ```cmd
 vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
 ```

## <a name="using---path"></a>Przy użyciu — ścieżki

Te parametry wiersza polecenia są **nowego 15.7**. Aby uzyskać więcej informacji na ich temat, zobacz [używania parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

* Korzystanie z instalacji, pamięci podręcznej i ścieżki udostępnionego:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Przy użyciu tylko ścieżek instalacji i pamięci podręcznej:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Przy użyciu tylko instalacji i ścieżki udostępnionego:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Przy użyciu tylko ścieżka instalacji:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tworzenie w trybie offline instalację programu Visual Studio 2017 r.](create-an-offline-installation-of-visual-studio.md)
