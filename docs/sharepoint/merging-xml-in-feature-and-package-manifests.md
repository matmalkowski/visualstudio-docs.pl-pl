---
title: Scalanie XML w funkcji i pakietów manifestach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3101245d720e9fdd1c4923ea03acd5b2d4db816
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120563"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Scalanie XML w manifestach funkcji i pakietu
  Funkcje i pakiety są definiowane przez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki manifestu. Te manifesty spakowanych są kombinacją danych generowanych przez projektantów i niestandardowe [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] wprowadzona w szablonie manifestu przez użytkowników. Podczas tworzenia pakietów [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scala niestandardowego [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcji z warunkiem projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] do utworzenia spakowanych [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliku manifestu. Podobnych elementów, z wyjątkiem wymienionych w dalszej części scalania wyjątki są łączone w celu uniknięcia [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] błędy sprawdzania poprawności po wdrożeniu plików do programu SharePoint, aby manifest pliki mniejsze i bardziej wydajnych.  
  
## <a name="modify-the-manifests"></a>Modyfikowanie manifestów
 Nie można bezpośrednio modyfikować plików manifestu w pakiecie, do momentu wyłączenia funkcji lub pakiet projektantów. Jednak można ręcznie dodać niestandardowe [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementy do manifestu szablonu przez projektantów funkcji i pakietów lub [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] edytora. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) i [porady: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Funkcja i pakietu manifestu procesu scalania
 Podczas łączenia z niestandardowych elementów wraz z elementami dostarczane przez projektanta, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przystępuje do następującej procedury. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sprawdza, czy każdy element ma unikatową wartość klucza. Jeśli element nie ma unikatowy kluczy wartości, jest dołączany do spakowanych pliku manifestu. Podobnie nie można scalić elementów, które mają wiele kluczy. W związku z tym są dołączane do pliku manifestu.  
  
 Jeśli element ma unikatowy klucz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] porównuje wartości projektanta i niestandardowe klucze. Jeśli wartości są zgodne, scalić pojedynczej wartości. Jeśli wartości są różne, projektanta wartości klucza są usuwane i wartość klucza niestandardowego jest używany. Scalane są także kolekcje. Na przykład jeśli wygenerowanym przez projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] i niestandardowej [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zarówno zawiera kolekcję zestawów, spakowanych manifest zawiera tylko jedną kolekcję zestawów.  
  
## <a name="merge-exceptions"></a>Scal wyjątków
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Scala projektanta większość [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementów wraz z podobną niestandardową [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tak długo, jak mają jeden unikatowy atrybut identyfikujący elementów. Jednak niektóre elementy braku Unikatowy identyfikator wymagane dla [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] scalania. Te elementy są określane jako *scalania wyjątki*. W takich przypadkach [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie scala niestandardowego [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementów wraz z warunkiem projektanta [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementów, ale zamiast tego dołącza je do pakietów pliku manifestu.  
  
 Poniżej przedstawiono listę wyjątków scalania dla funkcji i pakietu [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki manifestu.  
  
|Projektant|XML Element|  
|--------------|-----------------|  
|Projektant funkcji|Zależności aktywacji|  
|Projektant funkcji|UpgradeAction|  
|Projektanta pakietów|SafeControl —|  
|Projektanta pakietów|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Elementy manifestu funkcji
 Poniższa tabela znajduje się lista wszystkich elementów manifestu funkcji, które można by scalić i ich Unikatowy klucz, który służy do dopasowania.  
  
|Nazwa elementu|Unikatowy klucz|  
|------------------|----------------|  
|Funkcja (wszystkie atrybuty)|*Nazwa atrybutu* (nazwy atrybutu elementu funkcji jest unikatowy klucz).|  
|ElementFile|Lokalizacja|  
|ElementManifests/ElementManifest|Lokalizacja|  
|Właściwości lub właściwości|Key|  
|CustomUpgradeAction|Nazwa|  
|CustomUpgradeActionParameter|Nazwa|  
  
> [!NOTE]  
>  Ponieważ jedynym sposobem zmodyfikuj CustomUpgradeAction element jest niestandardowa [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] edytora, scalanie nie powoduje niski.  
  
## <a name="package-manifest-elements"></a>Elementy manifestu pakietu
 Poniższa tabela znajduje się lista wszystkich elementów manifestu pakietu, które można by scalić i ich Unikatowy klucz, który służy do dopasowania.  
  
|Nazwa elementu|Unikatowy klucz|  
|------------------|----------------|  
|Rozwiązania (wszystkie atrybuty)|*Nazwa atrybutu* (nazwy atrybutu elementu rozwiązania jest unikatowy klucz).|  
|ApplicationResourceFiles/ApplicationResourceFile|Lokalizacja|  
|Zestawy/zestawu|Lokalizacja|  
|ClassResources/ClassResource|Lokalizacja|  
|Plik DwpFiles/dwp|Lokalizacja|  
|FeatureManifests/FeatureManifest|Lokalizacja|  
|Zasoby/zasobów.|Lokalizacja|  
|RootFiles/RootFile|Lokalizacja|  
|SiteDefinitionManifests/SiteDefinitionManifest|Lokalizacja|  
|WebTempFile|Lokalizacja|  
|TemplateFiles/TemplateFile|Lokalizacja|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Ręcznie Dodaj wdrożonych plików
 Niektóre elementy manifestu, takie jak ApplicationResourceFile i DwpFiles, określ lokalizację, która zawiera nazwę pliku. Jednak dodanie wpisu nazwy pliku do manifestu szablonu nie dodaje podstawowego pliku do pakietu. Należy dodać plik do projektu, aby uwzględnić go w pakiecie i odpowiednio ustaw dla właściwości typu wdrożenia.  
  
## <a name="see-also"></a>Zobacz także
 [Pakiet i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
