---
title: '&lt;friendlyName&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <friendlyName> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 446a64c402ed9eb70b933b8c32f86426277564c5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; elementu (Office Development w Visual Studio)
  `friendlyName` Elementu `vstov4` przestrzeni nazw przechowuje nazwę wyświetlaną na liście zainstalowanych programów.  
  
## <a name="syntax"></a>Składnia  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `friendlyName` Elementu jest `vstov4` przestrzeni nazw. Wartości wyświetlane na liście zainstalowanych programów na komputerze, a następnie w oknie dialogowym dodatków COM VSTO w aplikacji pakietu Microsoft Office.  
  
 `friendlyName` Element nie ma atrybutów ani elementów podrzędnych.  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `friendlyName` element w rozwiązaniu poziomie aplikacji wdrożone przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  