---
title: 'Porady: użycie technologii ClickOnce do wdrażania aplikacji, które można uruchamiać na wielu wersji programu .NET Framework | Dokumentacja firmy Microsoft'
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
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c9ee766472adf215a29852f776b566997df2e28b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677168"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Porady: użycie technologii ClickOnce do wdrażania aplikacji uruchamianych w wielu wersjach systemu .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: użycie ClickOnce, aby wdrożyć aplikacje, mogą być uruchamiane przy użyciu wielu wersji programu .NET Framework](https://docs.microsoft.com/visualstudio/deployment/how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-dotnet-framework).  
  
Można wdrożyć aplikację, który jest przeznaczony dla wielu wersji programu .NET Framework przy użyciu technologii wdrażania ClickOnce. Wymaga to Generowanie i zaktualizuj manifesty aplikacji i wdrożenia.  
  
> [!NOTE]
>  Zanim zmienisz aplikacji pod kątem wielu wersji programu .NET Framework, należy upewnić się, że aplikacja działa z wieloma wersjami programu .NET Framework. Wersja środowiska uruchomieniowego języka wspólnego różni się między [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] a .NET Framework 2.0, .NET Framework 3.0 i .NET Framework 3.5.  
  
 Ten proces wymaga wykonania następujących kroków:  
  
1.  Generowanie manifestów aplikacji i wdrożenia.  
  
2.  Zmień manifest wdrożenia, aby wyświetlić listę wiele wersji .NET Framework.  
  
3.  Zmień plik app.config, aby wyświetlić listę niezgodne wersje środowiska uruchomieniowego .NET Framework.  
  
4.  Zmień manifest aplikacji, aby oznaczyć zestawów zależnych jako zestawy .NET Framework.  
  
5.  Zaloguj się w manifeście aplikacji.  
  
6.  Zaktualizuj i podpisać manifest wdrożenia.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Aby wygenerować manifesty aplikacji i wdrożenia  
  
-   Użyj Kreatora publikacji lub na stronie publikowania w Projektancie projektu do publikowania aplikacji i wygenerować aplikację i plikach manifestu wdrażania. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) lub [strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Aby zmienić manifestu wdrażania, aby wyświetlić listę wiele wersji .NET Framework  
  
1.  W katalogu publikowania otwarcie manifestu wdrażania za pomocą edytora XML w programie Visual Studio. Manifest wdrażania ma rozszerzenie nazwy pliku .application.  
  
2.  Zastąp kod XML między `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` i `</compatibleFrameworks>` elementy z danymi XML, który zawiera listę obsługiwanych wersji systemu .NET Framework dla aplikacji.  
  
     W poniższej tabeli przedstawiono niektóre z dostępnych wersji oprogramowania .NET Framework i odpowiedni plik XML, który można dodać do manifestu wdrażania.  
  
    |Wersja programu .NET Framework|XML|  
    |----------------------------|---------|  
    |4 klienta|\<Framework targetVersion = "4.0" profile = supportedRuntime "Client" = "4.0.30319" / >|  
    |Pełne 4|\<Framework targetVersion = "4.0" profile = supportedRuntime "Pełnej" = "4.0.30319" / >|  
    |3.5 klient|\<Framework targetVersion = "3.5" profile = supportedRuntime "Client" = "2.0.50727" / >|  
    |3.5 pełne|\<Framework targetVersion = "3.5" profile = supportedRuntime "Pełnej" = "2.0.50727" / >|  
    |3.0|\<Framework targetVersion = supportedRuntime "3.0" = "2.0.50727" / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Aby zmienić plik app.config, aby wyświetlić listę niezgodne wersje środowiska uruchomieniowego .NET Framework  
  
1.  W Eksploratorze rozwiązań Otwórz plik App.config przy użyciu edytora XML w programie Visual Studio.  
  
2.  Zastąp (lub dodać) kod XML między `<startup>` i `</startup>` elementów za pomocą XML, który zawiera listę obsługiwanych środowiska uruchomieniowego .NET Framework dla aplikacji.  
  
     W poniższej tabeli przedstawiono niektóre z dostępnych wersji oprogramowania .NET Framework i odpowiedni plik XML, który można dodać do manifestu wdrażania.  
  
    |Wersja środowiska uruchomieniowego .NET framework|XML|  
    |------------------------------------|---------|  
    |4 klienta|\<Wersja supportedRuntime = jednostki sku "v4.0.30319" = ". NETFramework, Version = w wersji 4.0, profilu klienta = "/ >|  
    |Pełne 4|\<Wersja supportedRuntime = jednostki sku "v4.0.30319" = ". NETFramework, Version = v4.0 "/ >|  
    |3.5 pełne|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 klient|\<Wersja supportedRuntime = jednostki sku "v2.0.50727" = "Client" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Aby zmienić manifest aplikacji, aby oznaczyć zestawów zależnych jako zestawy .NET Framework  
  
1.  W katalogu publikowania Otwórz manifest aplikacji za pomocą edytora XML w programie Visual Studio. Manifest wdrażania ma rozszerzenie nazwy pliku manifest.  
  
2.  Dodaj `group="framework"` na kod XML zależności dla zestawów wartownik (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, i `System.Data.Entity`). Na przykład kod XML powinien wyglądać następująco:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Zaktualizuj numer wersji `<assemblyIdentity>` elementu dla Microsoft.Windows.CommonLanguageRuntime numer wersji dla programu .NET Framework, która jest najprostszy. Na przykład, jeśli aplikacja jest przeznaczony dla .NET Framework 3.5 i [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], użyj 2.0.50727.0 numer wersji i XML powinien wyglądać podobnie do poniższego:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizowanie i ponowne podpisywanie aplikacji i wdrażania manifestów  
  
-   Aktualizowanie i ponowne podpisywanie manifestów aplikacji i wdrożenia. Aby uzyskać więcej informacji, zobacz [porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<zależność > Element](../deployment/dependency-element-clickonce-application.md)   
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Schemat pliku konfiguracji](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)



