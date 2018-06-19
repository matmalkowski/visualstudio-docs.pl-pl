---
title: Obsługa projektu i właściwościami konfiguracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 823bfa0453d3e33fea2daa51779b1fe4800a1a86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133581"
---
# <a name="support-for-project-and-configuration-properties"></a>Obsługa projektu i właściwości konfiguracji
**Właściwości** okna w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) można wyświetlić właściwości projektu i konfiguracji. Strony właściwości można określić typu projektu co użytkownik może ustawiać właściwości aplikacji.  
  
 Po wybraniu węzła projektu w **Eksploratora rozwiązań** , a następnie klikając polecenie **właściwości** na **projektu** menu, można otworzyć okno dialogowe, które zawiera projekt i konfiguracji właściwości. W [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]i projektu typy pochodzące z tych języków, to okno dialogowe zostanie wyświetlone jako stronę z kartami w [ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md). Aby uzyskać więcej informacji, zobacz [nie znajduje się w kompilacji: wskazówki: Udostępnianie projektu i właściwościami konfiguracji (C#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Framework pakietu zarządzania dla projektów (MPFProj) udostępnia klasy pomocy dotyczące tworzenia i zarządzania nowy system projektu. Instrukcje można znaleźć źródła kodu i kompilacji w [MPF projektów — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Trwałość projektu i właściwości konfiguracji  
 Właściwości projektu i konfiguracji są zachowywane w pliku projektu, który ma rozszerzenie nazwy pliku skojarzone z typem projektu, na przykład, .csproj, vbproj i .myproj. Projekty języka zazwyczaj używany plik szablonu do wygenerowania pliku projektu. Istnieją jednak faktycznie na kilka sposobów skojarzenia typów projektów i szablony. Aby uzyskać więcej informacji, zobacz [opis katalogu szablonu (. Pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Właściwości projektu i konfiguracji są tworzone przez dodawanie elementów do pliku szablonu. Te właściwości będą dostępne dla każdego projektu utworzone za pomocą typu projektu, który korzysta z tego szablonu. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projekty i MPFProj używają [nie znajduje się w kompilacji: Przegląd MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) schematu dla plików szablonów. Te pliki mają sekcji PropertyGroup dla każdej konfiguracji. Właściwości projektów zwykle są zachowywane w pierwszej sekcji PropertyGroup ma ustawioną wartość ciąg pusty argument konfiguracji.  
  
 Poniższy kod przedstawia początku podstawowy plik projektu programu MSBuild.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 W tym pliku projektu `<Name>` i `<SchemaVersion>` właściwości projektu i `<Optimize>` jest właściwości konfiguracji.  
  
 Jest odpowiedzialny za projektu, aby utrwalić właściwości projektu i konfiguracji w pliku projektu.  
  
> [!NOTE]
>  Projekt można zoptymalizować trwałości utrwalanie tylko wartości właściwości, które różnią się od wartości domyślnych.  
  
## <a name="support-for-project-and-configuration-properties"></a>Obsługa projektu i właściwości konfiguracji  
 `Microsoft.VisualStudio.Package.SettingsPage` Klasa implementuje strony właściwości projektu i konfiguracji. Domyślna implementacja `SettingsPage` oferuje właściwości publiczne z kontem użytkownika w siatce właściwości ogólnych. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Metody wybiera klasy pochodzące od `SettingsPage` dla siatki właściwości projektu. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Metody wybiera klasy pochodzące od `SettingsPage` dla siatki właściwości konfiguracji. Typ swojego projektu powinny zastępować te metody, aby zaznaczyć odpowiednie właściwości strony.  
  
 `SettingsPage` Klasy i `Microsoft.VisualStudio.Package.ProjectNode` klasy oferują tych metod, aby zachować właściwości projektu i konfiguracji:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` i `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` utrwalić właściwości projektu.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` i `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` utrwalić właściwości konfiguracji.  
  
    > [!NOTE]
    >  Implementacje `Microsoft.VisualStudio.Package.SettingsPage` i `Microsoft.VisualStudio.Package.ProjectNode` klasy użyj `Microsoft.Build.BuildEngine` metody get i set właściwości projektu i konfiguracji z pliku projektu (MSBuild).  
  
 Klasa pochodzi od `SettingsPage` musi implementować `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` i `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` do utrwalenia projektu lub Konfiguracja właściwości pliku projektu.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute i ścieżka rejestru  
 Klasy wyprowadzone z `SettingsPage` mają być współużytkowane przez kilka VSPackages. Aby umożliwić pakiet VSPackage utworzyć klasę pochodzącą od `SettingsPage`, Dodaj `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` do klasy pochodzącej od `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Pakiet VSPackage, do której jest dołączona atrybut jest bez znaczenia. Kiedy pakiet VSPackage jest zarejestrowany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], jest zarejestrowany identyfikator klasy (CLSID) wszystkich obiektów, które można utworzyć, aby wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> go utworzyć.  
  
 Ścieżka rejestru obiektu, który można utworzyć jest określany przez łączenie <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word, CLSID i identyfikator guid typu obiektu. Jeśli `MyProjectPropertyPage` klasa ma identyfikator guid {3c693da2-5bca-49b3-bd95-ffe0a39dd723} i UserRegistryRoot jest HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, a następnie ścieżka rejestru będzie HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projekt i atrybuty właściwości konfiguracji i układu  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, I <xref:System.ComponentModel.DescriptionAttribute> atrybuty określić układ, etykietowania i opis właściwości projektu i konfiguracji na stronie właściwości ogólnych. Te atrybuty określa kategorię, nazwę wyświetlaną i opis opcji, odpowiednio.  
  
> [!NOTE]
>  Odpowiednik atrybutów, SRCategory LocDisplayName i SRDescription, użyj zasoby ciągów dla lokalizacji i są zdefiniowane w [MPF projektów — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Rozważmy następujący fragment kodu:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp` Właściwości konfiguracji jest wyświetlany na stronie właściwości konfiguracji jako **Moje właściwości konfiguracji** w kategorii **Moje kategorii**. Jeśli zaznaczona jest opcja, opis, **Mój opis**, pojawi się na panelu Opis.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie i usuwanie strony właściwości](../../extensibility/adding-and-removing-property-pages.md)   
 [Projekty](../../extensibility/internals/projects.md)   
 [Opis katalogu szablonu (pliki Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
