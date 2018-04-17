---
title: Manifest wdrażania ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 5664c3505c44cb519365e7f15344d390eeebac0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="clickonce-deployment-manifest"></a>Manifest wdrożenia ClickOnce
Manifest rozmieszczenia jest plik XML, który opisuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, w tym identyfikacji bieżącego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wersji aplikacji do wdrożenia.  
  
 Manifesty wdrożenia ma następujące elementy i atrybuty.  
  
|Element|Opis|Atrybuty|  
|-------------|-----------------|----------------|  
|[\<zestaw > — Element](../deployment/assembly-element-clickonce-deployment.md)|Wymagany. Element najwyższego poziomu.|`manifestVersion`|  
|[\<element assemblyIdentity > — Element](../deployment/assemblyidentity-element-clickonce-deployment.md)|Wymagany. Identyfikuje dla manifest aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<Opis elementu > — Element](../deployment/description-element-clickonce-deployment.md)|Wymagany. Określa informacje o aplikacji, które pozwala utworzyć obecności powłoki i **Dodaj lub usuń programy** w Panelu sterowania.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<wdrożenie > — Element](../deployment/deployment-element-clickonce-deployment.md)|Opcjonalny. Identyfikuje atrybuty używane do wdrażania aktualizacji i zagrożeń do systemu.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<compatibleFrameworks > — Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)|Wymagany. Określa wersje programu .NET Framework, której tę aplikację można instalować i uruchamiać.|`SupportUrl`|  
|[\<zależności > — Element](../deployment/dependency-element-clickonce-deployment.md)|Wymagany. Identyfikuje wersji aplikacji do zainstalowania wdrożenia i lokalizacja manifestu aplikacji.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisheridentity — > — Element](../deployment/publisheridentity-element-clickonce-deployment.md)|Wymagany dla podpisanych manifestów. Zawiera informacje o wydawcy, który podpisał tego manifestu wdrożenia.|`Name`<br /><br /> `issuerKeyHash`|  
|[\<Podpis > — Element](../deployment/signature-element-clickonce-deployment.md)|Opcjonalny. Zawiera informacje potrzebne do cyfrowego podpisywania manifestu tego wdrożenia.|Brak|  
|[\<customErrorReporting > — Element](../deployment/customerrorreporting-element-clickonce-deployment.md)|Opcjonalny. Określa identyfikator URI do wyświetlenia, gdy wystąpi błąd.|Identyfikator URI|  
  
## <a name="remarks"></a>Uwagi  
 Określa plik manifestu wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji, łącznie z bieżącej wersji i inne ustawienia wdrażania. Odwołuje się manifest aplikacji, opisujący bieżącej wersji aplikacji i wszystkich plików znajdujących się we wdrożeniu.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Lokalizacja pliku  
 Plik manifestu wdrożenia odwołuje się do manifestu właściwej aplikacji z bieżącą wersją aplikacji. Po udostępnieniu nowej wersji wdrożenia aplikacji, należy zaktualizować manifest wdrażania, aby odwołać się do nowego manifest aplikacji.  
  
 Plik manifestu wdrożenia musi być silna i może również zawierać certyfikaty na potrzeby weryfikacji wydawcy.  
  
## <a name="file-name-syntax"></a>Składnia nazwy pliku  
 Nazwa pliku manifestu wdrożenia musi mieć rozszerzenie .application.  
  
## <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje manifest wdrażania.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
...  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)