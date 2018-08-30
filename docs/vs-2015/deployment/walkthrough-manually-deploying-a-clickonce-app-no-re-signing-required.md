---
title: 'Wskazówki: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 85453b899501d83191016bde0edd40b4e2a96d94
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43231239"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Wskazówki: ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wskazówki: ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i że zachowuje informacje o znakowaniu](https://docs.microsoft.com/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information).  
  
Po utworzeniu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji i nadaj mu klientowi do publikowania i wdrażania, tradycyjnie miał odbiorcy do manifestu wdrażania aktualizacji i ponownie zaloguj się. Która nadal jest preferowaną metodą w większości przypadków, .NET Framework 3.5 pozwala na tworzenie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeń, które mogą być wdrażane przez klientów bez konieczności ponownie wygenerować nowy manifest wdrożenia. Aby uzyskać więcej informacji, zobacz [wdrażania ClickOnce aplikacji do testowania i obsługi serwerów produkcyjnych bez Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Po utworzeniu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji i nadać mu klientowi do publikowania i wdrażania, można użyć znakowania przez klienta lub można zachować znakowanie aplikacji. Na przykład jeśli aplikacja jest pojedynczą aplikacją własności, warto zachować znakowanie. Jeśli aplikacja jest wysoce dostosowane dla każdego klienta, możesz chcieć użyć znakowania przez klienta. .NET Framework 3.5 umożliwia zachowanie znakowanie, informacje o wydawcy i sygnatury bezpieczeństwa po zapewnieniu umożliwia wdrażanie aplikacji dla organizacji. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji ClickOnce dla innych osób, Wdróż](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  W tym instruktażu utworzysz wdrożeń ręcznie za pomocą narzędzia wiersza polecenia Mage.exe lub graficznego narzędzia MageUI.exe. Aby uzyskać więcej informacji na temat ręcznego wdrożenia, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać kroki opisane w tym przewodniku potrzebne są następujące elementy:  
  
-   Aplikacja Windows Forms, która wszystko będzie gotowe do wdrożenia. Ta aplikacja zostanie określone jako WindowsFormsApp1.  
  
-   Visual Studio lub Windows SDK.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Do wdrożenia z wieloma wdrożenia i obsługę znakowania przy użyciu Mage.exe aplikacji ClickOnce  
  
1.  Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane są Twoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] plików.  
  
2.  Utwórz katalog o nazwie po bieżąca wersja wdrożenia. Jeśli po raz pierwszy, aplikacja jest wdrażana, prawdopodobnie wybierzesz opcję **1.0.0.0**.  
  
    > [!NOTE]
    >  Wersja wdrożenie może się różnić od wersji plików aplikacji.  
  
3.  Utwórz podkatalog o nazwie **bin** i skopiuj wszystkie pliki aplikacji w tym miejscu, w tym pliki wykonywalne, zestawy, zasobów i plików danych.  
  
4.  Generuj manifest aplikacji przy użyciu wywołania programu Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Zaloguj się w manifeście aplikacji za pomocą certyfikatu cyfrowego.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generowanie manifestu wdrażania za pomocą wywołania programu Mage.exe. Domyślnie program Mage.exe spowoduje oznaczenie Twojego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia jako zainstalowanych aplikacji, tak że można uruchomić zarówno online i offline. Aby udostępnić aplikację, tylko wtedy, gdy użytkownik jest w trybie online, należy użyć `-i` argumentu o wartości `f`. Ponieważ ta aplikacja będzie móc korzystać z funkcji wdrażania w wielu, Wyklucz `-providerUrl` argumentu programu Mage.exe. (W wersjach programu .NET Framework wcześniejszych niż wersja 3.5, z wyłączeniem `-providerUrl` dla aplikacji w trybie offline spowoduje wystąpienie błędu.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Zrezygnujesz z podpisania manifestu wdrażania.  
  
8.  Podaj wszystkie pliki do klientów, którzy wdroży aplikację w jego sieci.  
  
9. W tym momencie klienta muszą podpisać manifest wdrożenia przy użyciu własnej automatycznie wygenerowany certyfikat. Na przykład klient działa w przypadku firma o nazwie Adventure Works, on wygenerowanie certyfikatu z podpisem własnym za pomocą narzędzia MakeCert.exe. Następnie narzędzie Pvk2pfx.exe połączyć plików utworzonych przez MakeCert.exe do pliku PFX, który może być przekazywany programu Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Klient używa następnie ten certyfikat do podpisania manifestu wdrażania.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Klient wdraża ją do użytkowników.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Do wdrożenia z wieloma wdrożenia i obsługę znakowania przy użyciu MageUI.exe aplikacji ClickOnce  
  
1.  Otwórz wiersz polecenia programu Visual Studio lub [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] wiersz polecenia i przejdź do katalogu, w którym będą przechowywane są Twoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] plików.  
  
2.  Utwórz podkatalog o nazwie **bin** i skopiuj wszystkie pliki aplikacji w tym miejscu, w tym pliki wykonywalne, zestawy, zasobów i plików danych.  
  
