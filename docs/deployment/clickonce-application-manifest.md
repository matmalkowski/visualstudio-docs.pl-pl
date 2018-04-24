---
title: Manifest aplikacji ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52d5a288444b1e98df75e6748fa31176b27211b0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-application-manifest"></a>Manifest aplikacji ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji jest plik XML, który opisuje aplikacji, która jest wdrażane za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifesty aplikacji ma następujące elementy i atrybuty.  
  
|Element|Opis|Atrybuty|  
|-------------|-----------------|----------------|  
|[\<zestaw > — Element](../deployment/assembly-element-clickonce-application.md)|Wymagana. Element najwyższego poziomu.|`manifestVersion`|  
|[\<element assemblyIdentity > — Element](../deployment/assemblyidentity-element-clickonce-application.md)|Wymagana. Określa podstawowy zestaw z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustinfo — > — Element](../deployment/trustinfo-element-clickonce-application.md)|Identyfikuje wymagania dotyczące zabezpieczeń aplikacji.|Brak|  
|[\<entryPoint > — Element](../deployment/entrypoint-element-clickonce-application.md)|Wymagana. Określa punkt wejścia kodu aplikacji.|`name`|  
|[\<zależności > — Element](../deployment/dependency-element-clickonce-application.md)|Wymagana. Identyfikuje poszczególne zależności wymagane do uruchomienia aplikacji. Opcjonalnie określa zestawy, które muszą być preinstalowany.|Brak|  
|[\<Plik > — Element](../deployment/file-element-clickonce-application.md)|Opcjonalna. Identyfikuje każdego pliku nonassembly, który jest używany przez aplikację. Może zawierać składnika modelu COM (Object) izolacji dane skojarzone z plikiem.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation > — Element](../deployment/fileassociation-element-clickonce-application.md)|Opcjonalna. Określa rozszerzenie pliku do skojarzenia z aplikacją.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Pliku manifestu aplikacji identyfikuje aplikacje wdrażane za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], zobacz [zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Lokalizacja pliku  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji jest specyficzny dla jednej wersji wdrożenia. Z tego powodu powinny być przechowywane oddzielnie od manifesty wdrożenia. Typowe Konwencji jest umieszczanie ich w podkatalogu o nazwie po skojarzonej wersji.  
  
 Manifest aplikacji musi być zawsze podpisany przed ich wdrożeniem. Jeśli ręcznie zmienisz manifest aplikacji, należy użyć mage.exe ponownie podpisać manifest aplikacji, zaktualizowania manifest wdrażania i ponowne podpisywanie manifestu wdrożenia. Aby uzyskać więcej informacji, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="file-name-syntax"></a>Składnia nazwy pliku  
 Nazwa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliku manifestu aplikacji powinna być pełną nazwę i rozszerzenie aplikacji określonych w `assemblyIdentity` elementu, a następnie manifest rozszerzenia. Na przykład manifest aplikacji, która odwołuje się do aplikacji Example.exe użyje następującą składnię nazwy pliku.  
  
 `example.exe.manifest`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje manifest aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
...  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)