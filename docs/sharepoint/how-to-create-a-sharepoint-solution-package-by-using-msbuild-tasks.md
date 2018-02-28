---
title: "Porady: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 210793ab224e4da324591780dd3e6b171a1d721a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Porady: tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild
  Można kompilacji, czyszczenia i sprawdzanie poprawności pakietu programu SharePoint (wsp) przy użyciu zadań MSBuild wiersza polecenia na komputerze dewelopera. Można również używać tych poleceń, aby zautomatyzować proces kompilacji za pomocą programu Team Foundation Server na komputerze kompilacji.  
  
## <a name="building-a-sharepoint-package"></a>Tworzenie pakietu programu SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Aby utworzyć pakiet programu SharePoint  
  
1.  W systemie Windows **Start** menu, wybierz **wszystkie programy**, **Akcesoria**, **wiersza polecenia**.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby utworzyć pakiet dla projektu. Zastąp *ProjectFileName* z nazwą projektu.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Na przykład można uruchomić jeden z poniższych poleceń, aby pakiet projektu programu SharePoint o nazwie ListDefinition1.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>Czyszczenie pakietu programu SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Aby wyczyścić pakietu programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby wyczyścić pakietu dla projektu. Zastąp *ProjectFileName* z nazwą projektu.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Na przykład można Uruchom jedno z poniższych poleceń, aby wyczyścić projektu programu SharePoint o nazwie ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>Sprawdzanie poprawności pakietu programu SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Aby sprawdzić poprawność pakietu programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby sprawdzić poprawności pakietu dla projektu. Zastąp *ProjectFileName* z nazwą projektu.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Na przykład można Uruchom jedno z poniższych poleceń, aby sprawdzić poprawność projektu programu SharePoint o nazwie ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>Ustawianie właściwości w pakiecie programu SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Aby ustawić właściwość w pakiecie programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby ustawić właściwość pakietu dla projektu. Zastąp *PropertyName* razem z właściwością, który chcesz ustawić.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby ustawić poziom ostrzeżeń.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Instrukcje: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  