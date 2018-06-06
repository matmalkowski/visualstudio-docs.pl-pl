---
title: 'Porady: Określ adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02dfd64d7a6b3a2ffae49e5693bdac8ebdf2ad0f
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815652"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Porady: określanie adresu URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kilka wymagań wstępnych, które muszą być dostępne na komputerze klienckim, aby przetestować wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do uruchomienia aplikacji. Te zależności obejmują wymagana minimalna wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], wersja systemu operacyjnego i dowolne zestawy, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], jednak nie może zainstalować żadnego z tych wymagań wstępnych. Jeśli nie ma wymagań wstępnych, po prostu przerywa instalacji i wyświetla okno dialogowe wyjaśniający, dlaczego nie można zainstalować.  
  
 Istnieją dwie metody instalacji wstępnie wymaganego oprogramowania. Można zainstalować je za pomocą aplikacji programu inicjującego. Alternatywnie można określić adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników, która będzie wyświetlana użytkownikom w oknie dialogowym, jeśli nie ma wymagań wstępnych. Strona odwołuje się ten adres URL może zawierać łącza do instrukcje dotyczące instalowania wymaganiem wstępnym. Jeśli aplikacja nie określa adresu URL pomocy technicznej dla indywidualnych wymagań wstępnych [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Wyświetla adres URL pomocy technicznej, określona w manifeście wdrażania aplikacji jako całości, jeśli jest zdefiniowana.  
  
 Gdy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe i MageUI.exe wszystkie służy do generowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, żaden z tych narzędzi bezpośrednio obsługują określania adresu URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników. W tym dokumencie opisano sposób modyfikowania danego wdrożenia manifest aplikacji i manifest wdrażania, aby uwzględnić je obsługuje adresy URL.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Określanie adresu URL pomocy technicznej dla indywidualnych wstępnie wymaganego składnika  
  
1.  Otwórz plik manifestu aplikacji ( `.manifest` pliku) dla sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w edytorze tekstów.  
  
2.  Wstępnie wymaganego składnika systemu operacyjnego można dodać `supportUrl` atrybutu `dependentOS` elementu:  
  
    ```xml  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Wymaganiem wstępnym dla określonej wersji środowiska CLR, można dodać `supportUrl` atrybutu `dependentAssembly` wpis, który określa typowe zależności aparatu plików wykonywalnych języka:  
  
    ```xml  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Wymaganiem wstępnym dla zestawu, który musi być preinstalowany w globalnej pamięci podręcznej zestawów, ustaw `supportUrl` dla `dependentAssembly` element, który określa wymagany zestaw:  
  
    ```xml  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Opcjonalna. Dla aplikacji przeznaczonych dla platformy .NET Framework 4, otwórz plik manifestu wdrożenia ( `.application` pliku) dla sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji w edytorze tekstów.  
  
6.  Wymaganie wstępne platformy .NET Framework 4, można dodać `supportUrl` atrybutu `compatibleFrameworks` elementu:  
  
    ```xml  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Po ręcznie zmieniono manifest aplikacji, należy ponownie podpisać manifest aplikacji przy użyciu certyfikatu cyfrowego, a następnie zaktualizować i ponownie podpisać manifest rozmieszczenia również. Narzędzia Mage.exe lub MageUI.exe zestawu SDK do wykonania tego zadania jako ponownego generowania tych plików przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usuwa ręcznej zmiany. Aby uzyskać więcej informacji na temat używania Mage.exe do ponownego podpisania manifestów, zobacz [porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Adres URL pomocy technicznej nie jest wyświetlana w oknie dialogowym, jeśli aplikacja jest oznaczona do uruchamiania w częściowej relacji zaufania.  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Wskazówki: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > — Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Wstępnie wymagane składniki wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)