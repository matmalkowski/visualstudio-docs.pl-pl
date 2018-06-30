---
title: Omówienie programu SharePoint modelu programowania rozszerzeń narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7882439d6c25cf57a435e4bbe046b2121c3e0405
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120322"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Omówienie programu SharePoint modelu programowania rozszerzeń narzędzi
  Po utworzeniu rozszerzeń dla narzędzi SharePoint w Visual Studio możesz rozpocząć od implementowanie interfejsów rozszerzeń, które są udostępniane przez narzędzia programu SharePoint. W większości przypadków będą też używać innych typów dostarczone przez narzędzia programu SharePoint do implementowania funkcji w Twoje rozszerzenie. W niektórych scenariuszach może również używać typów w innych modeli obiektu zapewniane przez Visual Studio i SharePoint. Należy zrozumienie przeznaczenia każdego z tych modeli obiektów i jak mogą z nich korzystać ze sobą do tworzenia rozszerzeń dla narzędzi SharePoint.  
  
## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Rozszerzanie narzędzi SharePoint zaimplementowanie rozszerzalności interfejsów
 Visual Studio używa Framework Managed Extensibility (MEF) w .NET Framework 4, aby zapewnić modelu rozszerzeń dla narzędzi SharePoint. MEF to interfejs API (zaimplementowana w zestawie System.ComponentModel.Composition), umożliwia aplikacji udostępnianie punkty rozszerzeń i odnaleźć i załadować rozszerzeń w czasie wykonywania. Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).  
  
 Aby rozszerzyć narzędzia programu SharePoint, implementować interfejsów rozszerzeń, które są dostępne w programie Visual Studio. Należy także zastosować <xref:System.ComponentModel.Composition.ExportAttribute>, oraz dodatkowe SharePoint specyficzne dla narzędzia atrybutów w razie potrzeby implementacji interfejsu. W poniższej tabeli wymieniono interfejsów, które można zaimplementować w celu rozszerzenia narzędzia programu SharePoint.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementuje ten interfejs do definiowania nowego typu elementu projektu SharePoint. Na przykład zobacz [porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementuje ten interfejs do rozszerzenia typu elementu projektu SharePoint, która jest już zainstalowana w programie Visual Studio. Na przykład zobacz [porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementuje ten interfejs do rozszerzania SharePoint — projekty. Na przykład zobacz [porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementuje ten interfejs do definiowania nowych kroku wdrożenia, który może zostać wykonany, gdy element projektu programu SharePoint jest wdrożony lub wycofany. Na przykład zobacz [wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementuje ten interfejs, aby rozszerzyć istniejący węzeł w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera** okna. Na przykład zobacz [porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementuje ten interfejs do definiowania nowego typu węzła w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera** okna. Na przykład zobacz [porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementuje ten interfejs do definiowania funkcji niestandardowej reguły walidacji. Na przykład zobacz [porady: Tworzenie funkcji niestandardowej oraz pakietu reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementuje ten interfejs do definiowania reguły sprawdzania poprawności pakietu niestandardowego. Na przykład zobacz [porady: Tworzenie funkcji niestandardowej oraz pakietu reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 Po zaimplementowaniu rozszerzeń narzędzi SharePoint, należy wdrożyć zestawu rozszerzenia w pakiet programu Visual Studio (VSIX) rozszerzenia do włączenia programu Visual Studio odnaleźć i załadować rozszerzenia. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Zrozumienie modele obiektów, które są używane w rozszerzeń narzędzi SharePoint
 Istnieje kilka modeli obiektów używanych podczas tworzenia rozszerzeń dla narzędzi SharePoint:  
  
-   *Narzędzia programu SharePoint modelu obiektów*. Ten model obiektów udostępnia interfejsy rozszerzeń, których wdrożenie do tworzenia rozszerzeń narzędzi SharePoint i innych powiązanych typów.  
  
-   *Visual Studio Automatyzacja i integracja z modeli do obiektu*. Użyj tych modeli obiektów dostęp do funkcji programu Visual Studio, które wykraczają poza zakres modelu obiektów programu SharePoint tools.  
  
    > [!NOTE]  
    >  Niektóre obiekty w modelu obiektu narzędzia programu SharePoint do obiektów w automatyzacji programu Visual Studio i modele obiektów integracji i odwrotnie, za pomocą usługi projektu SharePoint można przekonwertować. Aby uzyskać więcej informacji, zobacz [konwersji między typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
-   *Modele obiektów serwera i klienta programu SharePoint*. Użyj tych modeli obiektów, aby zmodyfikować witryny programu SharePoint, lub do pobierania danych z witryny programu SharePoint z kontekstu rozszerzeń narzędzi SharePoint.  
  
### <a name="sharepoint-tools-object-model"></a>Model obiektów narzędzi SharePoint
 Każde rozszerzenie narzędzia SharePoint używa typów w modelu obiektów programu SharePoint narzędzia do definiowania zachowania podstawowe i funkcje rozszerzenia. W poniższych tabelach opisano przestrzenie nazw, które mają zostać uwzględnione w tym modelu obiektu assemby, który je zawiera.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll    
|Przestrzeń nazw|Opis|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint>|Zawiera typy, których używasz do rozszerzania i automatyzacji systemu projektu SharePoint. Na przykład wbudowana SharePoint — projekty i elementy projektu można rozszerzyć lub można utworzyć własne elementy projektu. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Zawiera typy, które umożliwiają rozszerzanie procesu wdrażania dla projektów programu SharePoint, takich jak tworzenie własnych kroki wdrażania i konfiguracji wdrażania. Aby uzyskać więcej informacji, zobacz [pakowania i wdrażania SharePoint rozszerzyć](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Zawiera typy, które zostało użyte do rozszerzenia węzłów w **połączeń SharePoint** w węźle **Eksploratora serwera** okna, lub do definiowania nowych typów węzłów. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Zawiera typy, które umożliwiają dostęp do definicji funkcji w projekcie programu SharePoint.|  
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Zawiera typy, które umożliwiają dostęp do definicji pakietu rozwiązania SharePoint.|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Zawiera typy, które służy do dostosowywania zachowania weryfikacji funkcji i pakietów dla projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie funkcji niestandardowej oraz pakietu reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).| 

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll
|Przestrzeń nazw|Opis|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Zawiera typy, które służy do tworzenia niestandardowych *polecenia SharePoint*. Polecenie programu SharePoint jest to metoda, która wywołuje w modelu obiektów programu SharePoint server z rozszerzeniem narzędzia programu SharePoint. Aby uzyskać więcej informacji, zobacz [wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll
|Przestrzeń nazw|Opis|  
|-|-| 
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Zawiera typy, których można użyć, aby uzyskać informacje o wbudowanych **Eksploratora serwera** węzłów, które reprezentują pojedynczych składników w witrynie programu SharePoint, na przykład węzeł, który reprezentuje listy, pola lub typu zawartości. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### <a name="visual-studio-automation-object-model"></a>Model obiektu automatyzacji programu Visual Studio
 Model obiektu automatyzacji programu Visual Studio udostępnia interfejsy API, których można zautomatyzować projektów programu Visual Studio i IDE. Model obiektów programu Visual Studio należy używać do wykonywania zadań związanych z projektem, które nie są specyficzne dla SharePoint — projekty lub wykonywać inne zadania automatyzacji ogólne w Visual Studio. Zazwyczaj ten model obiektów jest często używane w dodatkach programu Visual Studio i makra, ale można go w rozszerzeń narzędzi SharePoint.  
  
 Główna część modelu obiektu automatyzacji programu Visual Studio jest zdefiniowany w *EnvDTE.dll* zestawu. *EnvDTE\\<version>.dll* zestawy oferowanie dodatkowych funkcji, który został wprowadzony w określonych wersji programu Visual Studio. Te zestawy są dołączone do programu Visual Studio.  
  
 Aby uzyskać więcej informacji na temat modelu obiektu automatyzacji, zobacz [odwołania do zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
### <a name="visual-studio-integration-object-model"></a>Model obiektów integracji programu Visual Studio
 Model obiektów integracji udostępnia interfejsy API, który służy do dodawania funkcji do programu Visual Studio, tworząc *pakiet VSPackage*. Pakiet VSPackage jest moduł, który rozszerza dzięki takim funkcjom niestandardowe, takie jak okna narzędzi, edytory projektantów, usług i projektów programu Visual Studio IDE.  
  
 Jeśli chcesz dodać nowa funkcja programu Visual Studio, który będzie używany przy użyciu wbudowanych narzędzi SharePoint, można użyć modelu obiektów integracji. Na przykład w przypadku utworzenia niestandardowego elementu projektu SharePoint reprezentujący akcji niestandardowej witryny programu SharePoint, można również utworzyć pakiet VSPackage, który implementuje projektanta dla akcji niestandardowej. Projektant można skojarzyć z akcji niestandardowej, przez dodawanie pozycji menu skrótów do elementu projektu, który reprezentuje akcji niestandardowej w **Eksploratora rozwiązań**. Możesz otworzyć z projektantem przez otwarcie menu skrótów (przez kliknięcie prawym przyciskiem myszy element projektu akcji niestandardowej lub wybierając go, a następnie wybierając **Shift**+**F10** kluczy), a następnie wybierając **Otwórz**.  
  
 Ten model obiektów jest zdefiniowany w zestawie zestawy, które są dołączone do programu Visual Studio SDK. Zestawy głównego, w tym modelu obiektu między innymi *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll*, i  *Microsoft.VisualStudio.OLE.Interop.dll*.  
  
 Aby uzyskać więcej informacji na temat integracji modelu obiektów, zobacz [omówienie modelu automatyzacji](/visualstudio/extensibility/internals/automation-model-overview) i [odwołania do zestawu SDK programu Visual Studio](/visualstudio/extensibility/visual-studio-sdk-reference).  
  
### <a name="sharepoint-object-models"></a>Modele obiektów programu SharePoint
 Rozszerzeń narzędzi SharePoint można użyć interfejsy API programu SharePoint, aby zmodyfikować witryny programu SharePoint lub pobrać dane z witryny programu SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zapewniają dwa różne obiekty modele: modelu obiektów serwera i modelu obiektów klienta.  
  
 Interfejsy API można użyć w modelu obiektu, albo w rozszerzeniu narzędzia programu SharePoint, ale każdy model obiektów ma niektóre zalety i wady w kontekście rozszerzeń narzędzi SharePoint. Aby uzyskać więcej informacji, zobacz [wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Model obiektu|Opis|  
|------------------|-----------------|  
|Model obiektu serwera|W modelu obiektów serwera zapewnia dostęp do wszystkich funkcji [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ujawnia programowo. Ten model obiektów jest przeznaczony do użycia przez rozwiązań programu SharePoint, które są uruchamiane na serwerze programu SharePoint. Większość tego modelu obiektu jest zdefiniowana w *Microsoft.SharePoint.dll* zestawu. Aby uzyskać więcej informacji na temat modelu obiektów serwera, zobacz [za pomocą modelu obiektów programu SharePoint Foundation po stronie serwera](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Model obiektu klienta|Model obiektu klienta jest podzbiorem modelu obiektów serwera, który może służyć do współpracy z danymi programu SharePoint ze zdalnego klienta lub serwera. Zaprojektowano go w celu zminimalizowania liczby rund, które muszą być wykonywane do wykonywania typowych zadań. Większość client object model jest zdefiniowany w *Microsoft.SharePoint.Client.dll* i *Microsoft.SharePoint.Client.Runtime.dll* zestawów. Aby uzyskać więcej informacji na temat modelu obiektów klienta, zobacz [zarządzane Client Object Model](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)  
  
