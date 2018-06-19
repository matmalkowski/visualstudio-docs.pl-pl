---
title: '&lt;Opis elementu&gt; elementu (Office development w Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9fcdac1e950d98394b5703322f40dd1823b246f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265118"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Opis elementu&gt; elementu (Office development w Visual Studio)
  `description` Elementu `vstov4` przestrzeni nazw przechowuje opis rozwiązania do pakietu Office, który jest wyświetlany w oknie dialogowym dodatków modelu COM aplikacji pakietu Microsoft Office.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 Opcjonalna. `description` Elementu jest `vstov4` przestrzeni nazw. Zawiera opis dodatku, który jest wyświetlany w oknie dialogowym dodatki modelu COM aplikacji pakietu Microsoft Office.  
  
 `description` Element nie ma atrybutów ani elementów.  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `description` element rozwiązania poziomie aplikacji wdrożone przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```xml  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  