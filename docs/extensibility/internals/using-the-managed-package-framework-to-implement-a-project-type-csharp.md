---
title: Przy użyciu platformy zarządzanego pakietu dla typu projektu (C#) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112988f28728d40509a3af0360246a6bb4caef1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140206"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Za pomocą środowiska zarządzanego pakietu do zaimplementowania typ projektu (C#)
Framework zarządzane pakietu (MPF) zapewnia klas C# możesz użyć lub dziedziczyć po implementacji własnych typów projektów. MPF implementuje wiele interfejsów Visual Studio oczekuje typu projektu, aby zapewnić, pozwalając użytkownikowi na skoncentrować się na implementacji dane tego typu projektu.  
  
## <a name="using-the-mpf-project-source-code"></a>Za pomocą kodu źródłowego MPF projektów  
 Framework pakietu zarządzania dla projektów (MPFProj) udostępnia klasy pomocy dotyczące tworzenia i zarządzania nowy system projektu. W przeciwieństwie do innych klas MPF klasy projektu nie znajdują się w zestawach dostarczanego z programem Visual Studio. Zamiast tego klasy projektu są przekazywane jako kodu źródłowego w [MPF projektów 2013](http://mpfproj12.codeplex.com).  
  
 Aby dodać ten projekt do rozwiązania pakiet VSPackage, wykonaj następujące czynności:  
  
1.  Pobierz pliki MPFProj *MPFProjectDir*.  
  
2.  W *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, zmień następujący blok:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Utwórz projekt pakiet VSPackage.  
  
2.  Zwolnienie projektu pakiet VSPackage.  
  
3.  Edytowanie pliku .csproj pakiet VSPackage, dodając następujący blok przed innych `<Import>` bloków:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Zapisz projekt.  
  
2.  Zamknij i ponownie otwórz rozwiązanie pakiet VSPackage.  
  
3.  Otwórz projekt pakiet VSPackage. Nowy katalog o nazwie ProjectBase powinna zostać wyświetlona.  
  
4.  Dodaj następujące odwołanie do projektu pakiet VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Skompiluj projekt.  
  
## <a name="hierarchy-classes"></a>Hierarchia klas  
 W poniższej tabeli przedstawiono klasy w MPFProj, które obsługują hierarchii projektu. Aby uzyskać więcej informacji, zobacz [hierarchii i wybór](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Klasy obsługi dokumentów  
 W poniższej tabeli wymieniono klasy w MPF, które obsługują obsługi dokumentów. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Konfiguracja i klasy wyjściowe  
 W poniższej tabeli wymieniono klasy w MPF, które umożliwiają typów projektów obsługuje wiele konfiguracji, takich jak debug i release i kolekcje danych wyjściowych projektu. Aby uzyskać więcej informacji, zobacz [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md).  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Obsługa automatyzacji klas  
 W poniższej tabeli wymieniono klasy w MPF, które obsługują automatyzacji, dzięki czemu użytkownicy tego typu projektu można zapisywać dodatków.  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Właściwości klasy  
 W poniższej tabeli przedstawiono klasy w MPF, które umożliwiają typów projektów Dodaj właściwości, czy użytkownicy mogą przeglądać i modyfikować w przeglądarce właściwości.  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|