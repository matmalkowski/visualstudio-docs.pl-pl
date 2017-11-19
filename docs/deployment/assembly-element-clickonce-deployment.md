---
title: "&lt;zestaw&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 90def1bc4d824c6fdfd597ec8beb4b1f18f9e008
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;zestaw&gt; elementu (wdrażania ClickOnce)
Element najwyższego poziomu dla manifest wdrażania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `assembly` Element jest elementem głównym i jest wymagana. Musi być pierwszego elementu zawartych w niej `assemblyIdentity` elementu. Manifestu elementy muszą się znajdować w następujących przestrzeni nazw: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, i `http://www.w3.org/2000/09/xmldsig#`. Elementy podrzędne zestawu również musi być w tych obszarach nazw przez dziedziczenie lub znaczników.  
  
 `assembly` Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`manifestVersion`|Wymagany. Ten atrybut musi mieć ustawioną `1.0`.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `assembly` elementu w manifeście wdrażania dla aplikacji wdrożone przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego dla [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) tematu.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
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
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<zestaw > — Element](../deployment/assembly-element-clickonce-application.md)