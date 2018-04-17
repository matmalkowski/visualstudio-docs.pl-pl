---
title: '&lt;Zaktualizuj&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f0e1fdc26e285ce9b6a1fd5ecc1aa638fe909b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
|`unit`|Wymagany. Ustaw `unit` do jednej z następujących wartości:<br /><br /> -   **Godziny**<br />-   **dni korzystania z**<br />-   **Tygodni**|  
  
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
  
  