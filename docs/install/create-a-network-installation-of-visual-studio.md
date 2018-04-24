---
title: Utworzyć sieciowej instalację programu Visual Studio
description: Dowiedz się, jak utworzyć punkt instalacji sieci do wdrażania programu Visual Studio w obrębie przedsiębiorstwa.
ms.date: 10/17/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fdecc141affcb88d0a04346767469ef5296557d
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Tworzenie instalacji sieciowej programu Visual Studio 2017 r.

Często administrator przedsiębiorstwa tworzy punkt instalacji sieci do wdrożenia na klienckich stacjach roboczych. Firma Microsoft została zaprojektowana Visual Studio 2017 do pamięci podręcznej plików początkowej instalacji oraz wszystkie aktualizacje produktu w jednym folderze. (Ten proces jest również nazywany _tworzenia układu_.) Firma Microsoft już zostało to zrobione, aby klienckie stacje robocze umożliwiają zarządzanie ich instalacji, nawet jeśli ich nie zostały jeszcze zaktualizowane do obsługi najnowszych aktualizacji tej samej lokalizacji sieciowej.

 > [!NOTE]
 > Jeśli masz wiele wersji programu Visual Studio używany w obrębie przedsiębiorstwa (na przykład Visual Studio Professional i Visual Studio Enterprise), należy utworzyć udział instalacji oddzielnej sieci dla każdej wersji.

## <a name="download-the-visual-studio-bootstrapper"></a>Pobierz inicjujący Instalatora programu Visual Studio

**Pobierz** wersji programu Visual Studio ma. Upewnij się, że **zapisać**, a następnie kliknij przycisk **Otwórz folder**.

Ustawienia pliku wykonywalnego&mdash;lub dokładniej, pliku inicjującego&mdash;powinna być zgodna z jedną z następujących czynności.

|Wersja | Pobieranie|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Visual Studio Community | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

