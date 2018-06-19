---
title: '&lt;element assemblyIdentity&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 802d94063d2a4351ecc627c9426edb458d2543c2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31559832"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;element assemblyIdentity&gt; elementu (wdrażania ClickOnce)
Określa podstawowy zestaw z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `assemblyIdentity` Element jest wymagany. Nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagana. Identyfikuje zrozumiałą nazwę wdrożenia w celach informacyjnych.<br /><br /> Jeśli `name` zawiera znaki specjalne, takie jak pojedyncze lub podwójne cudzysłowy, aplikacja może uaktywnienie nie powiodło się.|  
|`version`|Wymagana. Określa numer wersji zestawu, w następującym formacie: `major.minor.build.revision`.<br /><br /> Ta wartość muszą być zwiększane w manifeście zaktualizowane w celu wyzwolenia aktualizacji aplikacji.|  
|`publicKeyToken`|Wymagana. Określa 16-znakowym ciągiem szesnastkowym reprezentujący ostatnich 8 bajtów wartość skrótu SHA-1 klucza publicznego, pod którym manifest wdrażania jest podpisany. Klucz publiczny, który jest używany do podpisywania musi wynosić 2048 bitów lub większej.<br /><br /> Podpisywanie zestawu jest zalecane, ale opcjonalne, ten atrybut jest wymagany. Jeśli zestaw jest podpisany, możesz skopiować wartości z podpisem własnym zestawu lub użyj wartości "zastępczego" z samych zer.|  
|`processorArchitecture`|Wymagana. Określa procesora. Prawidłowe wartości to `msil` dla wszystkich procesorów `x86` dla 32-bitowej wersji systemu Windows `IA64` dla 64-bitowej wersji systemu Windows i `Itanium` na procesorach Itanium 64-bitowym.|  
|`type`|Wymagana. Aby zapewnić zgodność z technologii side-by-side instalacji systemu Windows. Jest to jedyna wartość dozwolonych `win32`.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `assemblyIdentity` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania. Ten przykładowy kod jest częścią większego przykładu udostępnionego dla [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) tematu.  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<element assemblyIdentity > — Element](../deployment/assemblyidentity-element-clickonce-application.md)