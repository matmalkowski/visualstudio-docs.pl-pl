---
title: 'Wskazówki: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0584aac376345bc508e5f2088decd45b8c64783b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Wskazówki: ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu
Po utworzeniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i nadaj mu klientowi do publikowania i wdrażania, klient miał tradycyjnie manifest wdrażania aktualizacji i ponownie zaloguj się. Gdy nadal jest preferowaną metodą w większości przypadków, .NET Framework 3.5 umożliwia utworzenie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń, które mogą być wdrażane przez klientów bez konieczności ponownego generowania nowych manifest wdrażania. Aby uzyskać więcej informacji, zobacz [wdrażania ClickOnce aplikacji do testowania i obsługi serwerów produkcyjnych bez Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).  
  
 Po utworzeniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i nadaj klientowi do publikowania i wdrażania, można użyć znakowania klienta lub zachować znakowanie aplikacji. Na przykład jeśli aplikacja jest pojedynczą aplikacją zastrzeżonych, można zachować znakowanie. Aplikacja wysokiej jest dostosowany do każdego klienta, można użyć znakowania klienta. .NET Framework 3.5 umożliwia możesz zachować znakowanie, informacje o wydawcy i podpis zabezpieczeń po uruchomieniu aplikacji w organizacji do wdrożenia. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji ClickOnce dla innych użytkowników, na stronę wdrażanie](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  W tym przewodniku możesz tworzyć wdrożeń ręcznie za pomocą narzędzia wiersza polecenia Mage.exe lub graficzne narzędzie MageUI.exe. Aby uzyskać więcej informacji na temat wdrożenia ręczne, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać kroki opisane w tym przewodniku są potrzebne następujące elementy:  
  
-   Aplikacji formularzy systemu Windows, który chcesz wdrożyć. Ta aplikacja zostanie określone jako WindowsFormsApp1.  
  
-   Visual Studio lub zestawu SDK systemu Windows.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Do wdrażania aplikacji ClickOnce z wieloma wdrożenia i obsługę znakowania przy użyciu Mage.exe  
  
1.  Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików.  
  
2.  Utwórz katalog o nazwie po bieżącej wersji wdrożenia. Jeśli aplikacja jest wdrażana po raz pierwszy, prawdopodobnie wybierzesz **1.0.0.0**.  
  
    > [!NOTE]
    >  Wersja wdrożenie może się różnić od wersji plików aplikacji.  
  
3.  Utwórz podkatalog o nazwie **bin** i skopiuj wszystkie pliki aplikacji, w tym pliki wykonywalne, zestawy, zasobów i plików danych.  
  
4.  Generuj manifest aplikacji przy użyciu wywołania do Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Zaloguj się przy użyciu certyfikatu cyfrowego manifestu aplikacji.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generuj manifest wdrażania przy użyciu wywołania do Mage.exe. Domyślnie oznaczy Mage.exe Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia jako zainstalowanej aplikacji, którego nie można uruchomić zarówno online i offline. Aby udostępnić aplikację, tylko wtedy, gdy użytkownik jest w trybie online, należy użyć `-i` argumentu o wartości `f`. Od tej aplikacji będzie korzystać z wielu funkcji wdrażania, Wyklucz `-providerUrl` argument Mage.exe. (W wersjach programu .NET Framework przed w wersji 3.5, z wyłączeniem `-providerUrl` dla aplikacji w trybie offline spowoduje błąd.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Manifest rozmieszczenia nie zalogować.  
  
8.  Podaj wszystkie pliki do klienta, który będzie wdrażanie aplikacji w swojej sieci.  
  
9. W tym momencie klienta należy podpisać manifest wdrażania z własnej automatycznie wygenerowany certyfikat. Na przykład klient działa w przypadku firma Adventure Works, on wygenerować certyfikat z podpisem własnym za pomocą narzędzia MakeCert.exe. Następnie użyj narzędzia Pvk2pfx.exe, aby połączyć plików utworzonych przez MakeCert.exe do pliku PFX, które mogą zostać przekazane do Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Klient używa obok ten certyfikat do podpisania manifestu wdrożenia.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Klient wdraża aplikację dla użytkowników.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Do wdrażania aplikacji ClickOnce z wieloma wdrożenia i obsługę znakowania przy użyciu MageUI.exe  
  
1.  Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików.  
  
2.  Utwórz podkatalog o nazwie **bin** i skopiuj wszystkie pliki aplikacji, w tym pliki wykonywalne, zestawy, zasobów i plików danych.  
  
3.  Utwórz podkatalog o nazwie po bieżącej wersji wdrożenia. Jeśli aplikacja jest wdrażana po raz pierwszy, prawdopodobnie wybierzesz **1.0.0.0**.  
  
    > [!NOTE]
    >  Wersja wdrożenie może się różnić od wersji plików aplikacji.  
  
4.  Przenieś \\ **bin** katalogu do katalogu, który został utworzony w kroku 2.  
  
5.  Uruchom narzędzie graficzne MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Utwórz nowy manifest aplikacji przez wybranie **pliku**, **nowy**, **Manifest aplikacji** z menu.  
  
7.  Domyślny **nazwa** wprowadź nazwę i numer wersji tego wdrożenia. Ponadto należy podać wartość **wydawcy**, która będzie służyć jako nazwa folderu aplikacji łącza skrótu w Start menu po jej wdrożeniu.  
  
8.  Wybierz **Opcje aplikacji** i kliknij polecenie **Manifest aplikacji użyj dla zaufania informacji**. Spowoduje to włączenie innych firm znakowanie dla tego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
9. Wybierz **pliki** i kliknij polecenie **Przeglądaj** przycisk obok pola tekstowego katalogu aplikacji.  
  
10. Wybierz katalog, który zawiera pliki aplikacji, które zostały utworzone w kroku 2, a następnie kliknij przycisk **OK** w oknie dialogowym Wybieranie folderu.  
  
11. Kliknij przycisk **wypełnij** przycisk, aby dodać pliki aplikacji do listy plików. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, oznacz głównego pliku wykonywalnego dla tego wdrożenia jako uruchamiania aplikacji przez wybranie **punktu wejścia** z **typ pliku** listy rozwijanej. (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, MageUI.exe spowoduje oznaczenie go dla Ciebie.)  
  
12. Wybierz **uprawnienia wymagane** i wybierz poziom zaufania należy aplikacji do potwierdzenia. Wartość domyślna to **pełne zaufanie**, który będzie odpowiedni dla większości aplikacji.  
  
13. Wybierz **pliku**, **zapisać** z menu, a następnie zapisz manifest aplikacji. Pojawi się monit do podpisania manifestu aplikacji podczas zapisywania.  
  
14. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania jako plik certyfikatu** opcji, a następnie wybierz certyfikat z systemu plików, za pomocą wielokropka (**...** ) przycisku.  
  
     —lub—  
  
     Jeśli certyfikat jest przechowywany w magazynie certyfikatów, które są dostępne z komputera, wybierz **logowania z opcją przechowywanego certyfikatu**i wybierz certyfikat z listy.  
  
15. Wybierz **pliku**, **nowy**, **Manifest wdrażania** z menu, aby utworzyć manifeście wdrażania, a następnie na **nazwa** karcie, podaj Nazwa i numer wersji (**1.0.0.0** w tym przykładzie).  
  
16. Przełącz się do **aktualizacji** , a następnie określ, jak często tej aplikacji do zaktualizowania. Jeśli aplikacja używa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania interfejsu API, aby wyszukać aktualizacje, wyczyść pole wyboru **ta aplikacja ma sprawdzać dostępność aktualizacji**.  
  
17. Przełącz się do **odwołania aplikacji** kartę. Można wstępnie wypełnić wszystkie wartości na tej karcie, klikając **wybierz manifestu** przycisk i wybierając manifest aplikacji utworzony w poprzednich krokach.  
  
18. Wybierz **zapisać** i zapisać manifestu wdrożenia na dysku. Pojawi się monit do podpisania manifestu aplikacji podczas zapisywania. Kliknij przycisk **anulować** można zapisać manifestu bez podpisu.  
  
19. Podaj wszystkie pliki aplikacji do klienta.  
  
20. W tym momencie klienta należy podpisać manifest wdrażania z własnej automatycznie wygenerowany certyfikat. Na przykład klient działa w przypadku firma Adventure Works, on wygenerować certyfikat z podpisem własnym za pomocą narzędzia MakeCert.exe. Następnie użyj narzędzia Pvk2pfx.exe, aby połączyć plików utworzonych przez MakeCert.exe do pliku PFX, które mogą zostać przekazane do MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Wygenerowany certyfikatem klienta teraz podpisuje manifest wdrażania, otwórz manifest wdrażania MageUI.exe i zapisać go. Gdy pojawi się okno dialogowe podpisywania, klient wybiera **logowania jako plik certyfikatu** opcji i wybiera pliku PFX, został on zapisany na dysku.  
  
22. Klient wdraża aplikację dla użytkowników.  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Generowanie manifestu i edytowania narzędzia, klient grafiki)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)