3.  Tworzenie podkatalogu nazwanym tak bieżąca wersja wdrożenia. Jeśli po raz pierwszy, aplikacja jest wdrażana, prawdopodobnie wybierzesz opcję **1.0.0.0**.  
  
    > [!NOTE]
    >  Wersja wdrożenie może się różnić od wersji plików aplikacji.  
  
4.  Przenieś \\ **bin** katalog do katalogu, który został utworzony w kroku 2.  
  
5.  Rozpocznij graficznego narzędzia MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Utwórz nowy manifest aplikacji przez wybranie **pliku**, **New**, **Manifest aplikacji** z menu.  
  
7.  Domyślny **nazwa** wprowadź nazwę i numer wersji tego wdrożenia. Ponadto należy podać wartość **wydawcy**, która będzie służyć jako nazwa folderu dla łącza skrót aplikacji w Start menu po jego wdrożeniu.  
  
8.  Wybierz **Opcje aplikacji** kartę, a następnie kliknij przycisk **Manifest aplikacji użyj uzyskać zaufania**. Spowoduje to włączenie znakowania innych firm, w tym [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
9. Wybierz **pliki** kartę, a następnie kliknij przycisk **Przeglądaj** przycisk znajdujący się obok pola tekstowego katalogu aplikacji.  
  
10. Wybierz katalog, który zawiera pliki aplikacji, które zostały utworzone w kroku 2, a następnie kliknij przycisk **OK** okno dialogowe wyboru folderu.  
  
11. Kliknij przycisk **wypełniania** przycisk, aby dodać pliki aplikacji do listy plików. Jeśli aplikacja zawiera więcej niż jeden plik wykonywalny, oznacz głównego pliku wykonywalnego dla tego wdrożenia, co aplikacja uruchamiania, wybierając **punktu wejścia** z **typ pliku** listy rozwijanej. (Jeśli aplikacja zawiera tylko jeden plik wykonywalny, MageUI.exe oznaczy go dla Ciebie.)  
  
12. Wybierz **wymagane są uprawnienia** kartę, a następnie wybierz poziom zaufania, potrzebujesz aplikacji do potwierdzenia. Wartość domyślna to **pełne zaufanie**, który będzie odpowiedni dla większości aplikacji.  
  
13. Wybierz **pliku**, **Zapisz** z menu i Zapisz w manifeście aplikacji. Zostanie wyświetlony monit podpisać manifest aplikacji, podczas zapisywania.  
  
14. Jeśli masz certyfikat przechowywany jako plik w systemie plików, użyj **logowania jako plik certyfikatu** opcji, a następnie wybierz certyfikat z systemu plików, przy użyciu wielokropka (**...** ) przycisku.  
  
     —lub—  
  
     Jeśli certyfikat jest przechowywany w magazynie certyfikatów, które są dostępne z komputera, wybierz opcję **logowania przy użyciu opcji przechowywanego certyfikatu**, a następnie wybierz certyfikat z podanej listy.  
  
15. Wybierz **pliku**, **New**, **manifestu wdrażania** z menu, aby utworzyć manifest wdrożenia, a następnie **nazwa** kartę, podaj Nazwa i numer wersji (**1.0.0.0** w tym przykładzie).  
  
16. Przełącz się do **aktualizacji** kartę, a następnie określ, jak często ma tę aplikację, aby zaktualizować. Jeśli aplikacja używa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrażania interfejsu API, aby sprawdzał dostępność aktualizacji, wyczyść pole wyboru przy opcji **ta aplikacja ma sprawdzać dostępność aktualizacji**.  
  
17. Przełącz się do **odwołania aplikacji** kartę. Można wstępnie wypełnić wszystkie wartości na tej karcie, klikając **wybierz manifestu** przycisk i wybierając polecenie manifest aplikacji utworzony w poprzednich krokach.  
  
18. Wybierz **Zapisz** i zapisanie pliku manifestu wdrożenia na dysku. Zostanie wyświetlony monit podpisać manifest aplikacji, podczas zapisywania. Kliknij przycisk **anulować** zapisanie manifestu bez rejestrowania jej.  
  
19. Podaj wszystkie pliki aplikacji do klienta.  
  
20. W tym momencie klienta muszą podpisać manifest wdrożenia przy użyciu własnej automatycznie wygenerowany certyfikat. Na przykład klient działa w przypadku firma o nazwie Adventure Works, on wygenerowanie certyfikatu z podpisem własnym za pomocą narzędzia MakeCert.exe. Następnie narzędzie Pvk2pfx.exe połączyć plików utworzonych przez MakeCert.exe do pliku PFX, który może być przekazywany do MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Wygenerowany certyfikatem klienta teraz podpisuje manifest wdrożenia przez otwarcie manifestu wdrażania w MageUI.exe, a następnie zapisz go. Gdy pojawi się okno dialogowe podpisywania, klient wybiera **logowania jako plik certyfikatu** opcji, a następnie wybierze plik PFX, został on zapisany na dysku.  
  
22. Klient wdraża ją do użytkowników.  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (manifestu narzędzie generowania i edytowania)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest narzędzie generowania i edytowania, graficzny klient)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [MakeCert.exe (narzędzie tworzenia certyfikatów)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)



