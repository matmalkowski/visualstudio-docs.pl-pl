---
title: "Porady: użycie technologii ClickOnce do wdrażania aplikacji, które można uruchamiać na wielu wersji platformy .NET | Dokumentacja firmy Microsoft"
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
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c3153b4c6808d2a79a89a10e35830ec81ba15fd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Porady: użycie technologii ClickOnce do wdrażania aplikacji uruchamianych w wielu wersjach systemu .NET Framework
Możesz wdrożyć aplikację, która jest przeznaczony dla wielu wersji platformy .NET przy użyciu technologii wdrażania ClickOnce. Wymaga to Generowanie i manifestów aplikacji i wdrażania aktualizacji.  
  
> [!NOTE]
>  Przed wprowadzeniem zmian w aplikacji, aby korzystać z wielu wersji programu .NET Framework, należy upewnić się, że aplikacja działa z wieloma wersjami programu .NET Framework. Wersja środowiska CLR różni się między [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] i .NET Framework 2.0, .NET Framework 3.0 i .NET Framework 3.5.  
  
 Ten proces wymaga wykonania następujących czynności:  
  
1.  Generowanie manifestów aplikacji i wdrażania.  
  
2.  Zmień manifest wdrażania, aby wyświetlić listę wiele wersji .NET Framework.  
  
3.  Zmianę pliku app.config, aby wyświetlić listę zgodne wersje środowiska uruchomieniowego .NET Framework.  
  
4.  Zmień manifest aplikacji, aby oznaczyć zależne zestawy jako zestawy .NET Framework.  
  
5.  Zaloguj się manifest aplikacji.  
  
6.  Zaktualizuj i podpisać manifest wdrażania.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Aby wygenerować manifestów aplikacji i wdrażania  
  
-   Użyj Kreatora publikowania lub publikowania strony projektanta projektu do publikowania aplikacji i generowanie aplikacje i pliki manifestu wdrożenia. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) lub [strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Aby zmienić manifest wdrażania, aby wyświetlić listę wiele wersji .NET Framework  
  
1.  W katalogu publikowania Otwórz plik manifestu wdrożenia za pomocą edytora XML w Visual Studio. Manifest rozmieszczenia ma rozszerzenie nazwy pliku .application.  
  
2.  Zastąp kod XML między `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` i `</compatibleFrameworks>` elementów XML, który zawiera listę obsługiwanych wersji systemu .NET Framework dla aplikacji.  
  
     W poniższej tabeli przedstawiono niektóre z dostępnych wersji .NET Framework i odpowiedni plik XML, który można dodać do manifestu wdrożenia.  
  
    |Wersja programu .NET Framework|XML|  
    |----------------------------|---------|  
    |4 klienta|\<Framework targetVersion = "4.0" profile = supportedRuntime "Client" = "4.0.30319" / >|  
    |Pełne 4|\<Framework targetVersion = "4.0" profile = "Pełny" supportedRuntime = "4.0.30319" / >|  
    |3.5 klienta|\<Framework targetVersion = "3.5" profile = supportedRuntime "Client" = "2.0.50727" / >|  
    |3.5 Pełna|\<Framework targetVersion = "3.5" profile = "Pełny" supportedRuntime = "2.0.50727" / >|  
    |3.0|\<Framework targetVersion = supportedRuntime "3.0" = "2.0.50727" / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Aby zmienić pliku app.config, aby wyświetlić listę zgodne wersje środowiska uruchomieniowego .NET Framework  
  
1.  W Eksploratorze rozwiązań Otwórz plik App.config za pomocą edytora XML w Visual Studio.  
  
2.  Zastąp (lub dodać) kod XML między `<startup>` i `</startup>` elementów XML, który zawiera listę obsługiwanych środowisk uruchomieniowych .NET Framework dla aplikacji.  
  
     W poniższej tabeli przedstawiono niektóre z dostępnych wersji .NET Framework i odpowiedni plik XML, który można dodać do manifestu wdrożenia.  
  
    |Wersja środowiska uruchomieniowego .NET framework|XML|  
    |------------------------------------|---------|  
    |4 klienta|\<Wersja supportedRuntime = sku "4.0.30319" = ". NETFramework, Version = wersja 4.0, profilu klienta = "/ >|  
    |Pełne 4|\<Wersja supportedRuntime = sku "4.0.30319" = ". NETFramework, wersja 4.0 = "/ >|  
    |3.5 Pełna|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 klienta|\<Wersja supportedRuntime = sku "v2.0.50727" = "Client" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Aby zmienić manifest aplikacji, aby oznaczyć zależne zestawy jako zestawy .NET Framework  
  
1.  W katalogu publikowania Otwórz plik manifestu aplikacji przy użyciu edytora XML w Visual Studio. Manifest rozmieszczenia ma rozszerzenie nazwy pliku manifest.  
  
2.  Dodaj `group="framework"` do kod XML zależności dla zestawów wartownik (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, i `System.Data.Entity`). Na przykład XML powinien wyglądać następująco:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Zaktualizuj numer wersji `<assemblyIdentity>` elementu Microsoft.Windows.CommonLanguageRuntime numer wersji dla programu .NET Framework, która jest najprostszy. Na przykład, jeśli aplikacja jest przeznaczony dla platformy .NET Framework 3.5 i [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], użyj 2.0.50727.0 numer wersji i XML powinien wyglądać następująco:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Aby zaktualizować i ponowne podpisywanie aplikacji i wdrażania manifesty  
  
-   Aktualizowanie i ponowne podpisywanie manifestów aplikacji i wdrażania. Aby uzyskać więcej informacji, zobacz [porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > — Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<zależności > — Element](../deployment/dependency-element-clickonce-application.md)   
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Schemat pliku konfiguracji](/dotnet/framework/configure-apps/file-schema/index)