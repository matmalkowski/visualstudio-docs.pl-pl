---
title: "Wskazówki: Ręczne wdrażanie aplikacji ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2e0035641a8ed374892060dbaabe79d808150cc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Wskazówki: ręczne wdrażanie aplikacji ClickOnce
Jeśli nie można wdrożyć za pomocą programu Visual Studio z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, lub należy korzystać z funkcji zaawansowanego wdrożenia, takich jak wdrażanie zaufanej aplikacji należy za pomocą narzędzia wiersza polecenia Mage.exe tworzenia Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty. Ten przewodnik zawiera opis sposobu tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu wiersza polecenia wersji (Mage.exe) lub wersji graficznego (MageUI.exe) generowania manifestu i narzędzia do edycji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku ma pewne warunki wstępne i opcje, które należy wybrać przed zbudowaniem wdrożenia.  
  
-   Zainstaluj Mage.exe i MageUI.exe.  
  
     Mage.exe i MageUI.exe są częścią [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Musisz mieć [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] zainstalowanych wersji lub [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] uwzględnionych w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [zestaw Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) w witrynie MSDN.  
  
-   Podaj umożliwia wdrażanie aplikacji.  
  
     W tym przewodniku założono, że jest gotowy do wdrożenia aplikacji systemu Windows. Ta aplikacja zostanie określone jako AppToDeploy.  
  
-   Określ rozkład wdrożenia.  
  
     Dostępne są następujące opcje dystrybucji: sieci Web, udziału plików lub dysku CD. Aby uzyskać więcej informacji, zobacz [zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md).  
  
-   Sprawdź, czy aplikacja wymaga podwyższonego poziomu zaufania.  
  
     Jeśli aplikacja wymaga pełnego zaufania — na przykład pełnego dostępu do systemu użytkownika — można użyć `-TrustLevel` możliwość Mage.exe ustaw tę wartość. Jeśli chcesz zdefiniować niestandardowego zestawu uprawnień dla aplikacji, należy skopiować w Internecie lub intranecie sekcji uprawnień z innego manifestu, zmodyfikuj go do własnych potrzeb i dodać go do manifestu aplikacji za pomocą edytora tekstu lub MageUI.exe. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
-   Uzyskiwanie certyfikatu Authenticode.  
  
     Należy utworzyć wdrożenia za pomocą certyfikatu Authenticode. Można wygenerować certyfikatu testowego za pomocą narzędzi Visual Studio, MageUI.exe, lub MakeCert.exe i Pvk2Pfx.exe lub certyfikat można uzyskać od urzędu certyfikacji. Jeśli chcesz użyć zaufanych wdrożenia aplikacji, musi przeprowadzić jednorazowe instalacji certyfikatu na wszystkich komputerach klienckich. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    >  Możesz też zalogować wdrożenia przy użyciu certyfikatu CNG, który można uzyskać od urzędu certyfikacji.  
  
-   Upewnij się, czy aplikacja nie ma manifestu UAC informacje.  
  
     Należy ustalić, czy aplikacja zawiera manifestu kontroli konta użytkownika (UAC) informacje, takie jak `<dependentAssembly>` elementu. Aby zbadać manifest aplikacji, można użyć Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) narzędzia.  
  
     Jeśli aplikacja zawiera manifest ze szczegółami funkcji Kontrola konta użytkownika, użytkownik musi ponownie kompilacji bez informacji o funkcji Kontrola konta użytkownika. Dla projektu C# w programie Visual Studio Otwórz właściwości projektu i wybierz kartę aplikacji. W **manifestu** listy rozwijanej wybierz **Utwórz aplikację bez manifestu**. Dla projektu Visual Basic w programie Visual Studio, otwórz właściwości projektu, wybierz kartę aplikacji, a następnie kliknij przycisk **ustawienia kontroli konta użytkownika widoku**. Otwarty plik manifestu, usunąć wszystkie elementy w pojedynczą `<asmv1:assembly>` elementu.  
  
