---
title: Parametry wymienne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload: office
ms.openlocfilehash: f6e311f7c0268cecb94498fffda702438ea921b0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120622"
---
# <a name="replaceable-parameters"></a>Parametry wymienne
  Parametry wymienne lub *tokenów*, może być używany w plikach projektu o podanie wartości elementów rozwiązania programu SharePoint, których rzeczywistej wartości nie są znane w czasie projektowania. Są one podobne w funkcji standardu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokeny szablonu. Aby uzyskać więcej informacji, zobacz [parametrów szablonu](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Format tokenu
 Tokeny rozpoczynać i kończyć się znakiem dolara ($). We wdrożeniu, tokenów używanych są zastępowane rzeczywistymi wartościami gdy projekt jest umieszczone w pakietu rozwiązania programu SharePoint (*WSP* pliku). Na przykład token **$SharePoint.Package.Name$** może zostać rozwiązana do ciągu "Pakiet testowy programu SharePoint".  
  
## <a name="token-rules"></a>Token reguły
 Tokeny mają zastosowanie następujące reguły:  
  
-   Tokeny można określić dowolne miejsce w wierszu.  
  
-   Tokeny nie może obejmować wiele wierszy.  
  
-   Ten sam token można określić więcej niż raz w tym samym wierszu i w tym samym pliku.  
  
-   Można określić różne tokenów w tym samym wierszu.  
  
 Tokeny, których nie zastosowano reguły te są ignorowane, a nie powodują ostrzeżenia lub błędu.  
  
 Zastąpienia tokenów przez wartości ciągu jest realizowane natychmiast po przekształceniu manifestu. To zastąpienie zezwala użytkownikowi na edycję szablonów manifestu z tokenami.  
  
### <a name="token-name-resolution"></a>Rozpoznawanie nazw tokenu
 W większości przypadków token jest rozpoznawany jako niezależnie od tego, gdzie znajduje się określoną wartością. Jednak jeśli token jest powiązany z pakietu lub funkcji, wartość tokenu jest zależna od gdzie znajduje się. Na przykład, jeśli funkcja pakietu token, a następnie `$SharePoint.Package.Name$` jest rozpoznawana jako wartość "Pakiet A." Jeśli tej samej funkcji jest w pakiecie B, następnie `$SharePoint.Package.Name$` jest rozpoznawany jako "Pakiet B."  
  
## <a name="tokens-list"></a>Listy tokenów
 W poniższej tabeli wymieniono dostępne tokeny.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Zawierający nazwę projektu plików, takich jak *NewProj.csproj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Nazwa pliku zawierającego projektu bez rozszerzenia nazwy pliku. Na przykład "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Nazwa wyświetlana (silnej nazwy) zawierający projekt wyjściowy zestawu.|  
|$SharePoint.Project.AssemblyFileName$|Nazwa projektu zawierającego wyjściowy zestawu.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Nazwa projektu zawierającego wyjściowy zestawu bez rozszerzenia nazwy pliku.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Token klucza publicznego projektu zawierającego wyjściowy zestaw konwertowana na ciąg. (16-znaków "x2" szesnastkowej.)|  
|$SharePoint.Package.Name$|Nazwa pakietu.|  
|$SharePoint.Package.FileName$|Nazwa pliku definicji pakietu zawierającego.|  
|$SharePoint.Package.FileNameWithoutExtension$|Nazwa (bez rozszerzenia) pliku definicji pakietu zawierającego.|  
|$SharePoint.Package.Id$|Identyfikator pakietu programu SharePoint. Jeśli funkcja są używane w więcej niż jeden pakiet, ta wartość zostanie zmieniona.|  
|$SharePoint.Feature.FileName$|Nazwa pliku definicji zawierających funkcji, takich jak *Feature1.feature*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Nazwa pliku definicji funkcji bez rozszerzenia nazwy pliku.|  
|$SharePoint.Feature.DeploymentPath$|Nazwa folderu, który zawiera funkcję w pakiecie. Token ten jest równa właściwości "Path wdrożenia" w Projektancie funkcji. Przykładowa wartość to "Project1_Feature1".|  
|$SharePoint.Feature.Id$|Identyfikator programu SharePoint zawierającego funkcji. Ten token, zgodnie ze wszystkich funkcji na poziomie tokenów, może być używany tylko przez pliki uwzględnione w pakiecie za pomocą funkcji, nie dodał bezpośrednio do pakietu poza funkcją.|  
|$SharePoint.ProjectItem.Name$|Nazwa elementu projektu (nie jego nazwa pliku), jako uzyskany z **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<Identyfikator GUID >. AssemblyQualifiedName$|Nazwy kwalifikowanej zestawu zgodnych typu [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] tokenu. Format [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] jest pisana małymi literami i formatem Guid.ToString("D") (to znaczy xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type. \<Identyfikator GUID >. Imię i nazwisko$|Pełna nazwa typu dopasowania identyfikatora GUID w tokenie. Format identyfikatora GUID jest pisana małymi literami i formatem Guid.ToString("D") (to znaczy xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Dodawanie rozszerzenia do listy rozszerzeń plików zastępujący tokenu
 Mimo że tokeny teoretycznie mogą być używane przez każdego pliku, który należy do projektu SharePoint elementu uwzględniony w pakiecie, domyślnie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyszukuje tokenów tylko w przypadku plików pakietu, pliki manifest i pliki, które mają następujące rozszerzenia:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Składnik Web Part  
  
-   DWP  
  
 Te rozszerzenia są definiowane przez `<TokenReplacementFileExtensions>` element znajduje się w pliku Microsoft.VisualStudio.SharePoint.targets... \\< pliki programów\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools folderu.  
  
 Można jednak dodać dodatkowe rozszerzenia plików do listy. Dodaj `<TokenReplacementFileExtensions>` element do dowolnego PropertyGroup w pliku projektu programu SharePoint, który zdefiniowano przed \<Import > pliku obiektów docelowych programu SharePoint.  
  
> [!NOTE]  
>  Ponieważ zastępujący tokenu odbywa się to skompilowany projekt, nie należy dodawać rozszerzeniom plików dla typów plików, które są kompilowane, takich jak *.cs*, *.vb* lub *.resx*. Tokeny są zamieniane tylko w plikach, które nie są kompilowane.  
  
 Na przykład, aby dodać rozszerzeń nazw plików (*.myextension* i *.yourextension*) do listy rozszerzeń nazw plików zastępujący tokenu, należy dodać następujące polecenie, aby projekt (*.csproj* ) plików:  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Można dodać rozszerzenia bezpośrednio do obiektów docelowych (*.targets*) pliku. Jednak nie Dodawanie rozszerzenia zmienia się na liście rozszerzeń dla wszystkich projektów SharePoint opakowane w systemie lokalnym, tylko własne. To rozszerzenie może być wygodną projektanta wyłącznie w systemie lub w przypadku większości projektów wymagają. Jednak ponieważ jest specyficzne dla systemu, ta metoda nie jest przenośny i dlatego zalecane jest dodać wszystkich rozszerzeń do pliku projektu zamiast tego.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
