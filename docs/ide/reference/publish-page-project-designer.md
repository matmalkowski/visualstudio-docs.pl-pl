---
title: Strona publikowania, Projektant projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c0fa900e0e3eff479e9fbbeed375b4d8b580d132
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="publish-page-project-designer"></a>Strona publikowania, Projektant projektu
**Publikowania** strony **projektanta projektu** służy do konfigurowania właściwości wdrażania ClickOnce.  
  
 Aby uzyskać dostęp do **publikowania** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** pojawia się, kliknij przycisk **publikowania** kartę.  
  
> [!NOTE]
>  Niektóre właściwości ClickOnce opisane w tym miejscu można również ustawić **PublishWizard**, dostępne z **kompilacji** menu lub przez kliknięcie przycisku **PublishWizard** przycisk na tym Strona.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Lokalizacja folderu publikowania**  
 Określa lokalizację, w którym aplikacja jest opublikowana. Może być ścieżką dysku (`C:\deploy\myapplication`), udział plików (`\\server\myapplication`), serwer FTP (`ftp://ftp.microsoft.com/myapplication`), lub witryny sieci Web (`http://www.microsoft.com/myapplication`). Należy pamiętać, że tekst musi znajdować się w **lokalizację publikowania** polu aby Przeglądaj (**...** ) przycisku do pracy.  
  
 Domyślnie jest lokalizację publikowania `http://localhost/<projectname>/` Jeśli usługi IIS są zainstalowane, lub `publish\` katalogu, jeśli nie masz zainstalowane usługi IIS. Jeśli komputer jest systemem Windows Vista, wartością domyślną jest zawsze `publish\` katalogu, niezależnie od tego, czy zostały zainstalowane usługi IIS.  
  
 **Adres URL folderu instalacji**  
 Opcjonalny. Określa witryny sieci Web, do którego użytkownicy przejdź do instalowania aplikacji. Jest to konieczne, tylko jeśli różni się od **lokalizację publikowania**, na przykład po opublikowaniu aplikacji na serwerze tymczasowym.  
  
 **Tryb i ustawienia instalacji**  
 Określa, czy aplikacja jest uruchamiana bezpośrednio z **lokalizację publikowania** (gdy **aplikacja jest dostępna online tylko** jest zaznaczone) lub jest zainstalowana i dodać do **Start**  menu i **Dodaj lub usuń programy** elementu **Panelu sterowania** (gdy **aplikacja jest dostępna w trybie offline oraz** jest zaznaczona).  
  
 W przypadku aplikacji przeglądarki sieci Web WPF **aplikacja jest dostępna w trybie offline oraz** opcja jest wyłączona, ponieważ takie aplikacje są dostępne tylko w trybie online.  
  
 **Pliki aplikacji**  
 Otwiera [aplikacji plikach — okno dialogowe](http://msdn.microsoft.com/en-us/b06dff3a-b87a-4caf-996b-7a4acf8137a8), używany do określania, jak i gdzie poszczególne pliki są zainstalowane.  
  
 **Wymagania wstępne**  
 Otwiera [wstępnie wymagane składniki — okno dialogowe](../../ide/reference/prerequisites-dialog-box.md), który służy do określania wstępnie wymagane składniki, takie jak .NET Framework, można zainstalować z aplikacji.  
  
 **Aktualizacje**  
 Otwiera [okno dialogowe aktualizacje aplikacji](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), który służy do określania zachowania aktualizacji dla aplikacji. Nie jest dostępna, gdy **aplikacja jest dostępna online tylko** jest zaznaczone.  
  
 **Opcje**  
 Otwiera [publikowania opcje — Okno dialogowe](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), który jest używany do określenia dodatkowych zaawansowane opcje publikowania.  
  
 **Opublikuj wersję**  
 Ustawia numer wersji publikowania dla tej aplikacji; Po zmianie numeru wersji aplikacji jest publikowany jako aktualizacja. Każda część wersji publikowania (**głównych**, **pomocnicza**, **kompilacji**, **poprawki**) może mieć maksymalną wartość 65355 (<xref:System.UInt16.MaxValue>), Maksymalna wartość dozwolona przez <xref:System.Version>.  
  
 Po zainstalowaniu więcej niż jedną wersję aplikacji przy użyciu technologii ClickOnce instalacji przenosi wcześniejszych wersji aplikacji do folderu o nazwie archiwum w określonej lokalizacji. Archiwizowanie starszych wersji w ten sposób przechowuje katalog instalacyjny wyczyść folderów ze starszej wersji.  
  
 **Automatycznie zwiększać poprawki przy każdej publikacji**  
 Opcjonalny. Po wybraniu tej opcji (ustawienie domyślne), **poprawki** część numeru wersji publikacji jest zwiększany o jeden zawsze opublikowanej aplikacji. Powoduje to, że aplikacja publikowane jako aktualizacja.  
  
 **Kreator publikacji**  
 Otwiera [Kreator publikowania](http://msdn.microsoft.com/en-us/fc6abebd-13d6-48e4-a567-fbc52dad0872). Kończenie pracy kreatora Publikowanie ma ten sam efekt co działa **publikowania** na **kompilacji** menu.  
  
 **Publikuj teraz**  
 Publikowanie aplikacji przy użyciu bieżących ustawień. Odpowiednikiem **Zakończ** przycisk **PublishWizard**.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Porady: Określ, gdzie programu Visual Studio kopiuje pliki](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Porady: Określanie lokalizacji, gdzie użytkownicy końcowi będą przeprowadzać z](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [Porady: Określanie łącza pomocy technicznej](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [Porady: Określanie ClickOnce w trybie Offline lub Online instalowania tryb](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [Porady: włączenie funkcji AutoStart dla instalacji z dysku CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)   
 [Porady: zestaw ClickOnce wersji publikacji](../../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Porady: automatycznie wersji publikacji ClickOnce inkrementacji](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Porady: Określanie plików publikowanych za pomocą technologii ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)   
 [Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Porady: Zarządzanie aktualizacji dla aplikacji ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)   
 [Porady: Zmienianie języka publikacji dla aplikacji ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [Porady: Określanie nazwy Menu Start dla aplikacji ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [Porady: określanie strony publikowania dla aplikacji ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../../deployment/clickonce-security-and-deployment.md)