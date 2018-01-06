---
title: "Manifesty aplikacji dla rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
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
helpviewer_keywords: application manifests [Office development in Visual Studio]
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 847d42015b28f3d2ad0e2e2eb48c5b1ce060ab14
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="application-manifests-for-office-solutions"></a>Manifesty aplikacji dla rozwiązań Office
  Manifest aplikacji jest plik XML, który opisuje zestawy, które są ładowane do rozwiązania Microsoft Office. Użyj narzędzia Microsoft Office development w Visual Studio [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schematu manifestu aplikacji zdefiniowane w [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest) odwołania.  
  
 Manifesty aplikacji dla rozwiązań pakietu Office należy użyć następującego [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] elementów i atrybutów.  
  
|Element|Opis|Atrybuty|  
|-------------|-----------------|----------------|  
|[&#60; zestawu &#62; Element &#40; &#41; aplikacji ClickOnce](/visualstudio/deployment/assembly-element-clickonce-deployment)|Wymagany. Element najwyższego poziomu.|`manifestVersion`|  
|[&#60; assemblyIdentity &#62; Element &#40; &#41; aplikacji ClickOnce](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|Wymagany. Identyfikuje [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] podstawowego zestawu aplikacji.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60; trustinfo — &#62; Element &#40; &#41; aplikacji ClickOnce](/visualstudio/deployment/trustinfo-element-clickonce-application)|Identyfikuje wymagania dotyczące zabezpieczeń aplikacji.|Brak|  
|[&#60; entryPoint &#62; Element &#40; &#41; aplikacji ClickOnce](/visualstudio/deployment/entrypoint-element-clickonce-application)|Wymagany. Określa punkt wejścia kodu aplikacji do wykonania.|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60; zależności &#62; Element &#40; &#41; aplikacji ClickOnce](/visualstudio/deployment/dependency-element-clickonce-deployment)|Wymagany. Identyfikuje poszczególne zależności wymagane do uruchomienia aplikacji. Opcjonalnie określa zestawy, które muszą być preinstalowany.|Brak|  
|[&#60; plik &#62; Element &#40; &#41; aplikacji ClickOnce](/visualstudio/deployment/file-element-clickonce-application)|Wymagany. Identyfikuje każdego pliku z systemem innym niż zestawu, który jest używany przez aplikację. Może zawierać składnika modelu COM (Object) izolacji dane skojarzone z plikiem.|`name`<br /><br /> `size`|  
  
 Manifesty aplikacji dla rozwiązań pakietu Office ma następujący element w `co.v1` przestrzeni nazw.  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>   
```  
  
 Te manifesty aplikacji ma również następujące elementy i atrybuty w `vstav3` przestrzeni nazw.  
  
```  
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
|[&#60; customHostSpecified &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Wymagany. Oznacza manifest w szczególności jako rozwiązania do pakietu Office.|Brak|  
|[&#60; addin &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Wymagany. Przechowuje punkty wejścia do jednej przestrzeni nazw.|Brak|  
|[&#60; entrypointscollection — &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Wymagany. Grupuje wszystkie zestawy dla jednego lub więcej rozwiązań pakietu Office.|`id`|  
|[&#60; punkty wejścia &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Wymagany. Grupy wszystkie zestawy do uruchamiania rozwiązań pakietu Office.|Brak|  
|[&#60; entryPoint &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Wymagany. Określa zestaw, do uruchamiania w rozwiązaniach pakietu Office.|`class`<br /><br /> `contract`|  
|[&#60; aktualizację &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/update-element-office-development-in-visual-studio.md)|Wymagany. Konfiguruje aktualizacje dla rozwiązania.|`enabled`<br /><br /> `expiration`|  
|[&#60; postactions — &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Opcjonalny. Grupy wszystkie po wdrożeniu akcje, które uruchamiane po zainstalowaniu rozwiązań pakietu Office.|Brak|  
|[&#60; postAction &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Opcjonalny. Określa akcję po wdrożeniu.|Brak|  
|[&#60; postactiondata — &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Opcjonalny. Konfiguruje danych dotyczących akcji po wdrożeniu.|Brak|  
|[&#60; aplikacji &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/application-element-office-development-in-visual-studio.md)|Wymagany. Koduje informacje specyficzne dla aplikacji do jednego węzła.|Brak|  
|[&#60; dostosowania &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Wymagany. Przechowuje wszystkie informacje specyficzne dla hosta aplikacji w oddzielnych przestrzeni nazw.|Brak|  
|[&#60; dostosowania &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Wymagany. Przechowuje informacje specyficzne dla hosta aplikacji w oddzielnych przestrzeni nazw.|`xmlns`|  
|[&#62; &#60; dokumentu Element &#40; programowanie Office w Visual Studio &#41;](../vsto/document-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązania na poziomie dokumentu. Przechowuje informacje dotyczące dostosowywania.|`solutionId`|  
|[&#60; appAddin &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązania na poziomie aplikacji. Przechowuje informacje dotyczące dostosowywania.|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60; friendlyName &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Opcjonalny. Przechowuje nazwę dodatku VSTO, który pojawia się na liście zainstalowanych dodatków VSTO.|Brak|  
|[&#60; opis &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/description-element-office-development-in-visual-studio.md)|Wymagany tylko dla dodatków VSTO. Przechowuje opis wyświetlany na liście zainstalowanych programów.|Brak|  
|[&#60; formregions — &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Wymagany tylko dla dodatków VSTO programu Outlook, które obejmują regionów formularzy.|Brak|  
|[&#60; formRegion &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Wymagany tylko dla dodatków VSTO programu Outlook, które obejmują regionów formularzy.|`Name`|  
|[&#60; vstoruntime — &#62; Element &#40; programowanie Office w Visual Studio &#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Wymagany. W tym artykule opisano określonej wersji programu Visual Studio Tools for Office runtime, która jest obsługiwana przez rozwiązanie Office.|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## <a name="remarks"></a>Uwagi  
 Można ręcznie edytować aplikację i manifesty wdrożenia w rozwiązaniach pakietu Office. Następnie należy ponownie podpisać aplikację i manifesty wdrożenia przy użyciu Generowanie manifestu i edytowania narzędzia (mage.exe i mageui.exe). Aby uzyskać więcej informacji, zobacz [porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="file-location"></a>Lokalizacja pliku  
 Manifest aplikacji jest specyficzny dla jednej wersji rozwiązania. Z tego powodu manifesty aplikacji powinny być przechowywane oddzielnie od manifesty wdrożenia. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]umieszcza pliki określonej wersji w podkatalogu o nazwie po skojarzonej wersji w **pliki aplikacji** podkatalogu w folderze publikowania.  
  
## <a name="file-name-syntax"></a>Składnia nazwy pliku  
 Nazwa pliku manifestu aplikacji powinna być pełną nazwę i rozszerzenie aplikacji określonych w `assemblyIdentity` elementu, a następnie manifest rozszerzenia. Na przykład manifest aplikacji, która odwołuje się do dostosowania OutlookAddIn1.dll użyje następującą składnię nazwy pliku.  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  