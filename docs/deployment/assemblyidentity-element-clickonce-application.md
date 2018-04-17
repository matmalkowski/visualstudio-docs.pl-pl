---
title: '&lt;element assemblyIdentity&gt; elementu (aplikacji ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 86a9aedcd3f21d4dbc1cc4f09106421542b188f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;element assemblyIdentity&gt; elementu (aplikacji ClickOnce)
Identyfikuje aplikację wdrożone w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `assemblyIdentity` Element jest wymagany. Nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Określa nazwę aplikacji.<br /><br /> Jeśli `Name` zawiera znaki specjalne, takie jak pojedyncze lub podwójne cudzysłowy, aplikacja może uaktywnienie nie powiodło się.|  
|`Version`|Wymagany. Określa numer wersji aplikacji w następującym formacie: `major.minor.build.revision`|  
|`publicKeyToken`|Opcjonalny. Określa ciąg szesnastkowy 16 znaków, który reprezentuje ostatnich 8 bajtów `SHA-1` wartość klucza publicznego, pod którą jest podpisany aplikacji lub zestawu skrótu. Klucz publiczny, który jest używany do podpisywania katalogu musi wynosić 2048 bitów lub większej.<br /><br /> Podpisywanie zestawu jest zalecane, ale opcjonalne, ten atrybut jest wymagany. Jeśli zestaw jest podpisany, możesz skopiować wartości z podpisem własnym zestawu lub użyj wartości "zastępczego" z samych zer.|  
|`processorArchitecture`|Wymagany. Określa procesora. Prawidłowe wartości to `msil` dla wszystkich procesorów `x86` dla 32-bitowej wersji systemu Windows `IA64` dla 64-bitowej wersji systemu Windows i `Itanium` na procesorach Itanium 64-bitowym.|  
|`language`|Wymagany. Identyfikuje części dwóch kodów języków (na przykład `en-US`) zestawu. Tego elementu jest `asmv2` przestrzeni nazw. Jeśli zostanie określona, wartością domyślną jest `neutral`.|  
  
## <a name="examples"></a>Przykłady  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `assemblyIdentity` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Kod  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<element assemblyIdentity > — Element](../deployment/assemblyidentity-element-clickonce-deployment.md)