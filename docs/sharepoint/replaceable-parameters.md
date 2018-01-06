---
title: Parametry wymienne | Dokumentacja firmy Microsoft
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ed085a38b77f7c323451e8209902bece3747ddb1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="replaceable-parameters"></a>Parametry wymienne
  Parametry wymienne lub *tokenów*, może być używany w plikach projektu o podanie wartości elementów rozwiązania programu SharePoint, których rzeczywistej wartości nie są znane w czasie projektowania. Są one podobne w funkcji standardu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokeny szablonu. Aby uzyskać więcej informacji, zobacz [parametrów szablonu](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Format tokenu  
 Tokeny rozpoczynać i kończyć się znakiem dolara ($). Gdy projekt jest umieszczone w pliku pakietu (wsp) rozwiązania programu SharePoint w czasie wdrażania tokenów używanych są zastępowane rzeczywistymi wartościami. Na przykład token **$SharePoint.Package.Name$** może zostać rozwiązana do ciągu "Test pakiet programu SharePoint".  
  
## <a name="token-rules"></a>Token reguły  
 Tokeny mają zastosowanie następujące reguły:  
  
-   Tokeny można określić dowolne miejsce w wierszu.  
  
-   Tokeny nie może obejmować wiele wierszy.  
  
-   Ten sam token może być określone wiele razy w tym samym wierszu i w tym samym pliku.  
  
-   Można określić różne tokenów w tym samym wierszu.  
  
 Tokeny, których nie zastosowano reguły te są ignorowane, bez konieczności podawania ostrzeżenia lub błędu.  
  
 Zastąpienia tokenów przez wartości ciągu jest realizowane natychmiast po przekształceniu manifestu, dzięki czemu manifestu szablony zmieniony przez użytkownika do używania tokenów.  
  
### <a name="token-name-resolution"></a>Rozpoznawanie nazw tokenu  
 W większości przypadków token jest rozpoznawany jako niezależnie od tego, gdzie znajduje się określoną wartością. Jednak jeśli token jest powiązany z pakietu lub funkcji, wartość tokenu jest zależna od gdzie znajduje się. Na przykład, jeśli funkcja pakietu token, a następnie `$SharePoint.Package.Name$` jest rozpoznawana jako wartość "Pakiet A." Jeśli tej samej funkcji jest w pakiecie B, następnie `$SharePoint.Package.Name$` jest rozpoznawany jako "Pakiet B."  
  
## <a name="tokens-list"></a>Listy tokenów  
 W poniższej tabeli wymieniono dostępne tokeny.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Nazwa pliku zawierającego projektu, takie jak "NewProj.csproj".|  
|$SharePoint.Project.FileNameWithoutExtension$|Nazwa pliku zawierającego projektu bez rozszerzenia nazwy pliku. Na przykład "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Nazwa wyświetlana (silnej nazwy) zawierający projekt wyjściowy zestawu.|  
|$SharePoint.Project.AssemblyFileName$|Nazwa projektu zawierającego wyjściowy zestawu.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Nazwa projektu zawierającego wyjściowy zestawu bez rozszerzenia nazwy pliku.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Token klucza publicznego projektu zawierającego wyjściowy zestaw konwertowana na ciąg. (16-znaków "x2" szesnastkowej.)|  
|$SharePoint.Package.Name$|Nazwa pakietu.|  
|$SharePoint.Package.FileName$|Nazwa pliku definicji pakietu zawierającego.|  
|$SharePoint.Package.FileNameWithoutExtension$|Nazwa (bez rozszerzenia) pliku definicji pakietu zawierającego.|  
|$SharePoint.Package.Id$|Identyfikator pakietu programu SharePoint. Jeśli funkcja są używane w więcej niż jeden pakiet, ta wartość zostanie zmieniona.|  
|$SharePoint.Feature.FileName$|Nazwa pliku definicji zawierającego funkcji, takich jak Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Nazwa pliku definicji funkcji bez rozszerzenia nazwy pliku.|  
|$SharePoint.Feature.DeploymentPath$|Nazwa folderu, który zawiera funkcję w pakiecie. Token ten jest równa właściwości "Path wdrożenia" w Projektancie funkcji. Przykładowa wartość to "Project1_Feature1".|  
|$SharePoint.Feature.Id$|Identyfikator programu SharePoint zawierającego funkcji. Ten token, zgodnie ze wszystkich funkcji na poziomie tokenów, może być używany tylko przez pliki uwzględnione w pakiecie za pomocą funkcji, nie dodał bezpośrednio do pakietu poza funkcją.|  
|$SharePoint.ProjectItem.Name$|Nazwa elementu projektu (nie jego nazwa pliku), jako uzyskany z **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<Identyfikator GUID >. AssemblyQualifiedName$|Nazwy kwalifikowanej zestawu zgodnych typu [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] tokenu. Format [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] jest pisana małymi literami i formatem Guid.ToString("D") (to znaczy xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type. \<Identyfikator GUID >. Imię i nazwisko$|Pełna nazwa typu dopasowania identyfikatora GUID w tokenie. Format identyfikatora GUID jest pisana małymi literami i formatem Guid.ToString("D") (to znaczy xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>Dodawanie rozszerzenia do zastępujący tokenu listy rozszerzeń plików  
 Mimo że tokeny teoretycznie mogą być używane przez każdego pliku, który należy do projektu SharePoint elementu uwzględniony w pakiecie, domyślnie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyszukuje tokenów tylko w przypadku plików pakietu, pliki manifest i pliki, które mają następujące rozszerzenia:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Składnik Web Part  
  
-   DWP  
  
 Te rozszerzenia są definiowane przez `<TokenReplacementFileExtensions>` element znajduje się w pliku Microsoft.VisualStudio.SharePoint.targets... \\< pliki programów\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools folderu.  
  
 Można jednak dodać dodatkowe rozszerzenia plików do listy. Aby to zrobić, należy dodać `<TokenReplacementFileExtensions>` element do dowolnego PropertyGroup w pliku projektu programu SharePoint, który zdefiniowano przed \<Import > pliku obiektów docelowych programu SharePoint.  
  
> [!NOTE]  
>  Ponieważ zastępujący tokenu odbywa się to skompilowany projekt, nie należy dodawać rozszerzenia plików dla typów plików, które są kompilowane, na przykład .cs, .vb lub resx. Tokeny są zamieniane tylko w plikach, które nie są kompilowane.  
  
 Na przykład można dodać rozszerzenia nazwy pliku ".myextension" i ".yourextension" do listy rozszerzeń nazw plików zastępujący tokenu, należy dodać następujące do pliku .csproj:  
  
```  
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
  
 Alternatywnie można dodać rozszerzenia bezpośrednio w pliku .targets. Jednak w ten sposób zmienia listy rozszerzeń dla wszystkich projektów SharePoint opakowane w systemie lokalnym, nie tylko własne. Może to być wygodny projektanta wyłącznie w systemie lub w przypadku większości projektów wymagają. Jednak ponieważ jest specyficzne dla systemu, ta metoda nie jest przenośny i dlatego zalecane jest dodać wszystkich rozszerzeń do pliku projektu zamiast tego.  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  