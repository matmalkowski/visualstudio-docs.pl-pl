---
title: "Przykłady parametru wiersza polecenia do instalacji programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
manager: ghogen
ms.openlocfilehash: a3b12bfe0c289bfdefc6e3107960fd94889df287
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
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
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także

 * [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
 * [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Tworzenie w trybie offline instalację programu Visual Studio 2017 r.](create-an-offline-installation-of-visual-studio.md)