Inne obsługiwane bootstrappers obejmują [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe), i [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Utwórz folder instalacji w trybie offline

Musi mieć połączenie internetowe, aby ukończyć ten krok. Do utworzenia instalacji w trybie offline z wszystkich języków i wszystkie funkcje, użyj jednej z poniższych przykładach poleceń.

   > [!IMPORTANT]
   > Pełny układ Visual Studio 2017 wymaga co najmniej 35 GB miejsca na dysku i może zająć trochę czasu, aby pobrać.  Zobacz [Dostosowywanie układ sieci](#customizing-the-network-layout) sekcji, aby uzyskać więcej informacji na temat sposobu tworzenia układu ze składnikami, które chcesz zainstalować.
   >
   > [!TIP]
   > Upewnij się, uruchom polecenie z katalogu pobierania. Zwykle to jest `C:\Users\<username>\Downloads` na komputerze z systemem Windows 10.

- For Visual Studio Enterprise, run:

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Dla programu Visual Studio Professional Uruchom polecenie:

  ```vs_professional.exe --layout c:\vs2017offline```

- For Visual Studio Community, run:

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Modyfikowanie pliku response.json

Można zmodyfikować response.json można ustawić wartości domyślne, które są używane po uruchomieniu Instalatora.  Na przykład można skonfigurować `response.json` plik, aby wybrać określony zbiór obciążeń wybierana automatycznie.
Zobacz [instalacji automatyzacji programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md) szczegółowe informacje.

## <a name="copy-the-layout-to-a-network-share"></a>Skopiuj układ do udziału sieciowego

Host układu w udziale sieciowym, co może być uruchamiane z innych komputerów.
* Przykład:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```

## <a name="customizing-the-network-layout"></a>Dostosowywanie układ sieci

Dostępnych jest kilka opcji, w którym można dostosować układ sieci. Możesz utworzyć układ częściowej zawiera tylko określonego zestawu [ustawień regionalnych języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [obciążeń, składniki oraz ich zależności zalecane lub opcjonalne](workload-and-component-ids.md). Może to być przydatne, jeśli wiadomo, że zamierzasz wdrożyć tylko podzestaw obciążeń na klienckich stacjach roboczych. Typowe parametry wiersza polecenia dostosowywania układ obejmują:

* ```--add``` Aby określić [identyfikatorów obciążenia lub składnik](workload-and-component-ids.md).  Jeśli `--add` jest używana, tylko obciążeń i składniki określony za pomocą `--add` zostaną pobrane.  Jeśli `--add` jest nieużywane, obciążenia i wszystkie składniki zostaną pobrane.
* ```--includeRecommended``` Aby uwzględnić wszystkie składniki zalecane do określonego obciążenia identyfikatorów
* ```--includeOptional``` Aby uwzględnić wszystkie składniki zalecane i opcjonalne dla określonych obciążeń identyfikatorów.
* ```--lang``` Aby określić [ustawień regionalnych języka](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Oto kilka przykładów sposobu tworzenia niestandardowego układu częściowej.

* Aby pobrać obciążeń i wszystkie składniki tylko dla jednego języka, uruchom polecenie: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
* Aby pobrać obciążeń i wszystkie składniki wielu języków, uruchom polecenie: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
* Aby pobrać jeden obciążenia dla wszystkich języków, uruchom <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
* Aby pobrać dwóch obciążeń i jeden składnik opcjonalny w trzech językach, uruchom polecenie: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
* Aby pobrać dwóch obciążeń i wszystkie ich zalecane składniki, uruchom polecenie: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
* Aby pobrać dwóch obciążeń i wszystkie ich zalecane i opcjonalne składniki, uruchom polecenie: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```

### <a name="new-in-153"></a>Nowość w wersji 15 ustęp 3

Po uruchomieniu polecenia układ, opcje, które określisz są zapisywane (na przykład obciążeń i języków). Układ kolejne polecenia będzie zawierać wszystkie poprzednie opcje.  Poniżej przedstawiono przykład układu z tylko jednego obciążenia angielski:

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US```

Jeśli chcesz zaktualizować do nowszej wersji tego układu, nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia są zapisywane i używane przez wszystkie polecenia kolejnych układu, w tym folderze układu.  Następujące polecenie spowoduje zaktualizowanie istniejących układu częściowej.

```vs_enterprise.exe --layout c:\VS2017Layout```

Jeśli chcesz dodać dodatkowych obciążeń, tutaj przykładem to zrobić. W takim przypadku dodamy obciążenia Azure i języku lokalnym.  Teraz zarządzane komputerowych i Azure znajdują się w tym układzie.  Zasoby językowe dla są w języku angielskim i niemieckim obejmują dla tych zadań. Układ zostało zaktualizowane do najnowszej dostępnej wersji.

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE```

Jeśli chcesz zaktualizować istniejący układ pełnego układ, użyj wszystkich opcji, jak pokazano w poniższym przykładzie.

```vs_enterprise.exe --layout c:\VS2017Layout --all```

## <a name="deploying-from-a-network-installation"></a>Wdrażanie z sieci

Administratorzy mogą wdrożyć program Visual Studio na klienckich stacjach roboczych, jako część skryptu instalacji. Lub użytkowników, którzy mają prawa administratora można uruchomić Instalatora bezpośrednio z udziału do zainstalowania programu Visual Studio na komputerze.

- Użytkownicy mogą zainstalować, uruchamiając: <br>```\\server\products\VS2017\vs_enterprise.exe```
- Administratorzy mogą instalować w trybie instalacji nienadzorowanej, uruchamiając: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Gdy wykonywane jako część pliku wsadowego `--wait` opcji zapewnia, że `vs_enterprise.exe` procesu czeka przed zakończeniem instalacji przed zwraca kod zakończenia. Jest to przydatne, jeśli chce wykonać dalsze działania na Ukończono instalację administratora przedsiębiorstwa (na przykład, aby [Zastosuj klucz produktu do pomyślnej instalacji](automatically-apply-product-keys-when-deploying-visual-studio.md)), ale należy poczekać na zakończenie do obsługi instalacji Kod powrotu z tej instalacji.  Jeśli nie używasz `--wait`, `vs_enterprise.exe` proces kończy się przed instalacja została zakończona i zwraca kod zakończenia niedokładne nie reprezentujący stan operacji instalacji.

Po zainstalowaniu z układu zawartość, która jest zainstalowana są uzyskiwane z układu. Jednak w przypadku wybrania składnika, który nie jest w układzie, będzie można uzyskać z Internetu.  Jeśli chcesz zapobiec instalacji programu Visual Studio pobieraniu zawartość, która nie istnieje w układzie, użyj `--noWeb` opcji.  Jeśli `--noWeb` jest używany i układu nie ma żadnej zawartości, który został wybrany do zainstalowania, konfiguracja kończy się niepowodzeniem.  

### <a name="error-codes"></a>Kody błędów

Jeśli używasz `--wait` parametr, a następnie w zależności od wyniku operacji `%ERRORLEVEL%` zmienna środowiskowa jest ustawiona na jedną z następujących wartości:

  | **Wartość** | **wynik** |
  | --------- | ---------- |
  | 0 | Operacja została wykonana pomyślnie |
  | 3010 | Operacja zakończyła się pomyślnie, ale instalacja wymaga ponownego uruchomienia, zanim będzie można go używać. |
  | Inne | Wystąpił błąd warunku — Sprawdź dzienniki, aby uzyskać więcej informacji |

## <a name="updating-a-network-install-layout"></a>Aktualizowanie układ instalacji sieci

Gdy będą dostępne aktualizacje produktu, może zaistnieć potrzeba [aktualizacji układu instalacji sieciowej](update-a-network-installation-of-visual-studio.md) uwzględnienie zaktualizowanych pakietów.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Tworzenie układu w poprzedniej wersji programu Visual Studio 2017 r.

> [!NOTE]
> Bootstrappers 2017 usługi Visual Studio, które są dostępne na [VisualStudio.com](http://www.visualstudio.com) pobranie i zainstalowanie najnowszej wersji programu Visual Studio 2017 dostępny zawsze, gdy są uruchamiane. Jeśli już dziś Pobierz programu inicjującego Visual Studio i uruchom go sześciu miesięcy od teraz, instaluje wersję programu Visual Studio 2017, która jest dostępna w późniejszym czasie. W przypadku utworzenia układu, instalacja programu Visual Studio z tego układu instaluje określonej wersji programu Visual Studio, który istnieje w układzie. Mimo że nowszej wersji może istnieć w trybie online, otrzymasz wersji programu Visual Studio, która jest w układzie.

Jeśli potrzebujesz do tworzenia układu dla starszej wersji programu Visual Studio 2017 r, możesz przejść do https://my.visualstudio.com pobierania "fixed" wersje bootstrappers programu Visual Studio 2017 r.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak uzyskać pomoc techniczną dla Twojego Instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcemy wiadomo o nim. Napisz, najlepiej przy użyciu [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia. Korzystając z tego narzędzia, możesz wysłać nam telemetrii i dzienniki potrzebujemy, aby pomóc nam zdiagnozować i rozwiązać problem.

Mamy zbyt inne dostępne opcje pomocy technicznej. Aby uzyskać listę, zobacz nasze [Porozmawiaj z nami](../ide/how-to-report-a-problem-with-visual-studio-2017.md) strony.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
