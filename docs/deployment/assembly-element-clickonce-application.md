---
title: '&lt;zestaw&gt; elementu (aplikacji ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c72dd684092784c88b1ef6dd76d410ac9ff84d5
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
|`manifestVersion`|Wymagana. `manifestVersion` Atrybut musi być ustawiony na `1.0`.|  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<zestaw > — Element](../deployment/assembly-element-clickonce-deployment.md)
