---
title: Zainstaluj na o niskiej przepustowości lub zawodnych w środowiskach sieci | Dokumentacja firmy Microsoft
description: W tym artykule opisano, jak Instalator programu Visual Studio działa w warunkach zawodnej sieci i wyjaśniono, jak pobrać pliki instalacji przed rozpoczęciem instalacji.
ms.date: 01/17/2018
ms.technology:
- vs-acquisition
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca2f541328e43a0c7b8d08697d10a905b9eb2cc1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Zainstaluj program Visual Studio 2017 na o niskiej przepustowości lub zawodnych w środowiskach sieci

Zalecamy wypróbowanie Instalator sieci web programu Visual Studio&mdash;naszym zdaniem znajdziesz ją dobrej doświadczenie w większości sytuacji.

 > [!div class="button"]
 > [Pobierz program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Jednak jeśli połączenie z Internetem jest niedostępne lub zawodnych, można użyć wiersza polecenia utworzyć lokalnej pamięci podręcznej plików trzeba wykonać instalację w trybie offline. Poniżej przedstawiono sposób.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce wykonać wdrożenie programu Visual Studio 2017 klienckich stacjach roboczych, które są zaporą z siecią Internet, zobacz nasze [Tworzenie instalacji sieciowej programu Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) i [Zainstalować certyfikaty wymagane do instalacji w trybie offline program Visual Studio](../install/install-certificates-for-visual-studio-offline.md) stron.

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 — pobieranie inicjujący Instalatora programu Visual Studio

Rozpocznij od pobierania programu Visual Studio inicjującego używanej wybranej wersji programu Visual Studio.

Plik Instalatora&mdash;lub dokładniej, plik inicjujący&mdash;będzie odpowiadać lub są podobne do jednej z następujących czynności.

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Krok 2 — Tworzenie instalacji lokalnej pamięci podręcznej

Musi mieć połączenie internetowe, aby ukończyć ten krok. Aby utworzyć lokalnego układu, otwórz wiersz polecenia i użyj jednej z poniższych przykładach poleceń: tutaj przykładów założono, że używasz wersji społeczności programu Visual Studio; Dostosuj polecenia odpowiednie dla posiadanej wersji.

- Dla sieci web .NET i .NET — rozwój pulpitu Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- .NET desktop i Office development Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Do tworzenia klasycznych aplikacji C++ Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Aby utworzyć pełną układ lokalnego z wszystkimi funkcjami (będzie to zająć dużo czasu&mdash;mamy _partii_ funkcji!), uruchom:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Jeśli chcesz zainstalować języka innego niż angielski, należy zmienić `en-US` ustawienia regionalne z listy w dolnej części strony. Użyj tej [listy składników i obciążeń dostępne](workload-and-component-ids.md) dostosować pamięć podręczną instalacji, w razie potrzeby.

> [!IMPORTANT]
> Pełny układ Visual Studio 2017 wymaga co najmniej 35 GB miejsca na dysku i może zająć trochę czasu, aby pobrać. Zobacz [używania parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) informacji na temat sposobu tworzenia układu z tylko składniki do zainstalowania.

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 — Instalacja programu Visual Studio z lokalnej pamięci podręcznej

> [!TIP]
> Po uruchomieniu z instalacji lokalnej pamięci podręcznej, Instalator używa lokalnych wersji każdy z tych plików. Jednak jeśli zostanie wybrana podczas instalacji składników, które nie znajdują się w pamięci podręcznej, możemy próbą pobrania ich z Internetu.

Aby zainstalować tylko pliki, które zostały pobrane, należy użyć tych samych opcji wiersza polecenia używane do tworzenia układu pamięci podręcznej. Na przykład, układu pamięci podręcznej został utworzony przy użyciu następującego polecenia:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Uruchom instalację za pomocą tego polecenia:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Jeśli zostanie wyświetlony błąd, że podpis jest nieprawidłowy, należy zainstalować certyfikaty zaktualizowane. Otwórz folder certyfikaty w pamięci podręcznej w trybie offline. Kliknij dwukrotnie plik certyfikatu, a następnie kliknij za pomocą Kreatora Menedżera certyfikatów. Jeśli pojawi się monit o podanie hasła, pozostaw to pole puste.

## <a name="list-of-language-locales"></a>Lista ustawień regionalnych języka

| **Ustawienia regionalne języka** | **Język** |
| ----------------------- | --------------- |
| cs-CZ | czeski |
| de-DE | niemiecki |
| EN US | Angielski |
| es-ES | Hiszpański |
| fr-FR | Francuski |
| IT-IT | Włoski |
| ja-JP | japoński |
| ko-KR | koreański |
| pl-PL | polski |
| pt-BR | Portugalski (Brazylia) |
| ru-RU | Rosyjski |
| tr-TR | turecki |
| zh-CN | Chiński (uproszczony) |
| zh-TW | Chiński — tradycyjny |

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także
* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
