---
title: Manifesty aplikacji dla rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 622d2066f6acfe1fdf344f06ee5bbbbdf3d9b410
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="application-manifests-for-office-solutions"></a>Manifesty aplikacji dla rozwiązań pakietu Office
  Manifest aplikacji jest plik XML, który opisuje zestawy, które są ładowane do rozwiązania Microsoft Office. Użyj narzędzia Microsoft Office development w Visual Studio [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schematu manifestu aplikacji zdefiniowane w [manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest) odwołania.  
  
 Manifesty aplikacji dla rozwiązań pakietu Office należy użyć następującego [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] elementów i atrybutów.  
  
|Element|Opis|Atrybuty|  
|-------------|-----------------|----------------|  
|[&#60;zestaw&#62; elementu &#40;aplikacji ClickOnce&#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|Wymagana. Element najwyższego poziomu.|**ManifestVersion**|  
|[&#60;element assemblyIdentity&#62; elementu &#40;aplikacji ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|Wymagana. Identyfikuje [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] podstawowego zestawu aplikacji.|**Nazwa**<br /><br /> **Wersja**<br /><br /> **publicKeyToken**<br /><br /> **Element ProcessorArchitecture**<br /><br /> **Język**|  
|[&#60;trustinfo —&#62; elementu &#40;aplikacji ClickOnce&#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|Identyfikuje wymagania dotyczące zabezpieczeń aplikacji.|Brak|  
|[&#60;punkt wejścia&#62; elementu &#40;aplikacji ClickOnce&#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|Wymagana. Określa punkt wejścia kodu aplikacji do wykonania.|**Nazwa**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|  
|[&#60;zależności&#62; elementu &#40;aplikacji ClickOnce&#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|Wymagana. Identyfikuje poszczególne zależności wymagane do uruchomienia aplikacji. Opcjonalnie określa zestawy, które muszą być preinstalowany.|Brak|  
|[&#60;plik&#62; elementu &#40;aplikacji ClickOnce&#41;](/visualstudio/deployment/file-element-clickonce-application)|Wymagana. Identyfikuje każdego pliku z systemem innym niż zestawu, który jest używany przez aplikację. Może zawierać składnika modelu COM (Object) izolacji dane skojarzone z plikiem.|**Nazwa**<br /><br /> **Rozmiar**|  
  
 Manifesty aplikacji dla rozwiązań pakietu Office ma następujący element w `co.v1` przestrzeni nazw.  
  
```xml  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>   
```  
  
 Te manifesty aplikacji ma również następujące elementy i atrybuty w `vstav3` przestrzeni nazw.  
  
```xml  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customizations>  
      <customization>  
      </customization>  
    </customizations>  
  </application  
</addIn>  
```  
  
|Element|Opis|Atrybuty|  
|-------------|-----------------|----------------|  
|[&#60;customHostSpecified&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Wymagana. Oznacza manifest w szczególności jako rozwiązania do pakietu Office.|Brak|  
|[&#60;Dodatek&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Wymagana. Przechowuje punkty wejścia do jednej przestrzeni nazw.|Brak|  
|[&#60;entrypointscollection —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Wymagana. Grupuje wszystkie zestawy dla jednego lub więcej rozwiązań pakietu Office.|**id**|  
|[&#60;punkty wejścia&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Wymagana. Grupy wszystkie zestawy do uruchamiania rozwiązań pakietu Office.|Brak|  
|[&#60;punkt wejścia&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Wymagana. Określa zestaw, do uruchamiania w rozwiązaniach pakietu Office.|**class**<br /><br /> **kontrakt**|  
|[&#60;Zaktualizuj&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Wymagana. Konfiguruje aktualizacje dla rozwiązania.|**włączone**<br /><br /> **wygaśnięcia**|  
|[&#60;postactions —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Opcjonalna. Grupy wszystkie po wdrożeniu akcje, które uruchamiane po zainstalowaniu rozwiązań pakietu Office.|Brak|  
|[&#60;postAction&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Opcjonalna. Określa akcję po wdrożeniu.|Brak|  
|[&#60;postactiondata —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Opcjonalna. Konfiguruje danych dotyczących akcji po wdrożeniu.|Brak|  
|[&#60;Aplikacja&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Wymagana. Koduje informacje specyficzne dla aplikacji do jednego węzła.|Brak|  
|[&#60;Dostosowywanie&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Wymagana. Przechowuje wszystkie informacje specyficzne dla hosta aplikacji w oddzielnych przestrzeni nazw.|Brak|  
|[&#60;Dostosowywanie&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Wymagana. Przechowuje informacje specyficzne dla hosta aplikacji w oddzielnych przestrzeni nazw.|**Xmlns**|  
|[&#60;dokument&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązania na poziomie dokumentu. Przechowuje informacje dotyczące dostosowywania.|**solutionId**|  
|[&#60;appAddin&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązania na poziomie aplikacji. Przechowuje informacje dotyczące dostosowywania.|**Aplikacji**<br /><br /> **LoadBehavior**<br /><br /> **Nazwa klucza**|  
|[&#60;friendlyName&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Opcjonalna. Przechowuje nazwę dodatku VSTO, który pojawia się na liście zainstalowanych dodatków VSTO.|Brak|  
|[&#60;Opis elementu&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Wymagany tylko dla dodatków VSTO. Przechowuje opis wyświetlany na liście zainstalowanych programów.|Brak|  
|[&#60;formregions —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Wymagany tylko dla dodatków VSTO programu Outlook, które obejmują regionów formularzy.|Brak|  
|[&#60;formRegion&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Wymagany tylko dla dodatków VSTO programu Outlook, które obejmują regionów formularzy.|**Nazwa**|  
|[&#60;vstoruntime —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Wymagana. W tym artykule opisano określonej wersji programu Visual Studio Tools for Office runtime, która jest obsługiwana przez rozwiązanie Office.|**Zlecenia**<br /><br /> **Wersja**<br /><br /> **supportUrl**|  
  
## <a name="remarks"></a>Uwagi  
 Można ręcznie edytować aplikację i manifesty wdrożenia w rozwiązaniach pakietu Office. Następnie należy ponownie podpisać aplikację i manifesty wdrożenia przy użyciu Generowanie manifestu i narzędzia do edycji (*mage.exe* i *mageui.exe*). Aby uzyskać więcej informacji, zobacz [porady: ponowne podpisywanie manifestów aplikacji i wdrażania](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="file-location"></a>Lokalizacja pliku  
 Manifest aplikacji jest specyficzny dla jednej wersji rozwiązania. Z tego powodu manifesty aplikacji powinny być przechowywane oddzielnie od manifesty wdrożenia. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umieszcza pliki określonej wersji w podkatalogu o nazwie po skojarzonej wersji w *pliki aplikacji* podkatalogu w folderze publikowania.  
  
## <a name="file-name-syntax"></a>Składnia nazwy pliku  
 Nazwa pliku manifestu aplikacji powinna być pełną nazwę i rozszerzenie aplikacji określonych w **assemblyIdentity** elementu, a następnie manifest rozszerzenia. Na przykład manifest aplikacji, która odwołuje się do *OutlookAddIn1.dll* dostosowywania użyje następującą składnię nazwy pliku.  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>Zobacz także  
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  