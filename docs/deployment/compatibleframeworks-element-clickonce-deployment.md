---
title: '&lt;compatibleFrameworks&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d406ecf058bf1c570b57ed8f50815cc3d9378cbe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31560781"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; elementu (wdrażania ClickOnce)
Określa wersje programu .NET Framework, której tę aplikację można instalować i uruchamiać.  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) nie obsługuje `compatibleFrameworks` elementu podczas zapisywania manifest aplikacji, która została już podpisana z certyfikatu przy użyciu [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Zamiast tego należy użyć [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
## <a name="syntax"></a>Składnia  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `compatibleFrameworks` Element jest wymagany dla obiektu docelowego manifesty wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] udostępniane przez środowisko uruchomieniowe [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] lub nowszym. `compatibleFrameworks` Elementu zawiera jeden lub więcej `framework` elementów, które Określ wersje programu .NET Framework, na których można uruchomić tej aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Środowiska uruchomieniowego uruchomi aplikację na pierwszy dostępny `framework` na tej liście.  
  
 W poniższej tabeli wymieniono atrybut który `compatibleFrameworks` obsługuje elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`S``upportUrl`|Opcjonalna. Określa adres URL, w którym można pobrać preferowanych zgodnej wersji programu .NET Framework.|  
  
## <a name="framework"></a>szablon  
 Wymagana. W poniższej tabeli przedstawiono atrybuty który `framework` obsługuje elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`targetVersion`|Wymagana. Określa numer wersji docelowej platformy .NET Framework.|  
|`profile`|Wymagana. Określa profil docelowej platformy .NET Framework.|  
|`supportedRuntime`|Wymagana. Określa numer wersji środowiska uruchomieniowego skojarzone z docelowej platformy .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład `compatibleFrameworks` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania. To wdrożenie może działać na [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Można również uruchomić na [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ponieważ jest on podzbiorem [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)