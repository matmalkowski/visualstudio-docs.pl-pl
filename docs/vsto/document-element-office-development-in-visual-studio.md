---
title: '&lt;dokument&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 48995b4a40d4e67b0c0e2e44d66545c4c90dd26b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;dokument&gt; elementu (Office Development w Visual Studio)
  `document` Elementu `vstov4` przestrzeni nazw są przechowywane informacje dotyczące dostosowywania na poziomie dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 Wymagane tylko w przypadku dostosowań na poziome dokumentu. `document` Elementu jest `vstov4` przestrzeni nazw. `document` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`solutionId`|Wymagany. Identyfikator GUID używany przez Visual Studio Tools dla pakietu Office runtime do jednoznacznego identyfikowania rozwiązania na poziomie dokumentu. Ta wartość jest przechowywana jako _AssemblyLocation właściwość niestandardowego dokumentu. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości niestandardowego dokumentu](../vsto/custom-document-properties-overview.md).|  
  
 `document`nie ma elementów podrzędnych.  
  
## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `document` element w poziomie dokumentu rozwiązania pakietu Office wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  