---
title: '&lt;zestaw&gt; elementu (aplikacji ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: c94d70f2be28a6a420d683335c99ee0466a52114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;zestaw&gt; elementu (aplikacji ClickOnce)
Element najwyższego poziomu dla manifest aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `assembly` Element jest elementem głównym i jest wymagana. Musi być pierwszego elementu zawartych w niej `assemblyIdentity` elementu. Liczba elementów manifestu musi być w jednym z następujących przestrzeni nazw:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Elementy podrzędne zestawu również musi być w tych obszarach nazw przez dziedziczenie lub znaczników.  
  
 `assembly` Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`manifestVersion`|Wymagany. `manifestVersion` Atrybut musi być ustawiony na `1.0`.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `assembly` elementu w manifeście aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<zestaw > — Element](../deployment/assembly-element-clickonce-deployment.md)