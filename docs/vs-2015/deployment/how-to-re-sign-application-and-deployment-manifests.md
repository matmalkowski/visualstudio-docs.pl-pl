---
title: 'Porady: ponowne podpisywanie aplikacji i manifestów wdrożenia | Dokumentacja firmy Microsoft'
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
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d16dfa86c4620868178687bcde3323f3e55b31b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633706"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Porady: ponowne podpisywanie aplikacji i manifestów wdrożenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](https://docs.microsoft.com/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
Po wprowadzeniu zmian do właściwości wdrożenia w manifeście aplikacji dla aplikacji Windows Forms, aplikacji Windows Presentation Foundation (xbap) lub rozwiązań pakietu Office, musisz ją ponownie podpisać zarówno aplikację i manifesty wdrożenia za pomocą certyfikat. Ten proces pozwala upewnić się, że zmodyfikowany pliki nie są zainstalowane na komputerach użytkowników końcowych.  
  
 Inny scenariusz, w którym może ponownie podpisać manifesty jest, gdy Twoi klienci wymagają podpisać aplikację i manifesty wdrożenia za pomocą ich własnych certyfikatów.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Ponowne podpisywanie aplikacji i wdrażania manifestów  
 W tej procedurze założono, że zostały już wprowadzone zmiany do pliku manifestu aplikacji (manifest). Aby uzyskać więcej informacji, zobacz [porady: Zmienianie właściwości wdrożenia](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Ponowne podpisywanie aplikacji i wdrażania manifestów za pomocą Mage.exe  
  
1.  Otwórz **Visual Studio Command Prompt** okna.  
  
2.  Zmień katalogi na folder, który zawiera pliki manifestu, które chcesz się zalogować.  
  
3.  Wpisz następujące polecenie, aby utworzyć plik manifestu aplikacji. Zamień ManifestFileName nazwę pliku manifestu, plus rozszerzenie. Zamień certyfikatu względną lub w pełni kwalifikowana ścieżka do pliku certyfikatu, a następnie zastąp hasło hasło dla certyfikatu.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacja formularza Windows lub aplikacji Windows Presentation Foundation przeglądarki. Certyfikaty tymczasowe, utworzone przez program Visual Studio nie są zalecane dla wdrożenia w środowisku produkcyjnym.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrażania, zastępując nazw zastępczych, jak w poprzednim kroku.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji programu Windows Forms lub aplikacja przeglądarki Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Opcjonalnie, skopiuj manifest wdrażania wzorca (publikowanie\\*appname*.application) do katalogu wdrażania wersji (pliki publish\Application\\*appname*_ *wersji*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Aktualizowanie i ponowne podpisywanie aplikacji i manifestów wdrożenia  
 Ta procedura zakłada, że już wprowadzono zmiany do aplikacji (manifest) plik manifestu, ale czy istnieją inne pliki, które zostały zaktualizowane. Podczas aktualizacji plików skrótu, który reprezentuje plik również musi zostać zaktualizowany.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aktualizowanie i ponowne podpisywanie aplikacji i wdrażania manifestów za pomocą Mage.exe  
  
1.  Otwórz **Visual Studio Command Prompt** okna.  
  
2.  Zmień katalogi na folder, który zawiera pliki manifestu, które chcesz się zalogować.  
  
3.  Usuń rozszerzenie pliku .deploy z plików w folderze Publikuj dane wyjściowe.  
  
4.  Wpisz następujące polecenie, aby zaktualizować manifest aplikacji przy użyciu nowych skrótów do zaktualizowanych plików i podpisać plik manifestu aplikacji. Zamień ManifestFileName nazwę pliku manifestu, plus rozszerzenie. Zamień certyfikatu względną lub w pełni kwalifikowana ścieżka do pliku certyfikatu, a następnie zastąp hasło hasło dla certyfikatu.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacja formularza Windows lub aplikacji Windows Presentation Foundation przeglądarki. Certyfikaty tymczasowe, utworzone przez program Visual Studio nie są zalecane dla wdrożenia w środowisku produkcyjnym.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrażania, zastępując nazw zastępczych, jak w poprzednim kroku.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji programu Windows Forms lub aplikacja przeglądarki Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Powrót do plików, należy dodać rozszerzenie pliku .deploy, z wyjątkiem pliki manifestu aplikacji i wdrożenia.  
  
7.  Opcjonalnie, skopiuj manifest wdrażania wzorca (publikowanie\\*appname*.application) do katalogu wdrażania wersji (pliki publish\Application\\*appname*_ *wersji*).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Porady: włączenie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Porady: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Instrukcje: konfigurowanie funkcji zaufanego monitowania technologii ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)



