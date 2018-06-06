---
title: '&lt;Zaktualizuj&gt; elementu (Office development w Visual Studio)'
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
ms.openlocfilehash: c51a7f79165d421f080d05088418d02a48680b66
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767611"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Zaktualizuj&gt; elementu (Office development w Visual Studio)
  `update` Element Określa interwał aktualizacji sprawdza rozwiązania.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
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
|`enabled`|Wymagana. Włącz na jedną z następujących wartości:<br /><br /> -   **wartość true,** do sprawdzania aktualizacji.<br />-   **FALSE** zapobiegające sprawdzania aktualizacji.|  
  
 `update` Element ma następujące elementy podrzędne.  
  
### <a name="expiration"></a>wygaśnięcia  
 `expiration` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Ten element Określa interwał sprawdza rozwiązania, w którym aktualizacje.  
  
 `expiration` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maximumAge`|   Wymagana. Ustaw to na liczbę całkowitą.|  
|`unit`|Wymagana. Ustaw `unit` do jednej z następujących wartości:<br /><br /> -   **Godziny**<br />-   **dni korzystania z**<br />-   **Tygodni**|  
  
## <a name="example-of-always-checking-for-updates"></a>Przykład zawsze sprawdzania dostępności aktualizacji  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `update` element, który ma ustawioną wartość sprawdzać dostępność aktualizacji w rozwiązaniach pakietu Office.  
  
### <a name="code"></a>Kod  
  
```xml  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Przykładowa konfiguracja domyślny interwał aktualizacji  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `update` elementu w manifeście aplikacji dla rozwiązań pakietu Office. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```xml  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  