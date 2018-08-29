---
title: Zainstaluj na o niskiej przepustowości zawodnych środowiskach sieciowych lub | Dokumentacja firmy Microsoft
description: Dowiedz się, jak używać Instalatora programu Visual Studio, gdy sieć jest tymczasowy lub masz o niskiej przepustowości i w jaki sposób można użyć wiersza polecenia, aby pobrać instalacji plików.
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: b273efb06e7b2e70617d28dcafc85735bcfb1fd1
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138803"
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Instalowanie programu Visual Studio 2017 w powolnych lub zawodnych środowiskach sieciowych

Zalecamy wypróbowanie Instalatora sieci web programu Visual Studio&mdash;uważamy, że znajdziesz ją dobre środowisko w większości sytuacji.

 > [!div class="button"]
 > [Pobierz program Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

Jednak jeśli połączenie z Internetem jest niedostępne lub niestabilne, można użyć wiersza polecenia do utworzenia lokalnej pamięci podręcznej pliki potrzebne do ukończenia instalacji w trybie offline. Poniżej przedstawiono sposób.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce wykonać wdrożenie programu Visual Studio 2017 do sieci z stacje robocze klienta, które są zaporą z Internetu, zobacz nasze [Tworzenie instalacji sieciowej programu Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) i [Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio](../install/install-certificates-for-visual-studio-offline.md) stron.

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Krok 1 — pobieranie program inicjujący programu Visual Studio

Rozpocznij, pobierając program inicjujący Instalatora programu Visual Studio dla Twojej wybranej wersji programu Visual Studio.

Plik Instalatora&mdash;lub dokładniej, plik inicjujący&mdash;dopasować, lub być podobne do jednej z następujących czynności.

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Krok 2 — Tworzenie instalacji lokalnej pamięci podręcznej

Musi mieć połączenie internetowe, aby ukończyć ten krok. Aby utworzyć lokalne układ, otwórz wiersz polecenia i użyj jednego z poleceń w poniższych przykładach. Podane tutaj przykłady zakładają, że korzystasz z wersji Community programu Visual Studio; Dostosuj polecenia odpowiednie dla posiadanej wersji.

- Dla sieci web platformy .NET i programowanie aplikacji klasycznych dla platformy .NET Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- .NET — aplikacje klasyczne i rozwoju pakietu Office Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Do tworzenia klasycznych aplikacji języka C++ Uruchom polecenie:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Aby utworzyć pełną układ lokalnych ze wszystkich funkcji (spowoduje to przejście przez długi czas&mdash;mamy _wiele_ funkcji!), uruchom:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Jeśli chcesz zainstalować język inny niż angielski, zmień `en-US` ustawienia regionalne na liście u dołu tej strony. Użyj tego [listą składników i dostępności obciążeń](workload-and-component-ids.md) dodatkowo dostosować pamięci podręcznej instalacji zgodnie z potrzebami.

> [!IMPORTANT]
> Pełny układ programu Visual Studio 2017 wymaga co najmniej 35 GB miejsca na dysku i może zająć trochę czasu, aby pobrać. Zobacz [Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) informacji na temat sposobu tworzenia układu z tylko te składniki, aby zainstalować.

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>Krok 3 — Instalowanie programu Visual Studio z lokalnej pamięci podręcznej

> [!TIP]
> Po uruchomieniu z pamięci podręcznej lokalnej instalacji, Instalator używa lokalnej wersji każdej z tych plików. Jednak jeśli zostanie wybrana podczas instalacji składników, które nie znajdują się w pamięci podręcznej, staramy się je pobrać z Internetu.

Aby upewnić się, czy należy zainstalować tylko pliki, które zostały pobrane, należy użyć tych samych opcji wiersza polecenia, które zostało użyte do utworzenia pamięci podręcznej układu. Na przykład, jeśli utworzono układ pamięci podręcznej za pomocą następującego polecenia:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Użyj tego polecenia, aby uruchomić instalację:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Jeśli wystąpi błąd, że podpis jest nieprawidłowy, należy zainstalować zaktualizowane certyfikaty. Otwórz folder certyfikatów w pamięci podręcznej w trybie offline. Kliknij dwukrotnie plik certyfikatu, a następnie kliknij za pomocą Kreatora Menedżera certyfikatów. Jeśli pojawi się pytanie o hasło, pozostaw to pole puste.

## <a name="list-of-language-locales"></a>Listę ustawień regionalnych języka

| **Ustawienia regionalne na język** | **Język** |
| ----------------------- | --------------- |
| cs-CZ | czeski |
| de-DE. | niemiecki |
| pl pl | Angielski |
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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 obciążeń i składników identyfikatorów](workload-and-component-ids.md)
