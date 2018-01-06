---
title: '&lt;Opis elementu&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
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
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 350a9003fcb87a6226e9ea14f7734aa40b9e62db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Opis elementu&gt; elementu (Office Development w Visual Studio)
  `description` Elementu `vstov4` przestrzeni nazw przechowuje opis rozwiązania do pakietu Office, który jest wyświetlany w oknie dialogowym dodatków modelu COM aplikacji pakietu Microsoft Office.  
  
## <a name="syntax"></a>Składnia  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 Opcjonalny. `description` Elementu jest `vstov4` przestrzeni nazw. Zawiera opis dodatku, który jest wyświetlany w oknie dialogowym dodatki modelu COM aplikacji pakietu Microsoft Office.  
  
 `description` Element nie ma atrybutów ani elementów.  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `description` element rozwiązania poziomie aplikacji wdrożone przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  