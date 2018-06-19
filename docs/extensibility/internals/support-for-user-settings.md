---
title: Obsługa ustawień użytkowników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf2ba79cc8bff57de1fd410f8a2780825d693181
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134096"
---
# <a name="support-for-user-settings"></a>Obsługa ustawień użytkowników
Pakiet VSPackage może zdefiniować co najmniej jednej kategorii ustawień, grup zmiennych stanu, które będą się powtarzać, gdy użytkownik wybierze **importowania i eksportowania ustawień** na **narzędzia** menu. Aby włączyć ten trwałości, należy użyć ustawienia interfejsów API w [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Wpis rejestru, który jest określany jako punkt ustawienia niestandardowe i identyfikator GUID definiuje pakiet VSPackage ustawienia kategorii. Pakiet VSPackage może obsługiwać wiele kategorii ustawień, każdy zdefiniowany przez punkt ustawienia niestandardowe.  
  
-   Implementacje ustawień, które są oparte na zestawy międzyoperacyjne (przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interfejsu) należy utworzyć niestandardowe ustawienia punktu przez edycję rejestru lub za pomocą skryptu rejestratora (pliku .rgs). Aby uzyskać więcej informacji, zobacz [tworzenie skrypty rejestratora](/cpp/atl/creating-registrar-scripts).  
  
-   Kod, który używa Framework zarządzane pakietu (MPF) należy utworzyć niestandardowe ustawienia punktów dołączając <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> do pakiet VSPackage dla każdego punktu ustawienia niestandardowe.  
  
     Jeśli pojedynczy pakiet VSPackage obsługuje kilka punktów ustawienia niestandardowe, w każdym punkcie ustawienia niestandardowe jest implementowany przez osobnej klasy i każdego zarejestrowane przez unikatowego wystąpienia <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> klasy. W rezultacie ustawienia implementującej klasy może obsługiwać więcej niż jedną kategorię ustawień.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Niestandardowe ustawienia rejestru punktu wejścia szczegóły  
 Punkty ustawienia niestandardowe są tworzone we wpisie rejestru w następującej lokalizacji: HKLM\Software\Microsoft\VisualStudio\\*\<wersji >* \UserSettings\\`<CSPName>`, gdzie `<CSPName>` jest nazwa punktu ustawienia niestandardowe obsługuje pakiet VSPackage i  *\<wersji >* jest wersja [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], na przykład 8.0.  
  
> [!NOTE]
>  Ścieżka katalogu głównego HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<wersji >* może zostać zastąpiona przez alternatywny główne, kiedy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest zintegrowane środowisko programistyczne (IDE) zainicjowane. Aby uzyskać więcej informacji, zobacz [przełączniki wiersza polecenia](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Struktura wpisu rejestru przedstawiono poniżej:  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<wersji >* \UserSettings\  
  
 `<CSPName`> = "#12345" s  
  
 Pakiet = "{XXXXXX XXXX XXXX XXXX XXXXXXXXX}"  
  
 Kategoria = "{rrrr RRRRRR rrrr rrrr YYYYYYYYY}"  
  
 ResourcePackage = "{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}"  
  
 AlternateParent = CategoryName  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|(Domyślnie)|REG_SZ|Nazwa punktu ustawień niestandardowych|Nazwy kluczy `<CSPName`>, jest Niezlokalizowany nazwę punktu ustawienia niestandardowe.<br /><br /> W przypadku implementacji oparte na MPF nazwy kluczy są uzyskiwane przez połączenie `categoryName` i `objectName` argumenty <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktora do `categoryName_objectName`.<br /><br /> Klucz może być pusta lub może zawierać identyfikator odwołanie do zlokalizowanego ciągu w satelitarnej biblioteki DLL. Ta wartość jest uzyskiwany z `objectNameResourceID` argument <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktora.|  
|Package|REG_SZ|Identyfikator GUID|Identyfikator GUID pakiet VSPackage, który implementuje punkt ustawienia niestandardowe.<br /><br /> Implementacje ze względu na użycie MPF <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> klasy, użyj Konstruktora `objectType` argument zawierający pakiet VSPackage <xref:System.Type> i odbicie, aby uzyskać tę wartość.|  
|Kategoria|REG_SZ|Identyfikator GUID|Identyfikator GUID kategorii ustawienia.<br /><br /> Implementacje oparte na zestawy międzyoperacyjne, ta wartość może być dowolnie wybrany identyfikator GUID, który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE przekazuje do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metody. Implementacje wszystkie te dwie metody należy sprawdzić ich argumentów identyfikatora GUID.<br /><br /> W przypadku implementacji oparte na MPF ten identyfikator GUID jest uzyskiwany przez <xref:System.Type> wykonawczych klasy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mechanizmu ustawienia.|  
|ResourcePackage|REG_SZ|Identyfikator GUID|Opcjonalny.<br /><br /> Ścieżka do satelitarne biblioteki DLL zawierający zlokalizowane ciągi Jeśli implementującej pakiet VSPackage nie dostarcza je.<br /><br /> MPF używa odbicia, aby uzyskać poprawny zasobów pakiet VSPackage, więc <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> klasy nie ustawia tego argumentu.|  
|AlternateParent|REG_SZ|Nazwa folderu, w obszarze strony opcji narzędzi zawierające ten punkt ustawienia niestandardowe.|Opcjonalny.<br /><br /> Tę wartość należy ustawić tylko w przypadku wdrażania ustawień obsługuje **opcje narzędzia** stron korzystających z mechanizmu stanu trwałego w [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] zamiast mechanizm model automatyzacji, aby zapisać stan.<br /><br /> W takich przypadkach wartość w kluczu AlternateParent jest `topic` sekcji `topic.sub-topic` ciąg używany do identyfikowania danej **ToolsOptions** strony. Na przykład w przypadku **ToolsOptions** strony `"TextEditor.Basic"` wartość AlternateParent będzie `"TextEditor"`.<br /><br /> Gdy <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> generuje punkt ustawienia niestandardowe, jest taka sama jak nazwa kategorii.|