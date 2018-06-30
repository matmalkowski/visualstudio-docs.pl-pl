---
title: 'Porady: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5a95eb80b860a1447fe6e958edb9c98b66805a90
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120286"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Porady: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild
  Kompilacji, czyszczenia i sprawdzanie poprawności pakietu programu SharePoint (*WSP*) przy użyciu zadań MSBuild wiersza polecenia na komputerze dewelopera. Można również używać tych poleceń, aby zautomatyzować proces kompilacji za pomocą programu Team Foundation Server na komputerze kompilacji.  
  
## <a name="build-a-sharepoint-package"></a>Tworzenie pakietu programu SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Aby utworzyć pakiet programu SharePoint  
  
1.  W systemie Windows **Start** menu, wybierz **wszystkie programy** > **Akcesoria** > **wiersza polecenia**.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby utworzyć pakiet dla projektu. Zastąp *ProjectFileName* z nazwą projektu.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Na przykład można uruchomić jeden z poniższych poleceń, aby pakiet projektu programu SharePoint o nazwie ListDefinition1.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>Wyczyść pakietu programu SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Aby wyczyścić pakietu programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby wyczyścić pakietu dla projektu. Zastąp *ProjectFileName* z nazwą projektu.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Na przykład można Uruchom jedno z poniższych poleceń, aby wyczyścić projektu programu SharePoint o nazwie ListDefinition1.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>Sprawdzanie poprawności pakietu programu SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Aby sprawdzić poprawność pakietu programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby sprawdzić poprawności pakietu dla projektu. Zastąp *ProjectFileName* z nazwą projektu.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Na przykład można Uruchom jedno z poniższych poleceń, aby sprawdzić poprawność projektu programu SharePoint o nazwie ListDefinition1.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>Ustawianie właściwości w pakiecie programu SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Aby ustawić właściwość w pakiecie programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby ustawić właściwość pakietu dla projektu. Zastąp *PropertyName* razem z właściwością, który chcesz ustawić.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby ustawić poziom ostrzeżeń.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Porady: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
