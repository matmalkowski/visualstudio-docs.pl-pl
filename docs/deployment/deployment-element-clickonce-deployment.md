---
title: '&lt;wdrożenie&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 80bcba10c350cc61d582acb80321fc75e02f16ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;wdrożenie&gt; elementu (wdrażania ClickOnce)
Identyfikuje atrybuty używane do wdrażania aktualizacji i zagrożeń do systemu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `deployment` Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v1` przestrzeni nazw. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`install`|Wymagany. Określa, czy ta aplikacja definiuje obecności w systemie Windows **Start** menu w Panelu sterowania **Dodaj lub usuń programy** aplikacji. Prawidłowe wartości to `true` i `false`. Jeśli `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] najnowszą wersję tej aplikacji będzie zawsze uruchamiana z sieci, a nie rozpoznaje `subscription` elementu.|  
|`minimumRequiredVersion`|Opcjonalny. Określa minimalną wersję tej aplikacji, które można uruchomić na komputerze klienckim. Jeśli numer wersji aplikacji jest mniejsza niż numer wersji podany w manifeście wdrażania, aplikacja nie będzie działać. Numery wersji należy określić w formacie `N.N.N.N`, gdzie `N` jest liczbą całkowitą bez znaku. Jeśli `install` atrybutu `false`, `minimumRequiredVersion` nie może być ustawiony.|  
|`mapFileExtensions`|Opcjonalny. Domyślnie `false`. Jeśli `true`, wszystkie pliki w ramach wdrożenia musi mieć rozszerzenie .deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Usuwa to rozszerzenie tych plików zaraz po pobraniu ich z serwera sieci Web. W przypadku publikowania aplikacji za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], automatycznie doda to rozszerzenie do wszystkich plików. Ten parametr umożliwia wszystkie pliki w obrębie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia mają być pobrane z serwera sieci Web, która blokuje transmisji plików w rozszerzeniach "unsafe", takie jak .exe.|  
|`disallowUrlActivation`|Opcjonalny. Domyślnie `false`. Jeśli `true`, uniemożliwia uruchomienie klikając adres URL lub wprowadzić adres URL w programie Internet Explorer zainstalowanych aplikacji. Jeśli `install` atrybut nie jest obecny, ten atrybut jest ignorowany.|  
|`trustURLParameters`|Opcjonalny. Domyślnie `false`. Jeśli `true`, umożliwia adres URL, który zawiera parametrów ciągu zapytania, które są przekazywane do aplikacji, wiele podobnych argumenty wiersza polecenia są przekazywane do wiersza polecenia aplikacji. Aby uzyskać więcej informacji, zobacz [porady: pobieranie informacji o ciągu kwerendy w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Jeśli `disallowUrlActivation` atrybutu `true`, `trustUrlParameters` musi być wyłączone w manifeście, lub jawnie ustawiona na `false`.|  
  
 `deployment` Element zawiera także następujące elementy podrzędne.  
  
## <a name="subscription"></a>Subskrypcji  
 Opcjonalny. Zawiera `update` elementu. `subscription` Element nie ma żadnych atrybutów. Jeśli `subscription` element nie istnieje, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja nigdy nie będą skanować pod kątem aktualizacji. Jeśli `install` atrybutu `deployment` jest element `false`, `subscription` element został zignorowany, ponieważ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, który jest zawsze uruchamiany z sieci korzysta z najnowszej wersji.  
  
## <a name="update"></a>Aktualizacja  
 Wymagany. Ten element jest elementem podrzędnym `subscription` element i zawiera jedną `beforeApplicationStartup` lub `expiration` elementu. `beforeApplicationStartup` i `expiration` nie można określić w tym samym manifest wdrażania.  
  
 `update` Element nie ma żadnych atrybutów.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Opcjonalny. Ten element jest elementem podrzędnym `update` elementu i nie ma żadnych atrybutów. Gdy `beforeApplicationStartup` element istnieje, że aplikacja będzie zablokowane, gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sprawdza dostępność aktualizacji, jeśli klient jest w trybie online. Jeśli ten element nie istnieje, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] najpierw rozpocznie skanowanie aktualizacji na podstawie wartości określonej dla `expiration` elementu. `beforeApplicationStartup` i `expiration` nie można określić w tym samym manifest wdrażania.  
  
## <a name="expiration"></a>wygaśnięcia  
 Opcjonalny. Ten element jest elementem podrzędnym `update` elementu, a nie ma elementów podrzędnych. `beforeApplicationStartup` i `expiration` nie można określić w tym samym manifest wdrażania. Podczas sprawdzania aktualizacji i zaktualizowaną wersję zostanie wykryte, nowa wersja buforuje podczas wykonywania istniejącą wersję. Nowa wersja instaluje przy następnym uruchomieniu z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
 `expiration` Elementu obsługuje następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maximumAge`|Wymagany. Określa, ile lat bieżąca aktualizacja powinny stać się przed aplikacji wykonuje sprawdzenie dostępności aktualizacji. Jednostka czasu jest określany przez `unit` atrybutu.|  
|`unit`|Wymagany. Identyfikuje jednostki czasu dla `maximumAge`. Prawidłowe jednostki są `hours`, `days`, i `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentprovider —  
 Dla programu .NET Framework 2.0, ten element jest wymagany, jeśli manifest rozmieszczenia zawiera `subscription` sekcji. Dla programu .NET Framework 3.5 lub nowszego oraz ten element jest opcjonalny i domyślnie zostanie ustawiona do serwera i ścieżki pliku, w którym zostało wykryte manifest wdrażania.  
  
 Ten element jest elementem podrzędnym `deployment` element a ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`codebase`|Wymagany. Określa lokalizację, jako jednolity identyfikator zasobów (URI), manifestu rozmieszczenia, która jest używana do aktualizowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten element umożliwia również przekazywanie aktualizacji lokalizacje instalacji przy użyciu dysku CD. Musi być prawidłowym identyfikatorem URI.|  
  
## <a name="remarks"></a>Uwagi  
 Można skonfigurować sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji do skanowania w poszukiwaniu aktualizacji uruchamianie skanowania w poszukiwaniu aktualizacji po uruchomieniu lub nigdy nie sprawdzaj, czy są aktualizacje. Do skanowania w poszukiwaniu aktualizacji podczas uruchamiania, upewnij się, że `beforeApplicationStartup` element istnieje w ramach `update` elementu. Po uruchomieniu skanowania pod kątem aktualizacji, upewnij się, że `expiration` element istnieje w ramach `update` elementu i podano interwały aktualizacji.  
  
 Aby wyłączyć sprawdzanie dostępności aktualizacji, należy usunąć `subscription` elementu. Po określeniu w manifeście rozmieszczenia nie skanowania pod kątem aktualizacji, można nadal ręcznie sprawdzania dostępności aktualizacji przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metody.  
  
 Aby uzyskać więcej informacji dotyczących sposobu deploymentprovider — odnosi się do aktualizacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje `deployment` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania. W przykładzie użyto `deploymentProvider` elementu, aby wskazać lokalizację preferowanych aktualizacji.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)