-   Sprawdź, czy aplikacja wymaga wymagań wstępnych na komputerze klienckim.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikacje wdrożone w programie Visual Studio może obejmować programu inicjującego wymagań wstępnych instalacji (setup.exe) z wdrożeniem. W tym przewodniku tworzy dwa manifesty wymagane dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Programu inicjującego wymagań wstępnych można utworzyć przy użyciu [generatebootstrapper — zadanie](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Aby wdrożyć aplikację za pomocą narzędzia wiersza polecenia Mage.exe  
  
1.  Utwórz katalog, w którym będą przechowywane z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki wdrożenia.  
  
2.  W katalogu wdrożenia utworzone Utwórz podkatalogu wersji. Jeśli po raz pierwszy, aplikacja jest wdrażana, nazwę podkatalogu wersji **1.0.0.0**.  
  
    > [!NOTE]
    >  Wersja wdrożenie może się różnić od wersji aplikacji.  
  
3.  Kopiowanie wszystkich plików aplikacji do podkatalogu wersji, w tym pliki wykonywalne, zestawy, zasobów i plików danych. W razie potrzeby można utworzyć dodatkowe podkatalogów, które zawierają dodatkowe pliki.  
  
4.  Otwórz [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] lub polecenia programu Visual Studio Monituj i zmienić podkatalog wersji.  
  
5.  Utwórz manifest aplikacji przy użyciu wywołania do Mage.exe. Poniższa instrukcja tworzy manifest aplikacji dla kodu skompilowanego do uruchomienia z procesora Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Należy uwzględnić znaku kropki (.) po `-FromDirectory` opcja, która wskazuje bieżący katalog. Jeśli nie zostanie uwzględniony kropki (.), należy określić ścieżkę do plików aplikacji.  
  
6.  Zaloguj się przy użyciu certyfikatu Authenticode manifest aplikacji. Zastąp *mycert.pfx* ze ścieżką do pliku certyfikatu. Zastąp *haseł* hasłem do pliku certyfikatu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Aby podpisać manifest aplikacji przy użyciu certyfikatu CNG, użyj następującego polecenia. Zastąp *cngCert.pfx* ze ścieżką do pliku certyfikatu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  Przejdź do katalogu głównego katalogu wdrażania.  
  
8.  Generuj manifest wdrażania przy użyciu wywołania do Mage.exe. Domyślnie oznaczy Mage.exe Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia jako zainstalowanej aplikacji, którego nie można uruchomić zarówno online i offline. Aby udostępnić aplikację, tylko wtedy, gdy użytkownik jest w trybie online, należy użyć `-Install` opcja o wartości `false`. Jeśli użytkownik korzysta z domyślnych, a użytkownicy będą instalować aplikację z witryny sieci Web lub udziału plików, upewnij się, że wartość `-ProviderUrl` manifestu opcja wskazuje lokalizację aplikacji na serwerze sieci Web lub w udziale.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Zaloguj się przy użyciu certyfikatu Authenticode lub CNG manifest wdrażania.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     lub  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Skopiuj wszystkie pliki w katalogu wdrożenia do wdrożenia docelowego lub nośnika. Może to być folderem na witryny sieci Web lub witryny FTP, udziału plików lub dysku CD.  
  
11. Zapewnić użytkownikom adres URL, UNC lub nośnik fizyczny wymagane do zainstalowania aplikacji. Należy podać adres URL lub ścieżką UNC, należy zapewnić użytkownikom pełną ścieżkę do manifestu wdrożenia. Na przykład jeśli jest wdrażana AppToDeploy http://webserver01/ w katalogu AppToDeploy, pełna ścieżka adresu URL byłaby http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Aby wdrożyć aplikację za pomocą narzędzia graficzne MageUI.exe  
  
1.  Utwórz katalog, w którym będą przechowywane z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki wdrożenia.  
  
2.  W katalogu wdrożenia utworzone Utwórz podkatalogu wersji. Jeśli po raz pierwszy, aplikacja jest wdrażana, nazwę podkatalogu wersji **1.0.0.0**.  
  
    > [!NOTE]
    >  Wersja wdrożenia prawdopodobnie różni się od wersji aplikacji.  
  
3.  Kopiowanie wszystkich plików aplikacji do podkatalogu wersji, w tym pliki wykonywalne, zestawy, zasobów i plików danych. W razie potrzeby można utworzyć dodatkowe podkatalogów, które zawierają dodatkowe pliki.  
  
4.  Uruchom narzędzie graficzne MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Utwórz nowy manifest aplikacji przez wybranie **pliku**, **nowy**, **Manifest aplikacji** z menu.  
  
6.  Domyślny **nazwa** , wpisz nazwę i numer wersji tego wdrożenia. Określ również **procesora** wbudowanej aplikacji, takich jak x86.  
  
7.  Wybierz **pliki** karcie i kliknij przycisk wielokropka (**...** ) znajdujący się obok **katalogu aplikacji** pola tekstowego. Zostanie wyświetlone okno dialogowe Przeglądanie w poszukiwaniu folderu.  
  
8.  Wybierz podkatalogu wersji zawierającym pliki aplikacji, a następnie kliknij przycisk **OK**.  
  
9. Jeśli zostanie wdrożona w Internetowych usług informacyjnych (IIS), wybierz **podczas wypełniania Dodaj rozszerzenie .deploy do każdego pliku, który nie ma** pole wyboru.  
  
10. Kliknij przycisk **wypełnij** przycisk, aby dodać pliki aplikacji do listy plików. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, oznacz głównego pliku wykonywalnego dla tego wdrożenia jako uruchamiania aplikacji przez wybranie **punktu wejścia** z **typ pliku** listy rozwijanej. (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, MageUI.exe spowoduje oznaczenie go dla Ciebie.)  
  
11. Wybierz **uprawnienia wymagane** i wybierz poziom zaufania potrzebnych aplikacji do potwierdzenia. Wartość domyślna to **FullTrust**, który będzie odpowiedni dla większości aplikacji.  
  
12. Wybierz **pliku**, **Zapisz jako** z menu. Okno dialogowe Opcje podpisywania pojawi się monit o podpisać manifest aplikacji.  
  
13. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania z plikiem certyfikatu** i wybrać certyfikat z systemu plików za pomocą wielokropka (**...** ) przycisku. Następnie wpisz hasło certyfikatu.  
  
     —lub—  
  
     Jeżeli certyfikat znajduje się w magazynie certyfikatów dostępny z komputera, wybierz **Podpisz certyfikatem przechowywanych** opcji, a następnie wybierz certyfikat z podaną listą.  
  
14. Kliknij przycisk **OK** do podpisania manifest aplikacji. Zostanie wyświetlone okno dialogowe Zapisz jako.  
  
15. W oknie dialogowym Zapisz jako, określ katalog wersji, a następnie kliknij przycisk **zapisać**.  
  
16. Wybierz **pliku**, **nowy**, **Manifest wdrażania** z menu, aby utworzyć manifeście wdrażania.  
  
17. Na **nazwa** karcie, określ nazwę i numer wersji dla tego wdrożenia (**1.0.0.0** w tym przykładzie). Określ również **procesora** wbudowanej aplikacji, takich jak x86.  
  
18. Wybierz **opis** , a następnie określ wartości dla **wydawcy** i **Produc *** t**. (**Produktu** jest nazwa aplikacji w menu Start systemu Windows po zainstalowaniu aplikacji na komputerze klienckim w trybie offline.)  
  
19. Wybierz **opcje wdrażania** kartę i w **Start lokalizacji** tekst Określ lokalizację manifest aplikacji na serwerze sieci Web lub w udziale. Na przykład \\\myServer\myShare\AppToDeploy.application.  
  
20. Jeśli w poprzednim kroku zostało dodane rozszerzenie .deploy, wybierz również **.deploy rozszerzeniem** tutaj.  
  
21. Wybierz **opcje aktualizacji** , a następnie określ, jak często chcesz tej aplikacji do zaktualizowania. Jeśli aplikacja używa <xref:System.Deployment.Application.UpdateCheckInfo> do sprawdzania dostępności aktualizacji samego wyczyść **ta aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru.  
  
22. Wybierz **odwołania aplikacji** a następnie kliknij pozycję **wybierz manifestu** przycisku. Zostanie wyświetlone okno dialogowe otwarte.  
  
23. Wybierz utworzony wcześniej manifest aplikacji, a następnie kliknij przycisk **Otwórz**.  
  
24. Wybierz **pliku**, **Zapisz jako** z menu. Okno dialogowe Opcje podpisywania pojawi się monit logowania manifest wdrażania.  
  
25. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania z plikiem certyfikatu** i wybrać certyfikat z systemu plików za pomocą wielokropka (**...** ) przycisku. Następnie wpisz hasło certyfikatu.  
  
     —lub—  
  
     Jeżeli certyfikat znajduje się w magazynie certyfikatów dostępny z komputera, wybierz **Podpisz certyfikatem przechowywanych** opcji, a następnie wybierz certyfikat z podaną listą.  
  
26. Kliknij przycisk **OK** do podpisania manifeście wdrażania. Zostanie wyświetlone okno dialogowe Zapisz jako.  
  
27. W **Zapisz jako** okno dialogowe, Przenieś w górę jednego katalogu głównego wdrożenia, a następnie kliknij przycisk **zapisać**.  
  
28. Skopiuj wszystkie pliki w katalogu wdrożenia do wdrożenia docelowego lub nośnika. Może to być folderem na witryny sieci Web lub witryny FTP, udziału plików lub dysku CD.  
  
29. Zapewnić użytkownikom adres URL, UNC lub nośnik fizyczny wymagane do zainstalowania aplikacji. Należy podać adres URL lub ścieżką UNC, należy nadać użytkownikom pełną ścieżkę manifest wdrażania. Na przykład jeśli jest wdrażana AppToDeploy http://webserver01/ w katalogu AppToDeploy, pełna ścieżka adresu URL byłaby http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Następne kroki  
 Jeśli zajdzie potrzeba wdrożenia nowej wersji aplikacji, Utwórz nowy katalog o nazwie po nowej wersji — na przykład 1.0.0.1—and skopiować nowych plików aplikacji do nowego katalogu. Następnie należy wykonać poprzednie kroki, aby utworzyć i nowych manifest aplikacji i zaktualizuj i zalogują się manifest wdrażania. Należy wskazać nowszej wersji tego samego w obu Mage.exe `-New` i `-Update` wywołań, jako [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tylko aktualizuje nowsze wersje najważniejszych całkowitą lewej. Jeśli używasz MageUI.exe, można zaktualizować manifest wdrażania, otwierając go, wybierając **odwołanie do aplikacji** kartę, klikając pozycję **wybierz manifestu** przycisk, a następnie wybierając zaktualizowane manifest aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Generowanie manifestu i edytowania narzędzia, klient grafiki)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)