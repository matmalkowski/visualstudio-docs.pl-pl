---
title: "Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
caps.latest.revision: "25"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f7921ccebf9872f8a1f8ed79e6ee8da05d04e320
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji
Aby udostępnić aplikacji ClickOnce, należy opublikować go do udziału plików lub ścieżki, serwer FTP lub nośnik wymienny. Aplikacja zostanie opublikowana przy użyciu Kreatora publikacji; dodatkowe właściwości związanych z publikowaniem są dostępne na **publikowania** strony **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md).  
  
 Przed uruchomieniem Kreatora publikowania, należy odpowiednio ustawione właściwości publikacji. Na przykład, jeśli chcesz wyznaczyć klucza do podpisania aplikacji ClickOnce, możesz to zrobić tak **podpisywanie** strony **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Po zainstalowaniu więcej niż jedną wersję aplikacji przy użyciu technologii ClickOnce instalacji przenosi wcześniejszych wersji aplikacji do folderu o nazwie archiwum w określonej lokalizacji. Archiwizowanie starszych wersji w ten sposób przechowuje katalog instalacyjny wyczyść folderów ze starszej wersji.  
  
> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Aby opublikować do udziału plików lub ścieżki  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt aplikacji.  
  
2.  Na **kompilacji** menu, kliknij przycisk **publikowania**`Projectname`.  
  
     Zostanie wyświetlony Kreator publikowania.  
  
3.  W **gdzie chcesz opublikować aplikację?** , wprowadź prawidłowy adres serwera FTP lub prawidłową ścieżkę do pliku przy użyciu jednej z formatów pokazano, a następnie kliknij przycisk **dalej**.  
  
4.  W **użytkownicy będą instalować jak aplikacja?** wybierz lokalizację, gdzie użytkownicy przechodzą do zainstalowania aplikacji:  
  
    -   Jeśli użytkownicy będą instalować z witryny sieci Web, kliknij przycisk **z witryny sieci Web** , a następnie wprowadź adres URL, który odpowiada na ścieżkę pliku podaną w poprzednim kroku. Kliknij przycisk **Dalej**. (Ta opcja jest zazwyczaj używana w przypadku określenia adresu FTP jako lokalizację publikowania. Bezpośrednie pobierania z FTP nie jest obsługiwane. W związku z tym należy wprowadzić adres URL, w tym miejscu.)  
  
    -   Jeśli użytkownicy będą instalować aplikacji bezpośrednio z udziału plików, kliknij przycisk **z UNC ścieżki lub w udziale plików**, a następnie kliknij przycisk **dalej**. (To jest publikowanie lokalizacji c:\deploy\myapp formularza lub \\\server\myapp.)  
  
    -   Jeśli użytkownicy będą instalować z nośników wymiennych, kliknij przycisk **z dysku CD-ROM lub DVD-ROM**, a następnie kliknij przycisk **dalej**.  
  
5.  Na **aplikacja będzie dostępna w trybie offline?** kliknij odpowiednią opcję:  
  
    -   Jeśli chcesz umożliwić uruchamianie aplikacji gdy użytkownik jest odłączony od sieci, kliknij przycisk **tak, ta aplikacja stanie się dostępny online lub offline**. Skrót na **Start** menu zostanie utworzony dla aplikacji.  
  
    -   Jeśli chcesz uruchomić aplikację bezpośrednio z lokalizacji publikacji, kliknij przycisk **nie, ta aplikacja jest dostępna tylko online**. Skrót na **Start** menu nie zostanie utworzony.  
  
     Kliknij przycisk **Dalej** , aby kontynuować.  
  
6.  Kliknij przycisk **Zakończ** do publikowania aplikacji.  
  
     Stan publikowania jest wyświetlany w obszarze powiadomień stanu.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Aby opublikować z dysku CD-ROM lub DVD-ROM  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt aplikacji i kliknij przycisk **właściwości**.  
  
     **Projektanta projektu** pojawi się.  
  
2.  Kliknij przycisk **publikowania** kartę, aby otworzyć **publikowania** strony **projektanta projektu**i kliknij przycisk **Kreator publikowania** przycisku.  
  
     Zostanie wyświetlony Kreator publikowania.  
  
3.  W **gdzie chcesz opublikować aplikację?** wprowadź ścieżkę do pliku lub lokalizacji FTP gdy aplikacja zostanie opublikowana, na przykład d:\deploy. Następnie kliknij przycisk **dalej** aby kontynuować.  
  
4.  Na **użytkownicy będą instalować jak aplikacja?** kliknij przycisk z **CD-ROM lub DVD-ROM**, a następnie kliknij przycisk **dalej**.  
  
    > [!NOTE]
    >  Jeśli chcesz, aby instalacja automatyczne uruchamianie po CD-ROM zostaną wstawione do dysku, otwórz **publikowania** strony **projektanta projektu** i kliknij przycisk **opcje** przycisk, a następnie w **opcji publikowania** kreatora wybierz **instalacji na dysku CD automatycznie Rozpocznij instalację po włożeniu dysku CD**.  
  
5.  Dystrybucję aplikacji na dysku CD, warto udostępnienia aktualizacji z witryny sieci Web. W **której aplikacja będzie sprawdzać dostępność aktualizacji?** wybierz opcję aktualizacji:  
  
    -   Jeśli aplikacja będzie sprawdzać dostępność aktualizacji, kliknij przycisk **aplikacja będzie sprawdzać dostępność aktualizacji z następującej lokalizacji** i wprowadź lokalizację, w której będzie można opublikować aktualizacje. Może to być lokalizacja pliku, witryny sieci Web lub serwera FTP.  
  
    -   Jeśli aplikacja nie będzie sprawdzać dostępność aktualizacji, kliknij przycisk **aplikacji nie będzie sprawdzać dostępność aktualizacji**.  
  
     Kliknij przycisk **Dalej** , aby kontynuować.  
  
6.  Kliknij przycisk **Zakończ** do publikowania aplikacji.  
  
     Stan publikowania jest wyświetlany w obszarze powiadomień stanu.  
  
    > [!NOTE]
    >  Po zakończeniu publikowania, należy użyć dysku CD-funkcji ponownego zapisu lub DVD-funkcji ponownego zapisu do kopiowania plików z lokalizacji określonej w kroku 3 na nośnik CD lub DVD-ROM.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](/office-dev/office-dev/deploying-an-office-solution-by-using-clickonce)