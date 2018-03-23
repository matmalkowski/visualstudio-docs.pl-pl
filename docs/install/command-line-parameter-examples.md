---
title: Przykłady parametru wiersza polecenia do instalacji programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/06/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d9d13daf406dc0c39d6a2f3571acf5f60c763126
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Przykłady parametru wiersza polecenia do instalacji programu Visual Studio 2017 r.
Aby zilustrować jak [używania parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md), poniżej przedstawiono kilka przykładów, które można dostosować w celu dostosowania potrzeb.

W każdym przykładzie `vs_enterprise.exe`, `vs_professional.exe` i `vs_community.exe` reprezentują odpowiedniej wersji programu inicjującego Visual Studio, czyli pliku małych (około 1 MB), który inicjuje proces pobierania. Jeśli używasz innej wersji, należy zastąpić nazwę odpowiedniego programu inicjującego.

> [!NOTE]
> Wszystkie polecenia wymaga podniesienia uprawnień administracyjnych i kontrola konta użytkownika, jeśli proces nie została uruchomiona z podniesionego wiersza zostanie wyświetlony monit.

> [!NOTE]
>  Można użyć `^` znak na końcu wiersza polecenia do łączenia wielu wierszy do jednego polecenia. Alternatywnie można po prostu umieścić te wiersze razem na jeden wiersz. W programie PowerShell odpowiednikiem jest backtick (`` ` ``) znaków.

* Zainstaluj minimalnego wystąpienie programu Visual Studio z nie interakcyjne monitów, ale wyświetlany postęp:
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Aktualizacja wystąpienia programu Visual Studio przy użyciu wiersza polecenia nie interakcyjne monitów, ale wyświetlany postęp:
```
vs_enterprise.exe --update --quiet --wait
vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
```

> [!NOTE]
> Oba polecenia są wymagane. Pierwsze polecenie aktualizacji, Instalator programu Visual Studio. Drugie polecenie aktualizuje wystąpienie programu Visual Studio. Aby uniknąć okno dialogowe kontroli konta użytkownika, należy uruchomić wiersz polecenia jako Administrator.

* Zainstalować pulpitu wystąpienie programu Visual Studio w trybie dyskretnym, przy użyciu pakietu języka francuskiego, zwracanie tylko wtedy, gdy jest zainstalowany produkt.
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  `--wait` Parametr jest przeznaczony do użytku w pliku wsadowym. W pliku wsadowym wykonanie następnego polecenia nie będzie kontynuowane dopiero po ukończeniu instalacji. `%ERRORLEVEL%` Zmienna środowiskowa będzie zawierał wartość zwracaną polecenie, zgodnie z opisem w [używania parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

* Pobierz edytorze podstawowych programu Visual Studio (najbardziej minimalnej konfiguracji programu Visual Studio). Uwzględnij tylko pakiet języka angielskiego:

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* Pobierz pulpitu .NET i .NET obciążenia sieci web oraz wszystkie zalecane składniki i rozszerzenie GitHub. Uwzględnij tylko pakiet języka angielskiego:
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Uruchom instalacji interakcyjnej wszystkich obciążeń i składników, które są dostępne w wersji Visual Studio 2017 Enterprise:
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Drugi nazwane wystąpienie programu Visual Studio 2017 Professional zostaną zainstalowane na komputerze z zainstalowanym, obsługę programowania Node.js w wersji Visual Studio 2017 Community:
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* Usuń składnik narzędzi profilowania z domyślnego zainstalowane wystąpienie programu Visual Studio:
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

 * [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
 * [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Tworzenie w trybie offline instalację programu Visual Studio 2017 r.](create-an-offline-installation-of-visual-studio.md)
