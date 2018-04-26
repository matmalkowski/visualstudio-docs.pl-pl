---
title: Strona publikowania, Projektant projektu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c323fd5f5f54bbc5c53934505c43dd20a9d58591
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="publish-page-project-designer"></a>Strona publikowania, Projektant projektu
**Publikowania** strony **projektanta projektu** służy do konfigurowania właściwości wdrażania ClickOnce.

 Aby uzyskać dostęp do **publikowania** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** pojawia się, kliknij przycisk **publikowania** kartę.

> [!NOTE]
> Niektóre właściwości ClickOnce opisane w tym miejscu można również ustawić **PublishWizard**, dostępne z **kompilacji** menu lub przez kliknięcie przycisku **PublishWizard** przycisk na tym Strona.


## <a name="uielement-list"></a>Lista elementów UI
 **Lokalizacja folderu publikowania**

 Określa lokalizację, w którym aplikacja jest opublikowana. Może być ścieżką dysku (`C:\deploy\myapplication`), udział plików (`\\server\myapplication`), lub serwera FTP (`ftp://ftp.microsoft.com/myapplication`). Należy pamiętać, że tekst musi znajdować się w **lokalizację publikowania** polu aby Przeglądaj (**...** ) przycisku do pracy.

 **Adres URL folderu instalacji**

 Opcjonalna. Określa witryny sieci Web, do którego użytkownicy przejdź do instalowania aplikacji. Jest to konieczne, tylko jeśli różni się od **lokalizację publikowania**, na przykład po opublikowaniu aplikacji na serwerze tymczasowym.

 **Tryb i ustawienia instalacji**

 Określa, czy aplikacja jest uruchamiana bezpośrednio z **lokalizację publikowania** (gdy **aplikacja jest dostępna online tylko** jest zaznaczone) lub jest zainstalowana i dodać do **Start**  menu i **Dodaj lub usuń programy** elementu **Panelu sterowania** (gdy **aplikacja jest dostępna w trybie offline oraz** jest zaznaczona).

 W przypadku aplikacji przeglądarki sieci Web WPF **aplikacja jest dostępna w trybie offline oraz** opcja jest wyłączona, ponieważ takie aplikacje są dostępne tylko w trybie online.

 **Pliki aplikacji**

 Otwiera okno dialogowe pliki aplikacji, która służy do określania, jak i gdzie poszczególne pliki są zainstalowane.

 **Wymagania wstępne**

 Otwiera okno dialogowe wymagania wstępne, które służy do określania wstępnie wymagane składniki, takie jak .NET Framework, można zainstalować z aplikacji.

 **Aktualizacje**

 Otwiera okno dialogowe aktualizacji aplikacji, która jest używana do określania zachowania aktualizacji dla aplikacji. Nie jest dostępna, gdy **aplikacja jest dostępna online tylko** jest zaznaczone.

 **Opcje**

 Otwiera okno dialogowe Opcje publikowania, który jest używany do określenia dodatkowych opcji publikowania zaawansowanych.

 **Opublikuj wersję**

 Ustawia numer wersji publikowania dla tej aplikacji; Po zmianie numeru wersji aplikacji jest publikowany jako aktualizacja. Każda część wersji publikowania (**głównych**, **pomocnicza**, **kompilacji**, **poprawki**) może mieć maksymalną wartość 65355 (<xref:System.UInt16.MaxValue>), Maksymalna wartość dozwolona przez <xref:System.Version>.

 Po zainstalowaniu więcej niż jedną wersję aplikacji przy użyciu technologii ClickOnce instalacji przenosi wcześniejszych wersji aplikacji do folderu o nazwie archiwum w określonej lokalizacji. Archiwizowanie starszych wersji w ten sposób przechowuje katalog instalacyjny wyczyść folderów ze starszej wersji.

 **Automatycznie zwiększać poprawki przy każdej publikacji**

 Opcjonalna. Po wybraniu tej opcji (ustawienie domyślne), **poprawki** część numeru wersji publikacji jest zwiększany o jeden zawsze opublikowanej aplikacji. Powoduje to, że aplikacja publikowane jako aktualizacja.

 **Kreator publikacji**

 Zostanie otwarty Kreator publikowania. Kończenie pracy kreatora Publikowanie ma ten sam efekt co działa **publikowania** na **kompilacji** menu.

 **Publikuj teraz**

 Publikowanie aplikacji przy użyciu bieżących ustawień. Odpowiednikiem **Zakończ** przycisk **PublishWizard**.

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ClickOnce](../../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Instrukcje: określanie lokalizacji kopiowania plików przez program Visual Studio](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Instrukcje: określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [Instrukcje: określanie linku do pomocy technicznej](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [Instrukcje: określanie trybu offline lub online instalowania za pomocą technologii ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [Instrukcje: włączenie funkcji AutoStart dla instalacji z dysku CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [Instrukcje: ustawienie wersji publikacji technologii ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [Instrukcje: automatyczne zwiększenie wersji publikacji ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Instrukcje: określanie plików publikowanych za pomocą technologii ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Instrukcje: zarządzanie aktualizacji dla aplikacji ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [Instrukcje: zmienianie języka publikacji dla aplikacji ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [Instrukcje: określanie nazwy menu Start dla aplikacji ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [Instrukcje: określanie strony publikowania dla aplikacji ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../../deployment/clickonce-security-and-deployment.md)
