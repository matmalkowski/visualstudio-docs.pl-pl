---
title: '&lt;Zaktualizuj&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
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
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1733ac8333675975bb5d4b42dce9df3c01e5ac0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Zaktualizuj&gt; elementu (Office Development w Visual Studio)
  `update` Element Określa interwał aktualizacji sprawdza rozwiązania.  
  
## <a name="syntax"></a>Składnia  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `update` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw.  
  
 `update` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Wymagany. Włącz na jedną z następujących wartości:<br /><br /> -   **wartość true,** do sprawdzania aktualizacji.<br />-   **FALSE** zapobiegające sprawdzania aktualizacji.|  
  
 `update` Element ma następujące elementy podrzędne.  
  
### <a name="expiration"></a>wygaśnięcia  
 `expiration` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Ten element Określa interwał sprawdza rozwiązania, w którym aktualizacje.  
  
 `expiration` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maximumAge`|-Wymagane. Ustaw to na liczbę całkowitą.|  
|`unit`|Wymagany. Ustaw `unit` do jednej z następujących wartości:<br /><br /> -   **godziny**<br />-   **dni korzystania z**<br />-   **tygodni**|  
  
## <a name="example-of-always-checking-for-updates"></a>Przykład zawsze sprawdzania dostępności aktualizacji  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `update` element, który ma ustawioną wartość sprawdzać dostępność aktualizacji w rozwiązaniach pakietu Office.  
  
### <a name="code"></a>Kod  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Przykładowa konfiguracja domyślny interwał aktualizacji  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `update` elementu w manifeście aplikacji dla rozwiązań pakietu Office. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  