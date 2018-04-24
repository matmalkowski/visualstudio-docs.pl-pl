---
title: Tworzenie w trybie Offline instalację programu Visual Studio
description: Dowiedz się, jak zainstalować program Visual Studio w trybie offline.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d70005a7e876b299e93ac2891ce6774a6300792
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Tworzenie w trybie offline instalację programu Visual Studio 2017 r.

Firma Microsoft zaprojektowane Instalator Visual Studio 2017 działają poprawnie w różnych warunków, sieci i komputera.

- Nowy model oparte na obciążeniu oznacza, że należy pobrać daleko mniejszej niż w poprzednich wersjach programu Visual Studio: małego 300 MB do najmniejszego instalacji;
- W porównaniu do ogólnego "ISO" lub plik zip, możemy pobrać tylko pakiety, które są potrzebne dla maszyny. Na przykład firma Microsoft nie pobieraj plików 64-bitowych, jeśli nie są potrzebne;
- W procesie instalacji spróbujemy trzy technologie różnych pobierania (WebClient, Usługa BITS i WinInet) aby zminimalizować zakłócenia oprogramowania antywirusowego i serwera proxy;
- Pliki, musisz zainstalować program Visual Studio są dystrybuowane w sieci dostarczania globalnych, dlatego firma Microsoft może udostępnić je użytkownikom z lokalnego serwera.

Zalecamy wypróbowanie [Instalator sieci web programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)&mdash;naszym zdaniem znajdziesz ją dobrej obsługi.

 > [!div class="button"]
 > [Pobierz program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)

Jeśli chcesz zainstalować w trybie offline, ponieważ połączenie z Internetem jest niedostępne lub zawodnych, patrz [zainstalować program Visual Studio 2017 o niskiej przepustowości lub zawodnych w środowiskach sieci](../install/install-vs-inconsistent-quality-network.md). Polecenie umożliwia utworzenie lokalnej pamięci podręcznej plików trzeba wykonać instalację w trybie offline. Ten proces zastępuje pliki ISO dostępne w poprzednich wersjach.

> [!NOTE]
> Jeśli jesteś administratorem przedsiębiorstwa, który chce wykonać wdrożenie programu Visual Studio 2017 klienckich stacjach roboczych, które są zaporą z siecią Internet, zobacz nasze [Tworzenie instalacji sieciowej programu Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) i [Zainstalować certyfikaty wymagane do instalacji w trybie offline program Visual Studio](../install/install-certificates-for-visual-studio-offline.md) stron.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)
