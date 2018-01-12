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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38b03c2a4980891d9a6841b24365db32ee555de4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
  
  